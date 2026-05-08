# Manychat - Carrinho Abandonado

Status: ✅ **Em produção** (aguardando primeiro lead real pra validar end-to-end)
Data de implementação: 06-07/05/2026
Webhook Hotmart: `CG Carrinho Abandonado - Make`
Cenário Make: `CG - Carrinho Abandonado`
Fluxo Manychat: `[Wtsp] Carrinho abandonado - CG`

---

## Visão geral

Sequência automatizada de recuperação de carrinho abandonado para o produto **Conexão Gestantes**. Captura abandonos via webhook Hotmart, cria/atualiza subscriber no Manychat via Make como ponte, e dispara fluxo conversacional da "Vitória" no WhatsApp com objetivo de recuperar a venda ou capturar o lead pra remarketing futuro.

### Por que o setup é assim

A integração nativa Manychat-Hotmart **não suporta** o evento `PURCHASE_OUT_OF_SHOPPING_CART`. A integração nativa funciona pra outros eventos (Compra Aprovada, etc.), mas pra carrinho abandonado precisa do Make como ponte:

```
[Hotmart] → [Webhook PURCHASE_OUT_OF_SHOPPING_CART]
              ↓
           [Make] → [Create Subscriber Manychat] → [Add Tag Carrinho Abandonado CG]
                                                            ↓
                                                   [Trigger fluxo Manychat]
                                                            ↓
                                                   [Sequência da Vitória]
```

---

## Arquitetura

### 1. Webhook Hotmart

- Nome: `CG Carrinho Abandonado - Make`
- URL destino: `https://hook.us2.make.com/syxb7v9sdvhteb97796ww6yn9y4ykjop`
- Evento: `PURCHASE_OUT_OF_SHOPPING_CART`
- Produto: Conexão Gestantes (`N100354142M`)

### 2. Cenário Make

Estrutura final:

```
[Webhook Custom (rosa)]
   ↓
[Manychat: Create Subscriber]
   ├─ Sucesso → [Manychat: Manage Tags] (aplica Carrinho Abandonado CG)
   └─ Erro (wa_id exists) → [Resume] (handler que ignora silenciosamente)
```

**Configuração do Create Subscriber:**

| Campo | Valor |
|---|---|
| Connection | Manychat - CG |
| First name | `first(split(2.data.buyer.name; " "))` |
| Last name | `join(slice(split(2.data.buyer.name; " "); 1); " ")` |
| Phone number | (vazio — limitação da conta) |
| WhatsApp phone number | `+` + `2.data.buyer.phone` (Hotmart já manda com DDI 55) |
| Email address | (vazio — limitação da conta) |
| Has SMS opt-in | Empty |
| Has email opt-in | Empty |
| Consent phrase | "Iniciei contato com a Conexão Gestantes ao preencher meus dados no checkout do produto e autorizo o recebimento de mensagens via WhatsApp." |

**Funções de split do nome:** inseridas via painel "Functions" do Make, não como texto literal.

**Manage Tags:**
- Action: Add a tag
- Subscriber ID: `6.data.id` (output do Create Subscriber)
- Tag: `Carrinho Abandonado CG`

**Error Handler (Resume) no Create Subscriber:**
Captura erro `wa_id already exists` que ocorre quando subscriber já existe na base. Handler ignora silenciosamente — cenário termina sem erro, subscriber existente não recebe mensagem (limitação aceita pra MVP, ver "Próximas iterações").

### 3. Estrutura JSON da Hotmart (referência)

```
data.buyer.name (string única ex: "Felipe Matheus Gonçalves")
data.buyer.email
data.buyer.phone (formato: 5511954515596 — JÁ COM DDI 55)
data.id (UUID do evento)
data.event = PURCHASE_OUT_OF_SHOPPING_CART
data.product.id, data.product.name
data.offer.code
```

---

## Fluxo Manychat - "Vitória"

### Trigger

Tag `Carrinho Abandonado CG` aplicada → fluxo dispara.

