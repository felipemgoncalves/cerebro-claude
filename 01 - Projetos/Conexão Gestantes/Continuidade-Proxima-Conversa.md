---
tags: [conexao-gestantes, continuidade, proxima-conversa, master, dossie]
data: 2026-05-12
status: ativo
versao: 2026-05-12 (manhã)
substitui: Continuidade-Proxima-Conversa.md de 2026-05-09 (manhã)
---

# Conexão Gestantes — Dossiê Completo pra Próxima Conversa

> **Como usar:** este é o documento master pra quem assume a próxima conversa. Lê do início ao fim antes de retomar qualquer trabalho. Cobre tráfego, criativos, LP, Manychat, redesenho estratégico, e estado atual de tudo.

---

## ⚡ ESTADO ATUAL EM UMA TELA

**Quem é o cliente:** Felipe Matheus, founder da Conectta Hub e do **Conexão Gestantes** (infoproduto B2B pra obstetras, ticket R$297, vendido via Hotmart, ~350 clientes ativos pagantes).

**O que está acontecendo:** Fase 1 de retomada de tráfego pago após meses pausado. Estamos no **dia 20 da retomada** (iniciada 23/04/2026).

**ROAS atual (consolidado 14 dias até 07/05):** 3,75x | **Excluindo Camp 04:** 5,95x → zona verde
**Investimento total acumulado (até 07/05):** R$1.991,13 | **27 vendas + 3 Order Bumps** | **Receita:** R$7.466,61

**Configuração de campanhas (atual, desde 09/05):**
- 3 campanhas ativas, R$180/dia (Camp_01 + Camp_02 + Camp_05)
- Camp_04 pausada em 09/05 cedo (3 sinais negativos convergentes, confirmado)

**Próximos checkpoints:** **12/05 hoje (sinal inicial Camp_05, em análise)** | 16/05 (decisão final Camp_05)

**Manychat carrinho abandonado:** EM PRODUÇÃO com filtro corretivo aplicado em 11/05 (filtro de phone válido no Make). Atraso M1→M2 = 8h.

**Manychat fluxo Dúvida WhatsApp pré-checkout:** EM PRODUÇÃO desde 11/05. Testado end-to-end, aguardando primeiro lead real.

---

## 🎯 1. TRÁFEGO PAGO — VISÃO COMPLETA

### 1.1 Arquitetura atual de campanhas

| Campanha | Tipo | Verba/dia | Status | ROAS recente |
|---|---|---|---|---|
| Camp 01 LL1% Compradores | LL1% baseado em quem comprou | R$60 | Performando | 5,17-5,66x |
| Camp 02 Aberto BR 25-55 | Segmentação aberta Brasil | R$60 | Performando | 5,78-6,31x |
| Camp 04 LL1% ViewContent 90D | LL1% baseado em quem viu LP | — | **Pausada 09/05** (R$215,94, 0 vendas, 5 dias) | 0x |
| Camp 05 V14 LL1% Iso | LL1% Compradores, Vídeo 14 isolado | R$60 | T0 = 08/05 ~15h, em medição | em análise |

**Camp 03** (Vídeo 4 isolado) foi pausada em 27/04 — Vídeo 4 confirmado como morto.

### 1.2 Princípios operacionais críticos (NUNCA esquecer)

1. **NUNCA aumentar verba em campanha existente.** Histórico de 9 meses confirma: aumentos de budget (mesmo +20%) desestabilizam consistentemente. **Solução:** criar conjuntos/campanhas novas em vez de escalar atuais. Discussão de 09/05 questionou se a regra ainda se aplica com setup atual; conclusão: vale testar, mas **somente após 16/05** (pós-checkpoint final Camp_05) pra não contaminar variáveis.

2. **Saturação vem antes de fadiga criativa.** Frequência alta indica saturação de audiência, não criativo morto. Solução: lookalike fresco antes de trocar criativo.

3. **Atribuição via WhatsApp pós-anúncio funciona.** Pessoa vê anúncio, pergunta no WPP, fecha via link. Meta atribui pela janela de 7 dias clique. **Confiar nas vendas marcadas pelo gerenciador.**

4. **Vendas sem UTM (`src=(none)`) costumam ser do Meta também.** Se Felipe confirma origem real, contar como Meta. Caso confirmado: Lisandra Campos (venda 08/05) — UTM `(none)`, atribuída pela Camp_01 com ROAS 5,40x, e Felipe confirmou venda direta (sem passagem pelo WhatsApp).

5. **Criativos visuais com música performam melhor que com voz.** Padrão histórico. Vídeo 10 e 15 são exemplos.

6. **Botões CTA da LP devem abrir pop-up imediatamente.** Bug histórico de "rolar página" gerava 84% dead clicks. Resolvido em 30/04/2026.

7. **CTR alto + 0 vendas = LP, não criativo.** Vídeo 4 com CTR 1,32% e 0 vendas confirmou esgotamento.

8. **Ruído estrutural do Instagram é uniforme entre audiences (35-40% das sessões mobile ≤5s).** Não é problema de targeting — é estrutural do canal. Alavanca real: hook do criativo nos primeiros 0,5-1s. Ver seção 2.5.

9. **Algoritmo do Meta esmaga diversidade de criativos.** Cada campanha tem 1 anúncio dominante absorvendo 90%+ do tráfego, mesmo em CBO/ABO com 4 anúncios disponíveis. Pra testar criativos secundários, isolamento em campanha dedicada é a única alternativa.

10. **Em estrutura 1-1-1 (1 campanha + 1 conjunto + 1 anúncio), CBO e ABO são funcionalmente equivalentes.** Escolha vira critério de consistência com baseline (replicar exatamente a campanha de origem).

11. **Critérios convergentes encurtam régua.** Quando há múltiplos sinais negativos independentes, decisão pode ser antecipada. Camp_04: pausada em 4 dias (régua era 7) com base em 0 vendas + 2 IC + mediana Clarity 10s + queda de entrega algorítmica (4 sinais). Validado em 09/05.

12. **Exploração proativa de público ≠ teste de aumento de verba.** Abrir audiência nova **não-sobreposta** à Camp_01 (LL3% excluindo LL1%, retargeting IC sem compra, interesses) não contamina a Camp_05 em curso — desde que não use LL1% Compradores (público compartilhado). Decisão de 09/05: standby até pelo menos checkpoint inicial Camp_05.

