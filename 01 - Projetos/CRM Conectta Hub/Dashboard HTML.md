---
tags: [projeto/crm, dashboard, html, webapp]
criado: 2026-04-16
atualizado: 2026-04-16
---

# 📊 Dashboard HTML

## O que é

**Webapp standalone** servido pelo Google Apps Script (`doGet`), que exibe métricas operacionais do CRM em uma página HTML limpa.

Acessível por URL pública gerada pelo deploy do Apps Script.

## Métricas exibidas

- Contatos totais na base
- Contatos ativos (não bounceados)
- Interações recentes
- Taxa de bounce
- Pipeline por estágio (prospecção → resposta → reunião → proposta → fechamento)
- Métricas por marca-alvo

## Arquitetura

```
Browser
  ↓
GET <URL do webapp>
  ↓
Apps Script doGet() → HtmlService.createTemplateFromFile('Dashboard')
  ↓
Template HTML executa google.script.run.getMetricas() via <script>
  ↓
Apps Script getMetricas() → lê Sheets → retorna JSON
  ↓
Render de cards + tabelas no browser
```

## Stack

- HTML + CSS vanilla (ou framework leve)
- JS para chamadas `google.script.run`
- Possível uso de Chart.js para gráficos

## Segurança

> [!warning] Acesso
> Definir no deploy:
> - **Execute as:** Me (dono)
> - **Who has access:** Anyone / Anyone with link / Only me
>
> Para uso só interno: "Anyone with link" + link não público, **ou** configurar auth por domínio.

## Próximas evoluções

- [ ] Filtros interativos (por marca, por status, por período)
- [ ] Export CSV direto do dashboard
- [ ] Tema dark
- [ ] Versão mobile-friendly (flex/grid responsivo)

## Manutenção

- O HTML vive dentro do projeto Apps Script (arquivo `.html`)
- Ao atualizar: **republicar** o deploy para a versão nova ir ao ar
- Manter versão anterior como backup no próprio Apps Script

## Relacionado
- [[CRM - Hub]]
- [[Arquitetura Apps Script v3]]