### Estrutura completa

```
[M1 inicial: "Oi, sou a Vitória..."]
   ↓
[Atraso Inteligente: 23h + janela 8-21h]
   ↓
[Condição: Tag está Respondeu Ao Vivo OR Membro CG?]
   ├─ Verde (TRUE) → encerra
   └─ Vermelha (FALSE) → segue para M2
   ↓
[M2 (Mensagem #1): "voltei aqui, deixei abaixo as dúvidas..." + 3 botões]
   ├─ "Como eu acesso?" → [Mensagem #2 "Eu te explico"]
   │     ├─ "Quero o link" → [M4 com Smart Link Após Acesso]
   │     │     └─ Próximo Passo → [Ações #2: tag Após acesso]
   │     │           └─ [Atraso #3: 1h + janela 8-21h]
   │     │                 └─ [Condição: Tag está Respondeu Ao Vivo OR Membro CG?]
   │     │                       ├─ Verde (TRUE) → encerra
   │     │                       └─ Vermelha (FALSE) → [M9]
   │     ├─ "Tenho outra dúvida" → [M5]
   │     └─ Próximo Passo (sem clique) → [Atraso 23h]
   │           └─ [Condição: Tag está Respondeu Ao Vivo OR Membro CG?]
   │                 ├─ Verde (TRUE) → encerra
   │                 └─ Vermelha (FALSE) → [M8] → fluxo M8
   │
   ├─ "Quero ver amostra" → [M3 "Legal!"]
   │     └─ [Atraso 10s]
   │           └─ [M6 "Prontinho 👇" + 2 PDFs anexados]
   │                 └─ [Atraso 7min]
   │                       └─ [M7 follow-up amostras + Smart Link Após Amostra + botão "Tenho outra dúvida"]
   │                             ├─ "Tenho outra dúvida" → [M5]
   │                             └─ Próximo Passo → [Ações #2: tag Após Amostra]
   │                                   └─ converge no [Atraso #3] do caminho acima
   │
   ├─ "Outra dúvida" → [M5]
   │
   └─ Próximo Passo (sem clique) → [Atraso 23h]
         └─ [Condição: Tag está Respondeu Ao Vivo OR Membro CG?]
               ├─ Verde (TRUE) → encerra
               └─ Vermelha (FALSE) → [M8] → fluxo M8
```

### Caminho convergente após M5 (resposta dúvida)

```
M5 → [Ações: Marcar Aberta + Tag Dúvida-Lead]
   → [Atraso #5: 23h]
      → [Condição: Tag está [CG] Respondeu Ao Vivo?]
         ├─ TRUE → encerra
         └─ FALSE → [Tag Lead Frio - Carrinho] → encerra
```

### Caminho M8 (fallback de não-clique)

```
M8 → (sem Ações intermediárias, vai DIRETO pro Atraso #5)
   → [Atraso #5: 23h]
      → [Condição: Tag está [CG] Respondeu Ao Vivo?]
         ├─ TRUE → encerra
         └─ FALSE → [Tag Lead Frio - Carrinho] → encerra
```

**Importante:** M8 **não passa pelas Ações** (Marcar Aberta + Tag Dúvida-Lead) que vêm depois da M5. Razão: pessoa caiu no fallback por silêncio, não pediu dúvida — não deve ser marcada como "Dúvida-Lead".

### Caminho da M9 (follow-up pós-clique no link)

```
M9 (botões: "Tenho dúvida" / "Outra hora")
   ├─ "Tenho dúvida" → [M5] (caminho de Live Chat)
   ├─ "Outra hora" → [Tag Lead Frio - Carrinho] direto (declaração explícita)
   └─ Próximo Passo (silêncio) → [Atraso 23h]
                                  → [Condição: Tag está Respondeu Ao Vivo?]
                                     ├─ TRUE → encerra
                                     └─ FALSE → [Tag Lead Frio - Carrinho]
```

---