### 1.3 Performance Fase 1 detalhada

**Período A (23-30/04, 7 dias):**
- Investimento: R$969,18 | 9 vendas | R$2.376,99 | **ROAS 2,45x** | CPA R$107,69

**Período B (01-04/05, 4 dias) — pós-otimizações:**
- Investimento: R$483,92 | 10 vendas | R$2.892,83 | **ROAS 5,98x** | CPA R$48,39

**Período C (05-07/05, 3 dias):**
- Investimento: R$538,03 | 8 vendas + OB | R$2.196,79 | **ROAS 4,08x** consolidado
- Sem Camp 04: ROAS 5,95x (estável)
- Camp 04 sozinha: R$168,63 sem vendas (3 dias)

**08/05 (sexta):**
- Camp_01: R$48,94 | 9 cliques | 5 LP views | 3 IC | **1 venda (Lisandra)** | R$264,11 | **ROAS 5,40x**
- Camp_02: R$50,92 | 11 cliques | 11 LP views | 0 IC | 0 vendas
- Camp_04: R$39,72 | 7 cliques | 4 LP views | 0 IC | 0 vendas
- Camp_05 dia 1 parcial (~9h de entrega): R$29,27 | 4 cliques | 4 LP views | 1 IC | 0 vendas
- Total dia: R$168,85 | 1 venda | R$264,11 | ROAS 1,56x

**Salto Período A → B:**
- Vendas/dia: +94% (1,29 → 2,5)
- ROAS: +144% (2,45 → 5,98x)
- CPA: -55% (R$107 → R$48)
- IC/dia: +477% (1,3 → 7,5)

### 1.4 Criativos — estado atual

**Vídeo 15 (Criativo C) — HERO ⭐**
- Mesa de madeira, POV obstetra, replica fórmula do Vídeo 4 histórico
- Domina entrega em todas as campanhas (90%+ do tráfego)
- Gera 80%+ das vendas
- **Janela de fadiga estimada:** ~5 semanas em rodagem (Vídeo 4 fadigou em ~2 meses)
- **Frente 1 do plano:** produção de 2 sucessores em 2 semanas

**Vídeo 14 (Criativo B) — Em teste isolado na Camp_05**
- Fundo de plantas, 6 frames
- **ROAS agregado real histórico: 5,73x** (R$138,24, 35 cliques, 31 LP views, 3 IC, 3 vendas, R$792,33 receita, em 3 instâncias)
- CTR 1,14%, taxa LP→IC 9,68%, frequência 1,74
- **Atenção:** a frase "ROAS 18x latente" repetida em notas anteriores vinha de janela específica de 4 cliques (Camp_01, 01-04/05) e era estatisticamente inflada. **O número correto é 5,73x.** Recalibrado em 08/05/2026.
- Performance verde sustentada em duas das três instâncias, mas sempre em micro-volume — algoritmo do Meta nunca deu entrega significativa.
- **Camp_05 V14 LL1% Iso (T0 08/05 ~15h) é o primeiro teste com volume controlado.** Decisão final em 16/05.

**Vídeo 13 (Criativo A) e Estático 17**
- Praticamente desligados pelo algoritmo
- Mantidos ativos custo zero — abre porta pra surpresa em público novo
- Decisão sobre testar isolado: AGUARDAR resultado da Camp_05. Se Vídeo 14 validar, abre lógica pra testar V13/Est17 em sequência (Camp_06/07). Se Vídeo 14 refutar, hipótese do "esmagamento" cai e provavelmente eles são fracos mesmo.

**Vídeo 4 — MORTO**
- Ex-campeão histórico (ROAS 4,42x)
- Camp 03 com isolamento confirmou esgotamento (5 dias, 0 vendas, R$168)
- Não recuperar

### 1.5 Régua oficial (aplicável a todas as campanhas)

- **Verde (manter/escalar):** ROAS ≥3x AND CPA ≤R$80 AND CTR ≥1%
- **Amarelo (mais 7 dias):** ROAS 2-3x AND CPA R$80-120
- **Vermelho (pausar):** ROAS <2x OR CPA >R$120 OR 0 vendas em 7 dias

**Gatilho de subentrega (não-régua, complementar):** se em 3 dias o gasto ficar abaixo de R$100, sinal de rejeição algorítmica — encerrar antes da janela completa.

### 1.6 Status Camp_04 — PAUSADA em 09/05

Pausa confirmada em 09/05 ~9h, no dia 5 da régua original (vs 12/05 que era a data oficial).

**Justificativa — 4 sinais negativos convergentes:**
1. **0 vendas em 4 dias completos** (R$215,94 gastos total no período)
2. **Apenas 2 IC em ~R$220 gastos** — baixa intenção mesmo no topo do funil
3. **Mediana de duração 10s no Clarity** (vs 20-25s das outras audiences) — sinal qualitativo independente
4. **Algoritmo reduziu entrega progressivamente** (R$93 → R$47 → R$37 → R$7 em 4 dias) — Meta "desistindo" do público

**Aprendizado-chave:** Vídeo 15 (HERO) não converteu nessa audience com R$185 e 32 cliques. O mesmo Vídeo 15 que carrega 80%+ das vendas nas Camp_01 e Camp_02 não gerou venda. **O problema era o público (LL1% ViewContent 90D), não o criativo.** O sinal "viewer da LP" é estatisticamente mais fraco que "comprador" pra alimentar lookalike.

### 1.7 Status Camp_05 V14 LL1% Iso — em medição

**Subida em 08/05/2026 ~15h.** T0 travado a partir da primeira impressão real (R$0,64 gastos no momento da confirmação).

**Configuração:**
- Naming: `Camp 05 V14 LL1% Iso 080526`
- sck: `[CG] - 05 - 080526 - V14 LL1% Iso - Página de Vendas`
- Audience: LL1% Compradores BR (mesma da Camp_01)
- Exclusões: Compradores 180D (Purchase) + Compr. CG e KCPC histórico (idênticas Camp_01)
- Estrutura: CBO, 1-1-1, R$60/dia
- Pixel: 1050936263908154 (mesmo)
- Princípio aplicado: cópia exata da Camp_01, única variável é o criativo (Vídeo 14)

