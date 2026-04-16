---
tags: [projeto, hub, crm, conectta-hub]
projeto: CRM Conectta Hub
status: ativo-deployado
criado: 2026-04-16
atualizado: 2026-04-16
---

# 🗄️ CRM Conectta Hub — Hub

## O que é

CRM operacional construído em **Google Sheets + Google Apps Script v3**, para gestão da prospecção B2B do [[Conectta Hub - Hub]].

**Status:** deployado e em uso.

## Componentes

| Componente | Função | Status |
|---|---|---|
| **Planilha mestre** | Banco de contatos + histórico de interações | ✅ Ativo |
| **Apps Script v3** | Lógica de automação, scoring, integrações | ✅ Deployado |
| **Aba Bounces** | Log automático de e-mails inválidos | ✅ Ativo |
| **Dashboard HTML** | Webapp standalone para visualização | ✅ Deployado |
| **Make (integração)** | Captura de bounces do domínio UOL | ✅ Ativo |

## Por que Sheets + Apps Script (e não Hubspot/Pipedrive)?

- **Custo zero** de licença
- **Flexibilidade total** — cada fluxo customizado
- **Dados ficam com a gente** (sem lock-in)
- **Integração nativa** com outras planilhas e Drive
- Trade-off: exige manutenção própria do script

## Abas principais da planilha

1. **Contatos** — dados dos leads (Apollo.io)
2. **Empresas** — marcas-alvo
3. **Interações** — histórico (e-mails enviados, respostas, reuniões)
4. **Bounces** — e-mails inválidos detectados automaticamente
5. **Configuração** — parâmetros do script

## Notas filhas

- [[Arquitetura Apps Script v3]]
- [[Bounces - Sistema de detecção]]
- [[Dashboard HTML]]

## Backup e versionamento

> [!warning] Prática crítica
> Apps Script **não tem versionamento nativo robusto**. Antes de mudanças grandes:
> 1. **Duplicar a planilha** (backup)
> 2. **Exportar o código do script** para um arquivo `.gs` versionado em Drive ou Git
> 3. Testar em cópia antes de aplicar no ambiente de produção

## Próximas evoluções

- [ ] Integração direta com Apollo.io (API) em vez de import manual
- [ ] Scoring automático de leads baseado em engajamento
- [ ] Notificações por e-mail de respostas importantes
- [ ] Relatórios semanais automáticos via script

## Relacionado
- [[Prospecção B2B]]
- [[Conectta Hub - Hub]]
- [[Automação e Ferramentas]]