## Condições de proteção em todos os atrasos longos

Todos os atrasos longos (≥ 1h) têm uma Condição imediatamente depois pra **interceptar** subscribers que interagiram durante o atraso. Sem isso, o fluxo automatizado continuaria mandando mensagens mesmo pra quem já está sendo atendido pelo humano (Live Chat) ou já comprou.

### Configuração padrão da Condição

Mesma estrutura nos 4 pontos do fluxo:

```
Condição:
- Tag está [CG] Respondeu Ao Vivo
- Tag está Membro CG

Operador: qualquer uma das condições (OR)

Saída Verde (TRUE = corresponde a alguma) → encerra (sem destino)
Saída Vermelha (FALSE = não corresponde a nenhuma) → continua o fluxo
```

### Onde está aplicada (4 pontos)

| Ponto | Posição | Próximo passo (vermelha) |
|---|---|---|
| 1 | Após Atraso 23h pós-M1 | M2 (3 botões) |
| 2 | Após Atraso 23h fallback M2 | M8 (mensagem genérica) |
| 3 | Após Atraso 23h fallback Mensagem #2 | M8 (mensagem genérica) |
| 4 | Após Atraso #3 (1h pós-clique link) | M9 (follow-up "conseguiu olhar?") |

### Lógica de decisão

- Pessoa **respondeu via texto livre** durante o atraso → tag `Respondeu Ao Vivo` aplicada pelo Default Reply → Condição vê tag → vai pra verde → **encerra** (humano atende)
- Pessoa **comprou** durante o atraso → tag `Membro CG` aplicada pelo webhook nativo → Condição vê tag → vai pra verde → **encerra**
- Pessoa **silêncio total** → nenhuma tag → vai pra vermelha → **continua** o fluxo

### Por que estilo POSITIVO ("está") em vez de NEGATIVO ("não é")

Padronização. As tags listadas representam **motivos de exclusão** (encerrar). É mais intuitivo de ler: *"se a pessoa tem qualquer dessas tags de exclusão, encerra"*. Misturar `Tag está` com `Tag não é` em uma mesma Condição quebra a lógica.

---

## Plano C - Trigger global Default Reply

### Função

Captura quando o subscriber envia **qualquer mensagem livre** (texto não capturado por keyword/botão) e aplica tag `[CG] Respondeu Ao Vivo`. Essa tag é checada pelas Condições no fluxo principal pra decidir se aplica Lead Frio ou encerra (humano atende).

### Configuração

Automação separada do fluxo principal, fica em **Automation** do Manychat:

**Trigger:** "O usuário envia uma mensagem - Resposta Padrão" (Default Reply)

**Condições (todas — AND):**
- Tag **está** `Carrinho Abandonado CG`
- Tag **não é** `[CG] Respondeu Ao Vivo`
- Tag **não é** `Membro CG`

**Ações:**
- Adicionar Tag `[CG] Respondeu Ao Vivo`
- Marcar Conversa como Aberta

### Lógica

Roda em paralelo ao fluxo principal. Se a pessoa responder em qualquer momento (em texto livre — não em botão), a tag é aplicada e o humano via Live Chat assume. Quando a Condição do fluxo principal rodar, vê a tag e encerra (não aplica `Lead Frio - Carrinho`).

---

## Tags estruturadas