**Janelas de avaliação:**
- **12/05 manhã (Dia 3 completo, sinal inicial):** olhar gasto, CTR, taxa LP→IC, vendas — **EM ANÁLISE HOJE**
- **16/05 manhã (Dia 7 completo, decisão final):** aplicar régua oficial

**Dia 1 parcial (08/05, ~9h entrega):** R$29,27 | CTR 0,82% | 4 cliques | taxa LP→IC 25% | 1 IC | 0 vendas. Sinal qualitativo bom mas amostra muito pequena.

### 1.8 Hipóteses abertas em tráfego

1. **Vídeo 14 sustenta ROAS verde com volume real (Camp_05).** Histórico agregado mostra 5,73x mas em micro-volume. Decisão em 16/05.

2. **Camp 02 Aberto pode estar esgotando.** CTR caiu de 1,93% pra 1,40% em 04/05, estabilizou em 1,49% no Período C. Em 08/05 (sexta), 0 IC anômalo — provavelmente efeito sexta-feira em B2B, não sinal de fadiga. Confirmação real só com segunda 12/05 (hoje). Monitorar.

3. **LL3% Compradores ou retargeting IC sem compra como exploração proativa.** Standby — Felipe questionou em 09/05 se faz sentido esperar a Camp_01 cair (gatilho original Frente 6). Conclusão: exploração proativa é diferente de aumento de verba, pode ser feita SEM contaminar Camp_05 desde que o público não sobreponha LL1%. Decisão de quando ativar fica pra após 16/05.

4. **Aumentar verba na mesma campanha funciona no setup atual?** Questão levantada em 09/05 — a regra "nunca aumentar verba" foi estabelecida em contexto antigo (Vídeo 4 hero, LP com bug, imagens pesadas). Decisão: testar SOMENTE após 16/05 (caminho B), com Camp_01 isolada, +R$20-30/dia por 5-7 dias.

### 1.9 Hipóteses fechadas

- ✅ ~~Sessões com menos de 5s representam ruído significativo~~ — **CONFIRMADA em 08/05.** 35,4% mobile, ruído estrutural uniforme entre audiences. Ver seção 2.5.
- ✅ ~~Camp_04 LL1% ViewContent 90D pode não converter como Camp_01~~ — **CONFIRMADA.** Pausada em 09/05 com 4 sinais convergentes.

### 1.10 Próximas escaladas planejadas (após Fase 2)

- LL3% Compradores excluindo LL1% (próxima escalada de público — Frente 6)
- Retargeting IC sem compra 180D (público quente)
- Interesses (Obstetrícia, Ginecologia, SBRP, FIGO) — alternativa ao Aberto
- Inlead/quiz (mudança estrutural de funil)
- Conteúdo orgânico (alimentar seed Visitantes LP)
- **Lead capture com isca digital — prioridade histórica alta (ver Frente 7 nova)**

---

## 🖥️ 2. LANDING PAGE — ESTADO E DESCOBERTAS

### 2.1 URL e plataforma

- URL: `https://conecttahub.com.br/conexaogestantes`
- Plataforma: **Hotmart Pages** (limitações conhecidas — ver Playbook de Otimização)
- Pixel Meta: `1050936263908154`
- Microsoft Clarity instalado via GTM
- Hotmart Product ID: `N100354142M`

### 2.2 Funil de venda real

**TODOS os botões CTA da LP levam ao formulário de pré-checkout.** Logo:

```
LP visit → Click CTA → Form pré-checkout (= Initiate Checkout) → Hotmart → Compra
```

**Não há rota de venda alternativa.** Quem não passa pelo formulário não compra.

**No Clarity, o evento "Enviar formulário" ≈ Initiate Checkout do Meta.**

### 2.3 Heatmap de scroll — linha de morte identificada

```
✅ 100%  ────  HERO + selos
🔥  ~50% ────  LINHA DE MORTE (na 1ª seção descritiva pós-hero)
🟡  ~30% ────  Seção "Não é pra você se..."
🟢  ~22% ────  Resto da página (price box, depoimentos, garantia)
```

**Apenas ~22-25% chega no resto da LP** (price box, depoimentos, garantia). Mas convertem **41% IC→Venda** — quem chega convertida bem.

### 2.4 Conversões reais

| Métrica | Pré (23-27/04) | Pós B (01-04/05) | Pós C (05-07/05) |
|---|---|---|---|
| Sessões/dia | ~53 | ~54 | ~58 |
| LP→IC | 2,64% | 11,68% | 9,20% |
| LP→Venda (bruta) | ~2,8% | 4,67% | 4,60% |
| LP→Venda (qualificada >5s mobile) | — | — | **~7%** |
| Dead clicks | 4-9% | 0% | 0% |
| Forms enviados/dia | 1-3 | 6-10 | 5-6 |

**LP→Venda 4,55% bruta é EXCEPCIONAL pra info-product B2B** (padrão típico 1-3%, otimizado 3-5%).
**LP→Venda 7% qualificada (filtrando ruído ≤5s)** é o número correto pra medir saúde da LP daqui em diante.

**Otimizações sustentaram efeito por 7+ dias** — não foi pico isolado.

### 2.5 Hipótese das sessões curtas — CONCLUÍDA em 08/05/2026

**Investigação executada em 08/05.** Período: 01-07/05, CSV Clarity filtrado por mobile (333 sessões).

**Achados:**
- **35,4% das sessões mobile (118 de 333) têm duração ≤5s e zero cliques registrados.** 
- Sample qualitativo de 6 gravações confirmou padrão:
  - 33% (2/6) **tela cinza** — clique acidental no feed, webview do iOS nem renderizou antes do voltar
  - 67% (4/6) **página carregou e usuário saiu sem nenhuma interação** — vista-relâmpago, tempo curto demais pra ler/processar
- Em ambos os sub-padrões, sessão é estatisticamente impossível de gerar venda — só infla denominador.

**Derivação da conversão qualificada (~7% mobile):**
- Total sessões mobile no período: 333
- Ruído ≤5s removido: 118
- Denominador qualificado: 215
- Vendas no período: 18 totais (10 período B + 8 período C)
- Vendas mobile estimadas em ~85% do total = ~15 vendas
- Conversão qualificada ≈ 15/215 ≈ **7,0%**
- **Atenção:** contém estimativa de vendas mobile, não medição direta. Refinar quando Hotmart desagregar por device.

