---
tags: [ferramenta, make, integromat, automacao]
criado: 2026-04-16
---

# 🔄 Make (Integromat)

## O que é
Plataforma **no-code de automação**. Conecta apps via cenários visuais (nodes + conexões).

## Uso no Conectta Hub

### Automação de bounces (ativa)
Lê e-mails do domínio UOL, identifica bounces, loga na aba `Bounces` do [[CRM - Hub]].

### Possíveis usos futuros
- Integração [[Manychat]] ↔ [[Hotmart]] para recuperação de carrinho
- Sincronização Apollo → CRM direta
- Notificações (Slack/e-mail) em eventos do CRM

## Vantagens sobre Zapier

- Preço por **operação** mais barato para volumes médios
- Interface visual mais poderosa (branches, loops, iteradores)
- Suporte nativo a JSON / arrays

## Princípios de uso

> [!tip] Boas práticas
> 1. **Nomear cenários claramente** (ex.: "Bounces UOL → CRM")
> 2. **Error handlers** configurados (não deixar falhas silenciosas)
> 3. **Logs** em Sheets para auditoria
> 4. **Teste com poucos dados** antes de ligar em produção
> 5. **Duplicar** cenário antes de mexer em algo crítico

## Relacionado
- [[Bounces - Sistema de detecção]]
- [[Automação e Ferramentas]]