| Tag | Quando é aplicada | Propósito |
|---|---|---|
| `Carrinho Abandonado CG` | Make aplica após webhook | Trigger do fluxo |
| `[CG] Clicou link - Após acesso` | Smart Link da M4 ao clicar | Métrica + segmentação caminho "Como eu acesso?" |
| `[CG] Clicou link - Após Amostra` | Smart Link da M7 ao clicar | Métrica + segmentação caminho "Quero ver amostra" |
| `[CG] Dúvida - Lead` | Após M5 (cliques explícitos em "Outra dúvida"/"Tenho outra dúvida") | Marcar lead que pediu atendimento |
| `[CG] Respondeu Ao Vivo` | Default Reply trigger global | Marcar quem interagiu via texto livre — humano assumir |
| `[CG] Lead Frio` | (genérica — não aplicada por esse fluxo) | Reservada para outros fluxos futuros (campanhas Meta, newsletter, etc.) |
| `[CG] Lead Frio - Carrinho` | Após Atraso 23h sem resposta nas Condições do fluxo de carrinho | Segmento específico de leads que tiveram alta intenção (chegaram a abrir checkout) e esfriaram |
| `Membro CG` | Webhook nativo Manychat-Hotmart de Compra Aprovada | Cliente — não receber mais mensagens de recuperação |

### Filosofia das tags

Híbrido entre tags **acumulativas** (jornada) e **de estado**:
- Tags de jornada acumulam (Clicou link, Respondeu, Dúvida)
- Membro CG funciona como tag de estado — quando aplicada, deve interromper qualquer remarketing

**Próximo passo opcional:** automação que remove `Carrinho Abandonado CG` quando `Membro CG` é aplicada (limpa base, evita conflito de tags). Pra MVP, mantemos acumulativas + uso de exclusões em automações.

---

## Smart Links com UTMs diferenciadas

### Por caminho

**M4 (Após acesso):**
```
https://pay.hotmart.com/N100354142M?checkoutMode=10&src=wpp|recuperacao|carrinho_abandonado|apos_acesso&sck=manychat_vitoria
```

**M7 (Após amostra):**
```
https://pay.hotmart.com/N100354142M?checkoutMode=10&src=wpp|recuperacao|carrinho_abandonado|apos_amostra&sck=manychat_vitoria
```

### Como configurado no Manychat

Manychat detecta automaticamente links inseridos em mensagens e oferece opção de tracking. Configuração:
- **URL do site:** URL Hotmart com UTM completa
- **Ações adicionais:** ON
- **Executar Ações:** "Ações #2" (que aplica tag de clique)

Tag aplicada **2x na prática** (no envio da mensagem + no clique do link). Aplicação 2x não gera erro mas afeta semântica da tag — vira "recebeu mensagem", não "clicou link". Pra métrica precisa de cliques, usar contador nativo do Smart Link no Manychat.

---

## Copy final aprovada — todas as mensagens

### M1 (mensagem inicial — aberta)

```
Oi {Primeiro Nome}, tudo bem?
Sou a Vitória, do Conexão Gestantes 🩺💚 
Notei que você quase garantiu seu acesso à nossa plataforma.
Quis te chamar pessoalmente porque algumas obstetras me procuram com dúvidas antes de fechar, e gosto de estar por perto pra ajudar.
*Me conta:* ficou com alguma dúvida sobre nossos materiais ou posso te ajudar de outra forma?
```

### M2 (Mensagem #1 — após Atraso 23h, com 3 botões)

```
Oi {Primeiro Nome}, voltei aqui 💚 
Sei o quanto seu dia é corrido. Mas, como você se interessou pelo Conexão Gestantes, deixei abaixo as dúvidas mais comuns que recebo. Me conta o que faz mais sentido pra você:
```

Botões (limite 20 chars cada):
- `Como eu acesso?` (15 chars)
- `Quero ver amostra` (17 chars)
- `Outra dúvida` (12 chars)

### Mensagem #2 ("Eu te explico" — resposta ao botão "Como eu acesso?")

```
Eu te explico! 💚

O *Conexão Gestantes* é uma plataforma online com materiais que otimizam suas consultas, encantam suas pacientes e agregam valor ao seu atendimento.

Todos os *materiais são prontos e 100% editáveis* — você pode acrescentar seu logo, alterar imagens e conteúdo. Ficam disponíveis imediatamente após a inscrição e podem ser acessados via computador, celular ou tablet.

O acesso é válido por 1 ano. Durante a vigência do seu plano, você tem acesso a *todo o pacote de materiais + atualizações*.

Quer garantir o seu agora? 👇
```