**Cruzamento por audience (ruído é estrutural, não de targeting):**
- Camp_01 LL1% Compradores: 35,4% ≤5s
- Camp_02 Aberto BR 25-55: 38,6% ≤5s
- Camp_04 LL1% VC90D: 40,9% ≤5s

Diferenças estatisticamente irrelevantes — o ruído é fenômeno do canal Instagram (cliques acidentais em rolagem rápida), não problema de público. Trocar audience não resolve. **Alavanca real: hook do criativo nos primeiros 0,5-1s.**

**Decorrência estratégica:**
- LP qualificada está em ~7% mobile, perto do teto pra info-product B2B → LP **não é mais o gargalo prioritário**.
- 88,86% dos visitantes "saem sem clicar" foi recalibrado: descontando o ruído, real é **~63% saem sem clicar entre os qualificados** — ainda alto, mas é a base correta.
- Foco de otimização sai da LP e vai pra **qualificação upstream** (criativo, audience). Mexer em LP rende pouco daqui pra frente; mexer em quem chega rende muito.

**Funil no Clarity configurado em 11/05** com filtro "URL contém https://conecttahub.com.br/conexaogestantes" (cobre URLs com e sem UTM). Etapa única: "Enviar formulário" = Initiate Checkout.

### 2.6 Otimizações aplicadas e sustentadas

**24/04 — Ajustes de copy LP:**
- H1/H2 reescritos
- "2.000 obstetras" → "350 obstetras" (consistência com base real)
- Removida exclamação no fim

**30/04 — Unificação dos 3 botões CTA (impacto MAIOR):**
- Antes: só último botão abria pop-up, outros só rolavam página
- 80 dos 96 cliques (84%) eram dead clicks frustrados
- Após: todos abrem pop-up imediatamente
- Resultado: IC dispararam de ~1/dia pra 6,75/dia

**01/05 — Otimização de imagens:**
- Performance Score: 73 → 89 (mobile) e 99% (desktop)
- LCP: 5,2s → 2,9s (mobile)
- Vilões: foto Sueli (115KB → 20KB), composição mockups duplicada (95KB×2 → 30KB)
- Causa raiz: imagens com dimensões físicas até 13x maiores que tamanho de exibição

### 2.7 Pendências estruturais da LP (Frente 5 do plano de redesenho)

Após hipótese das sessões curtas confirmada, prioridade da LP **caiu** mas a linha de morte ainda existe entre qualificados (~37% saem em 5-30s, 78% sem clicar). Atacar UMA intervenção isolada quando chegar a hora dessa frente:

- [ ] Social proof strip pós-hero (depoimentos + 350+ obstetras)
- [ ] Price anchor antes do price box
- [ ] Urgência honesta (sem falsa escassez)
- [ ] CTA sticky no mobile
- [ ] Hierarquia visual do price box

**Quando atacar:** Frente 5, após estabilizar Frentes 1 e 2. Escolher 1 só, não atacar duas em paralelo (não dá pra ler resultado).

### 2.8 Auditoria periódica obrigatória

**Aprendizado crítico:** LP estava em deterioração silenciosa (84 → 73 em 1 mês sem ninguém perceber).

**Auditoria mensal recomendada:**
1. PageSpeed mobile + GTmetrix desktop
2. Comparar com benchmark anterior
3. Se Performance caiu >5 pontos, expandir "Melhorar a entrega de imagens"
4. Otimizar 3 maiores vilões no Squoosh
5. Republicar e medir

Ver `Playbook - Otimizacão LP Hotmart.md` pra detalhes completos.

---

## 🤖 3. MANYCHAT — DOIS FLUXOS EM PRODUÇÃO

### 3.1 Visão geral

Existem **dois fluxos paralelos** no Manychat, conectados por design mas independentes:

| Fluxo | Trigger | Tag de origem | Status |
|---|---|---|---|
| **Carrinho Abandonado** | Hotmart webhook PURCHASE_OUT_OF_SHOPPING_CART | `[CG] Carrinho Abandonado` | EM PRODUÇÃO |
| **Dúvida WhatsApp pré-checkout** | Keyword no texto pré-preenchido do botão wa.me da LP | `[CG] Lead Frio - Site Dúvida` | EM PRODUÇÃO (deploy 11/05) |

A decisão de manter dois fluxos paralelos (em vez de gatilhos múltiplos no mesmo fluxo) foi tomada em 11/05 priorizando **mensurabilidade** — tags e UTMs exclusivas por fluxo permitem comparar performance dos dois funis. Custo: manutenção em dois lugares, exige disciplina de replicar mudanças quando aplicáveis.

### 3.2 Fluxo Carrinho Abandonado

**Estado:** EM PRODUÇÃO desde 07/05/2026. Já caíram leads reais (validação técnica feita). Filtro corretivo aplicado em 11/05.

**Arquitetura:**

```
Hotmart webhook PURCHASE_OUT_OF_SHOPPING_CART
   ↓
Make (cenário "CG - Carrinho Abandonado")
   ├─ FILTRO: phone existe AND phone como número > 999999999 (novo em 11/05)
   ├─ Create Subscriber
   │  └─ Error Handler (Resume) — silencia erro de subscriber existente
   └─ Manage Tags (aplica [CG] Carrinho Abandonado)
      ↓
Manychat (fluxo "Vitória" trigger por tag)
```

**Fluxo da Vitória — etapas:**

1. **M1 inicial** — apresentação aberta sem botões
2. **Atraso 8h** + janela 8-21h ⚠️ (era 23h, reduzido em 08/05)
3. **Condição** (encerra se Respondeu Ao Vivo OR Membro CG)
4. **M2** — 3 botões: "Como eu acesso?", "Quero ver amostra", "Outra dúvida"
5. Vários sub-fluxos por botão
6. **M9** — follow-up 1h após clique no link de pagamento
7. Tag final: `[CG] Lead Frio - Carrinho` ou `Membro CG` (se converteu)

### 3.3 Fluxo Dúvida WhatsApp pré-checkout (NOVO — deploy 11/05)

