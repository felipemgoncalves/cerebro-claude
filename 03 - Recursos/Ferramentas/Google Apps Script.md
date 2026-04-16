---
tags: [ferramenta, google, apps-script, desenvolvimento]
criado: 2026-04-16
---

# 🧰 Google Apps Script

## O que é
Linguagem de script (JavaScript-based) para **automatizar Google Workspace** — Sheets, Gmail, Drive, Calendar.

## Uso no Conectta Hub

Base do [[CRM - Hub]]. Ver [[Arquitetura Apps Script v3]].

## Capacidades chave

- Ler/escrever em Sheets
- Ler Gmail (bounces, respostas)
- Enviar e-mail
- Servir **webapp HTML** (`doGet`) → [[Dashboard HTML]]
- Triggers por tempo ou evento
- Chamar APIs externas (UrlFetch)

## Limites importantes

| Recurso | Limite (plano gratuito) |
|---|---|
| Execução | 6 min por chamada |
| Triggers totais | 20 por script |
| E-mails enviados/dia | 100 (via script) |
| UrlFetch/dia | 20.000 |
| Gmail read | 100 chamadas/dia em trigger |

Workspace pago aumenta os limites.

## Boas práticas

1. **Modularizar** em funções pequenas
2. **Logar** com `console.log` ou persistir em Sheet
3. **try/catch** em pontos críticos
4. **Backup do código** exportado para Drive regularmente
5. **Versionar** deploys (Apps Script tem controle de versão de deploy)

## Pitfalls comuns

- Edit de script durante execução de trigger → race conditions
- Permissões reaparecem quando novos escopos são adicionados → revisar deploys
- Timezone default é do Google, não do usuário — setar explicitamente

## Relacionado
- [[CRM - Hub]]
- [[Arquitetura Apps Script v3]]
- [[Dashboard HTML]]