Sub-botões:
- `Quero o link`
- `Tenho outra dúvida`

### M3 ("Legal!" — resposta ao botão "Quero ver amostra")

```
Legal! 💚
Vou te enviar duas amostras pra você ver de perto a qualidade dos materiais.
```

### M6 ("Prontinho" — antes dos PDFs, 10s depois)

```
Prontinho 👇
```
+ 2 anexos PDF:
- `Conexao Gestantes - Diabetes Gestacional (amostra).pdf`
- `Conexao Gestantes - Quando ir pra maternidade.pdf`

Ambos com marca d'água: *"AMOSTRA · Conexão Gestantes · Acesso completo: conecttahub.com.br/conexaogestantes"*

### M7 (follow-up amostras — 7min depois, com Smart Link e botão)

```
Essas são só duas amostras do nosso acervo repleto de materiais que cobre desde orientações pré-natais até cuidados pós-parto — com guias clínicos completos e lâminas práticas pra você entregar ou apresentar para suas pacientes na consulta.

Quer ter acesso completo? Garante o seu agora 👇

[Smart Link mc.ht/s/XXXXXX → Hotmart Após Amostra]
```

Botão: `Tenho outra dúvida`

### M4 ("Claro, aqui está o seu link" — resposta ao sub-botão "Quero o link")

```
Claro, aqui está o seu link:

[Smart Link mc.ht/s/XXXXXX → Hotmart Após Acesso]

Se tiver dúvida na hora de fechar, pode me chamar.
Quando finalizar me avisa por aqui? 💚
```

### M5 ("Claro 💚" — resposta a "Outra dúvida"/"Tenho outra dúvida")

```
Claro 💚
Tô por aqui pra te ajudar!
Me escreve aqui, qual sua dúvida sobre o Conexão Gestantes?
```

### M8 ("Oi {Primeiro Nome}" — fallback de não-clique)

```
Oi {Primeiro Nome} 💚
Tô por aqui pra te ajudar!
Me escreve aqui, qual sua dúvida sobre o Conexão Gestantes?
```

### M9 (follow-up pós-clique no link)

```
Oi {Primeiro Nome}, conseguiu dar uma olhada no link? 💚

Se ficou alguma dúvida na hora de fechar, me avisa por aqui que eu te ajudo!
```

Botões:
- `Tenho dúvida`
- `Outra hora`

---

## Configurações críticas

### Atrasos

| Atraso | Valor original | Onde |
|---|---|---|
| Após M1 | 23h + janela 8-21h | Antes da M2 |
| Atraso #1 | 10s (sem janela) | M3 → M6 (antes dos PDFs) |
| Atraso #1 (segundo) | 7 minutos (sem janela) | M6 → M7 (após PDFs, antes follow-up) |
| Atraso #3 | 1h + janela 8-21h | Após clique nos Smart Links |
| Atraso #4 | 23h + janela 8-21h | Após M2 sem clique → vai pra M8 |
| Atraso #5 | 23h (sem janela) | Após M5/M8/M9 → antes da Condição |
| Atraso #2 | 23h (sem janela) | Após M9 → antes Tag Lead Frio |

**Janela 8-21h:** apenas em atrasos longos (> 1h). Atrasos curtos (segundos/minutos) seguem imediatamente — fazem parte da sequência conversacional.

### Webhook nativo Manychat-Hotmart

Mantém ativo apenas pra evento **"Compra Aprovada"** (aplica tag `Membro CG`). O webhook nativo de carrinho abandonado foi pausado/não usado (substituído pela ponte Make).

### Pixel e infraestrutura
- Pixel Meta: `1050936263908154`
- API Key Manychat: configurada na conexão "Manychat - CG"
- URL LP: `https://conecttahub.com.br/conexaogestantes`
- Hotmart Product ID: `N100354142M`

---

## Decisões importantes do design

### Por que separar M5 e M8