**Estado:** EM PRODUÇÃO desde 11/05/2026. Testado end-to-end com 4 caminhos validados. Aguardando primeiro lead real.

**Trigger:** keyword match no texto pré-preenchido do botão wa.me da LP (botão flutuante + botão final da página).

**Estrutura:**

```
Lead clica botão wa.me na LP → texto pré-preenchido
   ↓ (trigger keyword)
M1-Início: "Oi! Que bom que veio 💚 ... Quer que eu te explique ou tem alguma dúvida específica?"
   ├─ Botão "Pode me explicar" → M1-Longa (explicação genérica)
   │   ├─ Botão "Quero o link" → M2 (envia link Hotmart) → 1h delay → M3 follow-up
   │   │   ├─ Botão "Tenho dúvida" → M5 (escreve aqui)
   │   │   └─ Botão "Outra hora" → 23h delay → M8 (segundo follow-up)
   │   └─ Botão "Tenho outra dúvida" → M5
   └─ Botão "Dúvida específica" → M5: "Pode mandar 💚 Me conta o que tá te deixando em dúvida?"
       ↓ (8h delay com janela 8-21h)
       Condição #2: se Respondeu Ao Vivo OR Membro CG → encerra
                    se não → M-Amostra-1 (oferta de 2 amostras)
                              ↓ Botão "Quero ver amostra"
                              M-Amostra-Files (envia arquivos)
                              ↓ 7min delay
                              M7 (CTA final com link + tag [CG] Clicou link - Após Amostra)
```

**Tags exclusivas (pra mensurabilidade):**
- `[CG] Lead Frio - Site Dúvida` — entrada no fluxo
- `[CG] Clicou link - Após acesso` — quem pegou o link direto
- `[CG] Clicou link - Após Amostra (Dúvida Site)` — quem clicou via amostra
- `[CG] Lead Frio - Carrinho (Dúvida Site)` — saída sem conversão

**Decisão intencional sobre Plano C:** quando lead responde texto livre na M5, Plano C aplica `Respondeu Ao Vivo` e Condição #2 intercepta a amostra automatizada — Felipe assume conversa pessoalmente. Lead que não responde em 8h recebe amostra como tentativa automatizada de recuperação.

**Volume e conversão de baseline (antes do deploy):** 5-7 leads/semana via WhatsApp pré-checkout, 1-2 fechando (~15-30%). Objetivo do novo fluxo: subir essa taxa de conversão.

### 3.4 Decisões importantes do design (válidas pros dois fluxos)

**Plano C — Default Reply trigger global:** detecta resposta livre e aplica tag `[CG] Respondeu Ao Vivo` + Marca Conversa Aberta. Roda em paralelo aos fluxos automatizados.

**Condições de proteção em pontos críticos:** após cada atraso longo, checa se subscriber tem `Respondeu Ao Vivo OR Membro CG`. Se sim, encerra fluxo automatizado (humano cuida via Live Chat).

**Padrão Manychat:** estilo positivo (`Tag está`) + operador OR + setas vermelhas continuam fluxo. NUNCA misturar `Tag está` com `Tag não é` na mesma Condição.

### 3.5 Limitações conhecidas

1. **Subscribers existentes** dão erro 400 no Create. Resume handler silencia (MVP). Solução robusta no backlog: HTTP Module com Custom Field `phone_lookup`.

2. **Subscribers importados via CSV NÃO disparam fluxo automatizado** mesmo com tag aplicada. Manychat tem proteção contra spam. Usar pra esses casos: tratar manualmente ou Broadcast.

3. **Tag de clique aplica 2x** (envio mensagem + clique link). Não é bug crítico mas afeta semântica. Refinar depois.

4. **Trigger keyword é case-sensitive e match exato.** Se o lead editar o texto pré-preenchido antes de enviar (hábito comum em mobile), o fluxo Dúvida não dispara — cai no Default Reply (Plano C) e tu atende manualmente.

5. **Webhooks Hotmart sem campo phone causavam erro fatal no Make.** Em 11/05 foi resolvido com filtro `phone exists AND phone > 999999999`. Antes do filtro, esses erros desativavam o cenário inteiro (causando perda de 2 dias de carrinhos abandonados em sábado/domingo 09-10/05).

### 3.6 Mudanças de 08-11/05

**08/05 — atraso M1→M2 reduzido de 23h pra 8h** (carrinho abandonado).
- **Hipótese:** aproveitar memória quente do abandono. Em 24h, obstetra esquece por que clicou. 8h pega ela ainda no contexto.
- **Avaliar resultado em 14 dias** comparando com baseline de 23h. Janela de avaliação: ~22/05.

**11/05 — deploy fluxo Dúvida WhatsApp pré-checkout.**
- Estrutura paralela ao carrinho com tags/UTMs exclusivas.
- Testado end-to-end.

**11/05 — filtro corretivo no Make do carrinho abandonado.**
- Causa raiz identificada: alguns webhooks Hotmart sem campo phone.
- Sintoma original: `BundleValidationError - Missing value of required parameter 'subscriberId'`.
- Solução: filtro entre webhook e Create Subscriber. Condição: `phone exists AND phone Numeric > 999999999`.
- Benefício adicional: cenário não desativa mais por erros consecutivos.

### 3.7 Configurações técnicas críticas

- **Pixel Meta:** `1050936263908154`
- **API Key Manychat:** configurada na conexão "Manychat - CG"
- **URL LP:** `https://conecttahub.com.br/conexaogestantes`
- **Hotmart Product ID:** `N100354142M`
- **Cenário Make:** "CG - Carrinho Abandonado" (Active, com filtro phone)
- **Fluxos Manychat ativos:** "[Wtsp] Carrinho abandonado - CG" + "[Wtsp] Dúvida site - CG"
- **Webhook nativo Manychat-Hotmart:** ativo apenas pra "Compra Aprovada" (aplica `Membro CG`)
- **Webhook URL Make:** `https://hook.us2.make.com/syxb7v9sdvhteb97796ww6yn9y4ykjop`

### 3.8 27 leads históricos do carrinho

Lista de 27 leads que abandonaram carrinho entre o início da implementação e o lançamento foi tratada **manualmente** (fora do fluxo automatizado), pois subscribers importados não disparam fluxo via tag.

---

