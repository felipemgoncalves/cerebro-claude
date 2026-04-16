---
tags: [ferramenta, hotmart, checkout, infoproduto]
criado: 2026-04-16
---

# 💰 Hotmart

## O que é
Plataforma brasileira de **infoprodutos** — hospedagem, checkout, afiliados, área do aluno.

## Uso no Conexão Gestantes

- Checkout de venda do produto (R$297 ticket)
- Gestão de compradores (~350 clientes ativos)
- Entrega do produto (materiais editáveis)
- Webhook de carrinho abandonado → [[Integração Manychat + Hotmart]]

## Pontos de atenção

### Pixel / Tracking
Garantir que:
- [ ] Pixel Meta configurado no checkout
- [ ] Evento **Purchase** disparado corretamente
- [ ] API de Conversões (CAPI) configurada para resiliência

### Abandono de carrinho
Webhook nativo do Hotmart → usado em [[Integração Manychat + Hotmart]].

### Afiliados (se aplicável)
Conferir termos e comissões antes de ativar.

## Limitações a lembrar
- UX do checkout não é totalmente customizável
- Relatórios nativos são básicos — complementar com dashboard próprio se precisar
- Taxa por transação (checar contrato atual)

## Relacionado
- [[Conexão Gestantes - Hub]]
- [[Integração Manychat + Hotmart]]
- [[Manychat]]