Ambas têm copy similar ("Tô por aqui pra te ajudar"), mas funções diferentes:
- **M5** = resposta a clique explícito em botões "Outra dúvida"/"Tenho outra dúvida". Pessoa pediu atendimento. Aplica `Dúvida-Lead`.
- **M8** = fallback de silêncio (não clicou em nada). Pessoa não pediu nada, só ficou em silêncio. **Não aplica Dúvida-Lead** (não passa pelas Ações).

Ambas convergem no mesmo Atraso #5 + Condição (reuso elegante).

### Por que Default Reply em vez de bloco User Input

User Input/Quick Question não está disponível no canal WhatsApp do Manychat dessa conta. Plano C com Default Reply rodando em paralelo resolve com 1 configuração pra todo o fluxo (em vez de adicionar lógica de timeout em cada ponto crítico).

### Por que tags por caminho (`Após acesso` vs `Após Amostra`)

Permite medir conversão por caminho. Em 30 dias dá pra dizer: *"X% das vendas recuperadas vieram do caminho amostra, Y% do caminho acesso"* — dado acionável pra otimizar criativos/copy.

### Por que M9 com Próximo Passo via Atraso + Condição

Em vez de Lead Frio direto (que aplicaria mesmo se a pessoa respondesse via Default Reply nesse meio tempo), o Atraso 23h + Condição protege contra falso positivo de Lead Frio.

---

## Limitações conhecidas e próximas iterações

### 1. Subscribers existentes (Make Resume handler)

**Status atual:** quando lead já existe no Manychat (criado por outro caminho ou abandonou carrinho antes), o Create Subscriber falha. Resume handler captura silenciosamente — subscriber existente **não recebe** mensagem de carrinho abandonado.

**Próxima iteração:** HTTP Module no Make pra fazer fallback. Quando Create falhar:
1. HTTP GET `findByCustomField` (precisa Custom Field `phone_lookup` setado)
2. Se encontrar → aplica tag com ID retornado
3. Se não encontrar → aceita perda

Pra cobrir 100%, precisa popular `phone_lookup` em massa pra subscribers existentes. Trabalho moderado, atacar quando tiver dado real do impacto (% de leads recorrentes nas primeiras semanas).

### 2. Tag duplicada no clique do link

Tag `[CG] Clicou link - Após acesso/Amostra` é aplicada 2x:
1. Bloco Ações #2 no fluxo principal (no envio da mensagem)
2. Smart Link no clique do link

Não é problema técnico (Manychat ignora aplicação 2x), mas afeta semântica da tag. **Refinamento:** remover Ações #2 do fluxo principal e deixar só nos cliques do Smart Link. Aí a tag passa a significar "clicou de verdade". Mas exige reorganização do fluxo (M9 e Condições dependem da Ações #2).

### 3. Atraso pós-PDFs (7 min)

Configurado em 7 min (entre PDFs e M7 follow-up). Decisão dada por discussão (1 min era curto, 30 min era longo, 5-7 min meio-termo). Pode precisar ajuste com dado real. Hipóteses:
- Se pessoa abre/lê PDFs em sessão única → 7 min ok
- Se pessoa só vê PDFs depois → atraso é irrelevante (vai ver tudo junto)

### 4. M9 Próximo Passo

Foi pelo caminho Lead Frio direto (Opção B), não Atraso + Condição (Opção C). Trade-off: se pessoa responder via Default Reply nesse momento, vai ganhar `Respondeu Ao Vivo` E `Lead Frio` simultaneamente (conflito tolerável, humano remove manual).

### 5. M9 falsamente atribuída a quem nem clicou no link

Atualmente a M9 ("conseguiu dar uma olhada no link?") chega pra todo mundo que recebe a M4 ou M7, mesmo quem não clicou de verdade. Razão: tag `Clicou link` é aplicada no envio da mensagem (não no clique). Mensagem fica deslocada pra quem não viu o link. Aceitar pra MVP.

---

## Casos de teste cobertos