## 🗺️ 4. PLANO DE REDESENHO — 7 FRENTES PRIORIZADAS

Após hipótese das sessões curtas confirmada, foco estratégico saiu de "otimizar LP" e foi pra "alimentar pipeline de criativos, proteger o que funciona, e expandir captação". Premissas-chave:

- LP qualificada está em ~7% (perto do teto)
- Ruído estrutural de 35% é não-corrigível por targeting
- Vídeo 15 absorve 90%+ da entrega — fadiga é questão de tempo
- Vídeo 14 tem ROAS agregado 5,73x mas precisa de volume real pra confirmar

### Frente 1 — CRÍTICA — Pipeline de sucessores do Vídeo 15

Vídeo 4 fadigou em ~2 meses. Vídeo 15 já está em ~5 semanas concentrando 90%+ da entrega. Sem sucessor pronto, ROAS despenca quando ele cair.

**Ação:** produzir 2 variantes mantendo wooden table + sentimento clínico, **com música (não voz)**, variando o hook nos primeiros 3s.

**Prazo:** 2 semanas até estar em teste.

### Frente 2 — ALTA — Camp_05 V14 + decisão de Camp_06

Camp_05 V14 LL1% Iso (subida 08/05) valida ou refuta mérito real do Vídeo 14 com volume controlado.

**Decisão final:** 16/05 conforme régua oficial.

**Se validar (verde):** considerar Camp_06 com LL3% Compradores + Vídeo 14, abre lógica pra Camp_07 com Vídeo 13/Estático 17 também isolado.

**Se refutar:** hipótese do "esmagamento por Vídeo 15" cai, foco volta totalmente pra Frente 1.

### Frente 3 — ALTA — Hook do criativo pra reduzir cliques acidentais

Pluga na Frente 1: nas variantes novas do Vídeo 15, testar hooks que segurem atenção em 1s (pergunta direta, número impactante, cena clínica forte).

**Hipótese:** reduzir ruído de 35% pra 30% libera 7,7% de orçamento real sem aumentar verba.

**Métrica:** %≤5s no Clarity por criativo, semanal.

### Frente 4 — MÉDIA — Régua atualizada de KPIs

**Conversão qualificada (~7% mobile)** como métrica primária da LP. **%≤5s** como métrica de saúde do criativo. **Mediana de duração por audience** como métrica de qualidade do tráfego pós-filtro.

**Ação:** atualizar dashboard semanal e notas operacionais.

**Prazo:** antes do checkpoint 16/05.

### Frente 5 — MÉDIA — Uma única intervenção na linha de morte da LP

Linha de morte na 1ª seção pós-hero ainda existe entre qualificados (~37% saem em 5-30s, 78% sem clicar). Ganho marginal mas real.

**Ação:** escolher UM dos 5 itens das pendências estruturais (seção 2.7). Não os dois juntos.

**Prazo:** após estabilizar Frentes 1 e 2.

### Frente 6 — STANDBY — Exploração proativa de público

Camp_01 LL1% Compradores é genuinamente superior (mediana 25s vs 20s da Camp_02). Quando saturar, exploração é o caminho natural.

**Opções a testar (não-sobrepostas com LL1%):**
- LL3% Compradores **excluindo LL1%** (anel externo)
- Retargeting IC sem compra 180D (público quente)
- Interesses (Obstetrícia, Ginecologia, SBRP, FIGO) — alternativa ao Aberto

**Gatilho original:** CTR Camp_01 cair abaixo de 1,2% por 5 dias seguidos.

**Revisão de 09/05:** Felipe questionou se faz sentido esperar a queda. Conclusão: exploração proativa é diferente de aumento de verba — pode ser feita SEM contaminar Camp_05 desde que público não sobreponha. Decisão final de quando ativar: pós 16/05.

### Frente 7 — STANDBY — Captação ampliada via isca digital (NOVO 11/05)

**Contexto:** hoje a captação é majoritariamente direta — anúncio → LP → checkout, com WhatsApp como canal de dúvida pré-checkout. Falta uma camada de captura "antes da compra" pra médicos que não estão prontos pra decidir mas têm interesse no tema. Isca digital (ebook, kit de amostras, calculadora, checklist, mini-curso, etc.) entraria como ponto de entrada de funil, gerando lista de leads pra nutrição e conversão posterior.

**Relação com o que já existe:**
- "Lead capture com kit amostra grátis" já estava como **prioridade histórica alta** no backlog.
- "Inlead/quiz como mudança estrutural de funil" também estava no backlog longo prazo.
- Frente 7 trata isca digital como **frente própria**, não como recurso acessório.

**Decisões pendentes quando ativar:**
- Qual isca testar primeiro (formato + conteúdo)
- Qual canal de captação (LP dedicada? botão na LP atual? campanha separada?)
- Como nutrir os leads capturados (sequência de e-mail? WhatsApp? mix?)
- Como atribuir conversões da nutrição

**Status:** standby, aguardando definição de prioridade real e detalhamento.

---

## 📊 5. PRÓXIMOS PASSOS PRIORIZADOS

### Hoje (12/05) — checkpoint Camp_05

- [ ] **Análise dos dias 08-11/05 (4 dias incluindo o parcial)** — Felipe vai enviar relatório consolidado. Olhar especialmente Camp_05 nos 3 dias completos (09, 10, 11/05).
- [ ] Aplicar régua oficial: gasto, CTR, taxa LP→IC, vendas, ROAS.
- [ ] **Decisão inicial Camp_05:** seguir até 16/05 OU pause antecipado se sinal de subentrega.
- [ ] Validar Camp_02 (suspeita de 08/05 era efeito sexta — primeira leitura de segunda hoje).

### Próximos dias

- [ ] **16/05:** decisão final Camp_05. Aplicar régua oficial. Se verde, planejar Camp_06.
- [ ] **Após 16/05:** decidir sobre teste de aumento de verba em Camp_01 (caminho B) E/OU ativação de exploração proativa de público (Frente 6).
- [ ] **~22/05:** avaliar atraso M1→M2 8h vs 23h após 14 dias de dado real.

### Frentes em paralelo (próximas 2 semanas)

