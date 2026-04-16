---
tags: [ferramenta, manychat, whatsapp, automacao]
criado: 2026-04-16
---

# 💬 Manychat

## O que é
Plataforma de **automação conversacional** — WhatsApp, Instagram DM, Messenger.

## Uso no Conexão Gestantes

- Captura de leads no WhatsApp antes do checkout
- Flow de pré-venda
- Recuperação de carrinho abandonado (com limitação)

## Limitação crítica mapeada

> [!warning] Só funciona para contatos já no Manychat
> Para WhatsApp enviar uma mensagem, o contato **precisa ter interagido** antes. Leads que vão direto para o [[Hotmart]] sem passar pelo WhatsApp **não** podem ser recuperados por essa via.
>
> Implicação: o funil precisa **forçar passagem pelo WhatsApp** antes do checkout, ou pelo menos capturar o contato antes.
>
> Ver [[Integração Manychat + Hotmart]].

## Fluxos principais

### Pré-checkout
Captura contato → pergunta qualificatória → envia link personalizado Hotmart

### Recuperação de carrinho
Webhook Hotmart → Manychat dispara sequência de recuperação (1 imediata, 1 em 24h, 1 em 72h)

## Boas práticas
- **Não enviar em massa** sem opt-in → WhatsApp bloqueia
- **Mensagem curta** (WhatsApp é íntimo)
- **Link clicável** sempre
- **Humano de plantão** para conversas que escalam

## Relacionado
- [[Integração Manychat + Hotmart]]
- [[Hotmart]]
- [[Conexão Gestantes - Hub]]