✅ Caminho silêncio total: nada → M1 → M2 (sem clique) → M8 → silêncio → Lead Frio
✅ Caminho "Como eu acesso?" → "Quero o link" → M4 → clique link → M9 → Lead Frio
✅ Caminho "Quero ver amostra" → PDFs → M7 → clique link → M9 → "Outra hora" → Lead Frio
✅ Caminho "Outra dúvida" → M5 → silêncio → Lead Frio
✅ Default Reply: texto livre em qualquer ponto → tag `Respondeu Ao Vivo` → Live Chat

---

## Pendências e backlog

### Pra rodar em produção (concluído ✅)
- [x] Cenário Make funcionando com Resume handler
- [x] Trigger global Default Reply ativo
- [x] Smart Links com UTM diferenciada
- [x] Webhook nativo Manychat-Hotmart de Compra Aprovada ativo (pra `Membro CG`)
- [x] Atrasos revertidos pros valores de produção
- [x] Fluxo Manychat publicado (LIVE)

### Pra atacar nas primeiras 2-4 semanas
- [ ] Monitorar volume e taxas (cliques, respostas, Membro CG, Lead Frio)
- [ ] Avaliar % de leads existentes que ficam fora (justifica HTTP Module?)
- [ ] Avaliar copy da M1 e M2 baseado em respostas reais
- [ ] Confirmar atraso de 7 min pós-PDFs com dado real

### Backlog de longo prazo
- [ ] HTTP Module pra cobrir subscribers existentes (Solução robusta)
- [ ] Custom Field `phone_lookup` populado em massa
- [ ] Sequência de nurture pra Lead Frio CG (campanha de reativação)
- [ ] Recuperação 7 dias pós-abandono (3ª tentativa pra quem nunca interagiu)
- [ ] Sequência pós-clique sem compra em 48h (mensagem mais direta com social proof)
- [ ] Refinar tag de clique (remover Ações #2 do fluxo principal pra ter métrica granular)
- [ ] Automação que remove `Carrinho Abandonado CG` quando `Membro CG` aplicada (limpeza)
- [ ] Considerar adicionar Atraso + Condição no Próximo Passo da M9 (em vez de Lead Frio direto)

---

## Arquivos relacionados

- PDFs de amostra (em `/uploads/` ou onde estiver mantido):
  - `Conexao Gestantes - Diabetes Gestacional (amostra).pdf`
  - `Conexao Gestantes - Quando ir pra maternidade.pdf`
- Lista histórica de 27 leads importados manualmente (tagueados com tag temporária `[Carrinho Abandonado CG] - Lista Manual A partir de 30/04/2026`)
- Webhook nativo Manychat-Hotmart "Compra Aprovada" — aplica tag `Membro CG`

---

## Histórico

- **06/05/2026:** Implementação inicial do cenário Make (Webhook Hotmart → Create Subscriber → Manage Tags). Confirmado bug da integração nativa Manychat-Hotmart pra carrinho abandonado.
- **06/05/2026:** Construção do fluxo conversacional Vitória completo no Manychat.
- **07/05/2026:** Plano C implementado (Default Reply + tag `Respondeu Ao Vivo`). Fallbacks da M2 e Mensagem #2 configurados. M5 e M8 separados (Ações só pra M5). Smart Links com UTM diferenciada configurados. Resume handler adicionado no Make pra cobrir leads existentes. Lista histórica de 27 leads tratada por outro caminho (não automatizado). Tag de Lead Frio do fluxo trocada de genérica `[CG] Lead Frio` pra específica `[CG] Lead Frio - Carrinho` (preserva tag genérica pra outros fluxos futuros). **Condições de proteção adicionadas em 4 pontos** (após cada atraso longo): checa `Respondeu Ao Vivo OR Membro CG` e encerra se a pessoa interagiu/comprou durante o atraso — antes o fluxo continuava cego. Aguardando primeiro lead real pra validar end-to-end.