- [ ] **Frente 1+3:** iniciar briefing dos sucessores do Vídeo 15 (com música, hook nos primeiros 3s).
- [ ] **Acompanhar Manychat carrinho abandonado:** primeiros leads pós-filtro Make.
- [ ] **Acompanhar fluxo Dúvida WhatsApp pré-checkout:** primeiro lead real.

### Backlog médio prazo

- [ ] **Análise de gravações Clarity** em 4 categorias (já tem diretrizes prontas)
- [ ] **Frente 5:** escolher 1 intervenção da LP, atacar
- [ ] **HTTP Module no Make** pra cobrir subscribers existentes do carrinho abandonado
- [ ] **Refinar tag duplicada** "Clicou link" no Manychat
- [ ] **Tagueamento de cliques no WhatsApp via GTM**

### Backlog longo prazo (após estabilização Fase 1)

- [ ] **Frente 7 — Captação ampliada via isca digital** (decisão de prioridade pendente)
- [ ] Inlead/quiz como mudança estrutural de funil (encaixa com Frente 7)
- [ ] Conteúdo orgânico pra alimentar seed Visitantes LP
- [ ] Próxima rodada de otimização técnica LP — auditoria mensal

---

## 🧠 6. APRENDIZADOS QUE NÃO PODEM SE PERDER

### Tráfego pago

1. **3 ajustes técnicos pequenos transformaram a Fase 1** (pausa Camp 03 + botões unificados + imagens otimizadas). ROAS +144%, CPA -55%.
2. **NÃO aumentar verba em campanha existente.** Histórico de 9 meses confirma desestabilização. Discussão em 09/05 abriu espaço pra testar a regra com setup atual, mas SOMENTE após Camp_05 fechar janela (pós 16/05).
3. **Atribuição via WhatsApp pós-anúncio funciona.** Confiar nas vendas marcadas pelo gerenciador.
4. **Vendas com `src=(none)` que o Meta atribui contam como Meta.** Validado com Lisandra Campos em 08/05.
5. **CTR alto + 0 vendas = LP, não criativo.** Vídeo 4 com CTR 1,32% e 0 vendas confirmou esgotamento.
6. **Inflar prova social é veneno.** "2.000 obstetras" mentira → "350 obstetras" verdade.
7. **Materiais queimados não recuperam com mudança de ângulo.** Refilmagem com material novo é a única solução.
8. **Vídeo 4 está oficialmente morto. Vídeo 15 é o novo hero. Vídeo 14 tem ROAS agregado 5,73x em micro-volume.**
9. **Algoritmo do Meta esmaga diversidade de criativos.** Pra testar criativos secundários, isolamento em campanha dedicada é a única alternativa.
10. **Em estrutura 1-1-1, CBO e ABO são funcionalmente equivalentes.** Escolha vira critério de consistência com baseline.
11. **Critérios convergentes encurtam régua.** Camp_04: 4 sinais negativos justificaram pausar 4 dias antes do prazo oficial.
12. **Algoritmo "desistindo" do público se manifesta em queda progressiva de entrega.** Camp_04: gasto caiu R$93 → R$47 → R$37 → R$7 antes da pausa. Sinal previsível.
13. **Exploração proativa de público é diferente de aumento de verba.** Pode ser feita sem contaminar testes em curso, desde que o público não sobreponha audience já em uso.

### Landing Page

14. **Botões CTA tinham bug crítico** (84% de cliques mortos). Diagnóstico via Clarity heatmap. Correção foi de maior impacto.
15. **LP em deterioração silenciosa** (84 → 73 em 1 mês). Auditoria mensal é necessária.
16. **PageSpeed Insights tem oscilação alta.** Sempre validar com GTmetrix antes de decisões.
17. **TODOS os botões CTA levam ao formulário de pré-checkout.** Logo, "Enviar formulário" no Clarity ≈ Initiate Checkout do Meta.
18. **Conversion rate LP→Compra bruta: 4,55%; qualificada: ~7% mobile.** Excepcional pra info-product B2B. Daqui em diante, métrica de saúde da LP é a qualificada.

### Análise / Métricas — sessões curtas

19. **35,4% das sessões mobile são ≤5s e zero têm clique.** 33% tela cinza, 67% página carregada sem interação. Nunca poderiam gerar venda — só inflam denominador.
20. **Ruído estrutural é uniforme entre audiences (35-40%).** Não é problema de targeting, é estrutural do canal Instagram. Trocar audience não resolve.
21. **Hook nos primeiros 0,5-1s do vídeo é a alavanca real** pra reduzir o ruído (decide se rola ou clica conscientemente).
22. **Volume de IC ≠ volume de venda imediata.** Atribuição diária é ruidosa. Acumulado de 4-7 dias é mais representativo.
23. **Dia parcial não é dia completo.** Sempre comparar dia completo com dia completo.
24. **Order Bump como sinal de saúde.** Quando começa a converter, indica público mais qualificado.
25. **Sexta à tarde/noite em B2B (médicas) tipicamente cai.** Fim do expediente, atenção dispersa pro fim de semana. Camp_02 0 IC em 08/05 (sexta) provavelmente é isso, não fadiga. Confirmar com segunda 12/05.

### Manychat / Carrinho abandonado / Dúvida WhatsApp

26. **Integração nativa Manychat-Hotmart NÃO suporta `PURCHASE_OUT_OF_SHOPPING_CART`.** Solução é Make como ponte.
27. **Subscribers existentes dão erro 400 no Create.** Resume handler resolve MVP.
28. **Subscribers importados via CSV NÃO disparam fluxo automatizado.** Limitação Manychat (anti-spam).
29. **Plano C (Default Reply) sozinho NÃO interrompe fluxo.** Precisa Condições nos 4 pontos do fluxo pra interceptar.
30. **Padrão Manychat:** estilo positivo + OR + setas vermelhas. NUNCA misturar `Tag está` com `Tag não é` na mesma Condição.
31. **Webhooks Hotmart podem vir sem campo phone** (alguns checkouts deixam o campo opcional ou lead abandona antes de preencher). Sem filtro, cenário Make desativa por erros consecutivos. **Solução:** filtro `phone exists AND phone > 999999999` entre webhook e primeiro módulo Manychat.
32. **Make desativa cenário automaticamente após muitos erros consecutivos.** Foi a causa real dos 2 dias parados em 09-10/05 (sábado e domingo). Filtros que previnem erros são prevenção de downtime, não só de bugs.
33. **Resume handler do Make NÃO cobre `BundleValidationError`.** Resume só pega erros DEPOIS do request à API. BundleValidationError é validação LOCAL do Make antes do request — não passa pelo Resume.
34. **Fluxos paralelos com tags exclusivas valem manutenção em dois lugares quando mensurabilidade é objetivo.** Decisão tomada em 11/05 pro fluxo Dúvida vs Carrinho.
35. **Trigger keyword é frágil se depende de texto pré-preenchido editável.** Lead pode editar o texto antes de enviar — fluxo não dispara, cai no Default Reply. Aceitável quando atendimento manual cobre os casos excepcionais.
36. **Pra leads engajados em conversa real, ofertas automatizadas podem prejudicar.** Condição #2 do fluxo Dúvida intercepta amostra automatizada quando Plano C marcou Respondeu Ao Vivo — Felipe assume pessoalmente.

