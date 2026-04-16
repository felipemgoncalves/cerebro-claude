---
tags: [area, automacao, ferramentas]
criado: 2026-04-16
---

# ⚙️ Automação e Ferramentas

Área permanente. Princípios de automação + mapa das ferramentas no stack.

## Princípios de automação

### 1. Automatizar só o que já está funcionando manualmente
Automação não conserta processo quebrado — **amplifica** o que existe. Se manual dá resultado, automatizar vale.

### 2. Simples > elegante
Google Sheets + Apps Script resolve 80% dos casos. Não partir para SaaS caro antes de esgotar o simples.

### 3. Diagnóstico antes de produção
Usar **webhook.site** ou similar para **ver payloads reais** antes de escrever integração (abordagem usada em [[Integração Manychat + Hotmart]]).

### 4. Log tudo
Falha em automação é silenciosa. Sem log, você descobre que quebrou quando o cliente reclama. **Sempre** persistir log em Sheets/BD.

### 5. Fallback humano
Automação deve notificar quando algo sair do esperado. Humano no loop para edge cases.

## Stack atual

### Operação comercial B2B
- [[Apollo.io]] — descoberta de contatos
- [[ZeroBounce]] — validação de e-mail
- [[Make (Integromat)]] — automação de bounces
- [[Google Apps Script]] — CRM e dashboard
- UOL — envio de e-mail pelo domínio próprio

### Conexão Gestantes
- [[Manychat]] — conversacional no WhatsApp
- [[Hotmart]] — checkout e carrinho
- [[Meta Ads Manager]] — tráfego pago

### Infraestrutura
- Google Sheets — banco de dados operacional
- Google Drive — arquivos e assets

## Decisões arquiteturais

> [!note] Por que Sheets em vez de Airtable/Notion?
> - Apps Script é mais poderoso que scripts de Airtable/Notion
> - Zero custo
> - Integração nativa com Google ecosystem
> - Trade-off: UI menos bonita (mas resolvido via [[Dashboard HTML]])

> [!note] Por que Make e não Zapier?
> - Preço melhor por operação
> - Interface visual mais poderosa (branches, loops)
> - Suporte a cenários complexos

## Templates mentais

### Fluxo de integração nova
1. **O que preciso resolver?** (problema claro)
2. **Já resolve manual?** (se não, não automatize ainda)
3. **Qual o menor MVP?** (uma etapa, não o fluxo todo)
4. **Como logar?** (Sheets com timestamp)
5. **Como detectar falha?** (notificação)
6. **Como reverter?** (plano B se quebrar)

## Relacionado
- [[CRM - Hub]]
- [[Prospecção B2B]]
- [[Integração Manychat + Hotmart]]
