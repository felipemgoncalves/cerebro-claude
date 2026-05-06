---
tags: [conexao-gestantes, whatsapp, mensagens, fluxo, vendas]
data: 2026-05-05
relacionado: "[[CG-Fase1-Retomada-AbrilMaio2026]]"
status: parcialmente-implementado
---

# Conexão Gestantes — Fluxo WhatsApp

## Identidade

**Nome usado:** Vitória (consistência total — não misturar com Felipe ou outros)
**Tom:** consultivo, não vendedor, próximo, profissional
**Emoji padrão:** 💚 (esporádico, sem exagero)
**Estilo:** primeira pessoa, direto, sem em-dashes

## Mensagens já criadas e aprovadas

### Mensagem 1 — Carrinho abandonado (primeira tentativa)

**Tempo:** 5 minutos após abandono, das 8h-21h
**Status:** texto aprovado e implementado no Manychat

```
Oi Dra. [nome], tudo bem?

Sou a Vitória, do Conexão Gestantes 💚

Vi que você quase garantiu seu acesso ontem e quis te chamar pessoalmente. Algumas obstetras me procuram com dúvidas antes de fechar e gosto de estar por perto pra ajudar.

Me conta: você ficou com alguma dúvida sobre nossos materiais ou posso te ajudar de outra forma?
```

**Mídia anexada antes do texto:** vídeo "Materiais Conexão Gestantes.mp4"

**Princípios aplicados na construção:**
- "Quase garantiu seu acesso" reposiciona como elogio, não cobrança
- "Quis te chamar pessoalmente" cria sensação de atendimento exclusivo
- "Algumas obstetras me procuram com dúvidas" normaliza o comportamento
- Pergunta dupla cobre tanto quem tem dúvida específica quanto quem hesitou por outros motivos

## Pendentes (próxima conversa)

### Mensagem 2 — Cobrança/follow-up

**Status:** não criada ainda
**Decisão preliminar:** intervalo de +24h após mensagem 1 (Felipe inclinou pra essa opção)
**Critério de envio:** se pessoa não respondeu mensagem 1 em 24h

**Princípios pra construção:**
- Mais leve que a primeira (não pode ser pressão)
- Curta (sem reapresentar o produto)
- Deixa porta aberta sem ser invasiva
- Pode ter pequeno gatilho de urgência genuína (não falsa)

### Sequência completa de objeções

Quando a pessoa **responder** com dúvidas, ter scripts prontos pra:
- "Achei caro" / "tá fora do meu orçamento"
- "Não sei se vou usar"
- "É físico ou digital?"
- "Posso editar mesmo? Não sei usar Canva"
- "É vitalício?"
- "Tem garantia?"
- "Vou pensar"

### Mensagem de pré-checkout (cliente respondeu, deu sinal de compra)

Quando a pessoa demonstra interesse de fechar, manda link direto e mensagem clara.

### Mensagem de boas-vindas pós-compra

Após pagamento aprovado, mensagem de:
- Confirmação calorosa
- Acesso rápido aos materiais
- Convite pra falar quando precisar

## Vendas via WhatsApp já confirmadas (validação do canal)

Casos reais onde o canal WhatsApp pós-anúncio fechou venda:

- **27/04 - Gutemberg Cayres** — veio do anúncio, fechou via WPP
- **27/04 - Flávia Palombo** — veio do anúncio, fechou via WPP

Padrão: pessoa clica no anúncio, vê a LP, vai pro WhatsApp pra perguntar antes de fechar. Felipe envia link de checkout, ela paga.

**Implicação estratégica:** o WhatsApp é canal de fechamento real, não só suporte. Vale investir em scripts e velocidade de resposta.

## Arquitetura técnica do fluxo (estado futuro)

```
ETAPA 1: Captura
- Pessoa abandona carrinho na Hotmart
- Webhook → Make → Manychat (fluxo via TAG)
- Mensagem 1 enviada após 5 min

ETAPA 2: Aguardar resposta (até 24h)
Se respondeu: vai pra ETAPA 3 (atendimento humano)
Se não respondeu em 24h: envia Mensagem 2 (cobrança)

ETAPA 3: Atendimento humano
- Felipe ou Vitória responde dúvidas
- Usa scripts prontos de objeções quando aplicável
- Conduz pra checkout se sinal de compra

ETAPA 4: Pós-compra (se aprovou)
- Mensagem de boas-vindas automática
- Tag "Cliente Ativo CG" aplicada

ETAPA 5: Pós-rejeição (se não comprou após follow-up)
- Tag "Lead Frio CG"
- Pode entrar em sequência futura de reengajamento
```

## Tagueamento de cliques no WhatsApp via GTM

**Status:** ainda pendente

Quando implementado, vai permitir medir:
- Quantos cliques no botão WhatsApp da LP
- Quantos desses chegam a iniciar conversa
- Quantos viram venda
- ROI real do canal WhatsApp

UTM sugerida no link wa.me da LP:
```
https://wa.me/55XXXXXXXXX?text=[mensagem]&utm_source=lp_conexaogestantes&utm_medium=whatsapp_floating&utm_campaign=duvidas_lp
```

GTM trigger: Click - Apenas links - Click URL contém wa.me
Tag: GA4 Event "whatsapp_click" + Custom Pixel Meta event "WhatsAppClick"