---

## 📁 7. ARQUIVOS DO VAULT — REFERÊNCIA

Localização: `01 - Projetos/Conexão Gestantes/` no vault Obsidian de Felipe (estrutura PARA + Johnny Decimal).

**Master/Hub:**
- `Conexão Gestantes - Hub.md`
- `Continuidade-Proxima-Conversa.md` ← **este arquivo (versão 12/05 manhã)**

**Tráfego:**
- `Fase1-Retomada AbrilMaio 2026.md` — projeto principal
- `Analise - 12dias Fase1.md` — dados consolidados (atualizar pra 19-20 dias)

**Criativo:**
- `Criativos - Estrutura Fase 1.md` — estrutura atual
- `Criativos - Vídeo 10 (referência).md` — formato de referência
- `Copy - Diretrizes.md` — regras de copy

**LP:**
- `Landing Page - Status e pendências.md` — pendências estruturais
- `Playbook - Otimizacão LP Hotmart.md` — recurso reutilizável

**Manychat:**
- `Manychat - Carrinho Abandonado.md` — implementação completa documentada
- `WhatsApp - Fluxo de mensagens.md` — copy do fluxo Vitória (parcialmente desatualizada — em revisão)
- **Considerar criar: `Manychat - Dúvida WhatsApp pré-checkout.md`** (documentação do novo fluxo deploy 11/05)

**Outros:**
- `Integração Manychat + Hotmart.md` — referência técnica
- `Prototipo - App Gestantes.md` — projeto futuro

---

## 🚦 8. CONTEXTO PRA RETOMAR RÁPIDO

**Quando a próxima conversa abrir, Felipe provavelmente vai:**

1. **Pedir análise de tráfego** — está focado em otimizar campanhas
2. **Trazer dados novos do Meta + Hotmart** (até checkpoint 16/05)
3. **Trazer prints da Camp_05** pra validar entrega
4. **Reportar primeiros leads do Manychat** (carrinho ou dúvida) e se converteram
5. **Discutir próxima frente prioritária** (Frente 1 produção criativo? Frente 6 exploração de público? Frente 7 isca digital?)

**Tom de comunicação esperado:**
- Direto, action-oriented, sem over-explanation
- Felipe corrige mischaracterizations precisamente — escutar e ajustar uma vez, sem pendular
- Prefere interactive HTML widgets pra planos multi-step, prosa direta pro resto
- Trabalha com PARA + Johnny Decimal no Obsidian
- Implementa tudo sozinho — Claude orienta passo a passo
- Valoriza clareza nas análises: validar dado antes de propor narrativa, não inflar com descobertas inventadas

**O que NÃO fazer:**
- Não responder com formato genérico de relatório
- Não inventar números que não estão no contexto
- Não ignorar ou minimizar correções dele
- Não sugerir aumentar verba em campanha existente sem reconhecer o histórico
- Não tratar Vídeo 4 como recuperável
- **Não apresentar como "descoberta" algo que já está no vault ou nas memórias**
- **Não pendular entre extremos quando recalibrar — recalibrar uma vez com o quadro completo**

---

## ⚠️ 9. LEMBRETES OPERACIONAIS

1. **Antes de qualquer ação no fluxo Manychat:** confirmar que os atrasos estão revertidos pros valores de produção. **Atenção: M1→M2 do carrinho é 8h, não 23h** (mudança de 08/05). Avaliar resultado em 14 dias (~22/05).

2. **Camp_04 confirmada pausada em 09/05 cedo.** Justificativa: 4 sinais convergentes (0 vendas + 2 IC + mediana Clarity 10s + queda progressiva de entrega). Investimento total: R$180/dia (Camp_01 + Camp_02 + Camp_05).

3. **Camp_05 checkpoints:** 12/05 (sinal inicial — HOJE) + 16/05 (decisão final). Régua oficial: verde/amarelo/vermelho. Subentrega <R$100 em 3 dias = pause antecipado.

4. **Vídeo 14 nunca foi 18x.** ROAS agregado real é 5,73x em micro-volume. Camp_05 é o primeiro teste com volume controlado pra ver se sustenta.

5. **Frente 1 (sucessores do Vídeo 15) tem janela fechando.** Vídeo 15 já está em ~5 semanas dominante. Não atrasar.

6. **Order Bump (R$83,91):** começou a aparecer no Período B (3 vendas). Sinal de público mais qualificado. Manter ativo, monitorar.

7. **Manychat — dois fluxos em paralelo:** Carrinho Abandonado (deploy 07/05, ativo com filtro corretivo) + Dúvida WhatsApp pré-checkout (deploy 11/05, ativo, aguardando primeiro lead real).

8. **Make do Carrinho tem filtro de phone obrigatório.** Não remover. Foi adicionado em 11/05 pra prevenir desativação automática do cenário por erros consecutivos.

9. **Sexta à tarde em B2B cai.** Não tirar conclusões de Camp_02 (ou qualquer campanha) baseado só em dados de sexta/sábado/domingo. Comparar dia útil com dia útil.

10. **Teste de aumento de verba em campanha existente:** SOMENTE após 16/05 (pós-checkpoint final Camp_05). Antes disso contamina leitura.

---

**FIM DO DOSSIÊ.** Versão 12/05/2026 manhã. Próxima atualização sugerida: após checkpoint final Camp_05 em 16/05.
