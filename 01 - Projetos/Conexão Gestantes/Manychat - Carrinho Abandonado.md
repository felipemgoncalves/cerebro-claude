---
tags:
  - conexao-gestantes
  - manychat
  - whatsapp
  - automacao
  - make
  - hotmart
  - em-andamento
data: 2026-05-05
relacionado: "[[Fase1-Retomada AbrilMaio 2026]]"
status: implementacao-pendente
---

# Manychat — Carrinho Abandonado CG (Diagnóstico + Solução em andamento)

## Problema identificado

Automação de carrinho abandonado no Manychat **não envia mensagens**. Comportamento: aparece "Total: 9" no fluxo mas "Enviado: 0".

## Investigação (05/05/2026)

### Sintomas observados

- Compras aprovadas: automação funciona 100%
- Carrinho abandonado: automação cria registro mas nunca envia
- "Hora envia, hora não" em testes anteriores → padrão errático

### Hipóteses descartadas

1. ~~Subscriber WhatsApp inexistente~~ — Felipe confirmou que 100% dos compradores recebem mensagem mesmo sem interação prévia. Logo, Manychat consegue criar subscribers de zero.

2. ~~Janela de 24h do WhatsApp~~ — não se aplica porque compras funcionam.

3. ~~Webhook duplicado~~ — havia 2 webhooks com evento "Abandono de carrinho" ativos. Mesmo após remover duplicata, problema persistiu.

4. ~~Triplo disparo~~ — Hotmart dispara 3x todos eventos (incluindo compras aprovadas que funcionam). Não é causa.

### Causa raiz CONFIRMADA

**A integração nativa Manychat-Hotmart NÃO cria subscriber pra evento `PURCHASE_OUT_OF_SHOPPING_CART` (carrinho abandonado).**

Confirmação:
- Histórico do webhook na Hotmart mostra eventos disparados com sucesso
- Manychat responde 200 OK
- Mas: **ZERO contatos foram criados via webhook de carrinho abandonado nos últimos 7 dias**
- Compradores SIM são criados normalmente

A integração nativa foi desenhada apenas pra eventos de compra. Eventos de carrinho passam pelo webhook mas são ignorados silenciosamente pelo Manychat.

## Solução escolhida — Caminho A: Make criando subscriber explicitamente

### Arquitetura

```
Hotmart (carrinho abandonado)
   ↓ webhook
Make (cenário customizado)
   ↓ extrai dados
Make → Manychat API (cria subscriber)
   ↓
Make → Manychat API (adiciona tag "Carrinho Abandonado CG")
   ↓
Manychat (fluxo triggered pela tag)
   ↓
WhatsApp enviado ✅
```

### Pré-requisitos

- ✅ Conta Make (Felipe já tem, usada na Conectta Hub)
- ✅ Manychat Pro (Felipe confirmou)
- ✅ API Key do Manychat gerada e copiada

## Status da implementação

### Concluído
- [x] Investigação completa do problema
- [x] Confirmação da causa raiz
- [x] Pegar API Key do Manychat
- [x] Criar cenário no Make
- [x] Adicionar módulo Webhook (Custom webhook)
- [x] Gerar URL do webhook no Make
- [x] Webhook capturou primeira execução de teste (apareceu "1" no módulo)

### Pendente
- [ ] Visualizar dados capturados na execução de teste (precisa ver estrutura do JSON da Hotmart)
- [ ] Configurar webhook na Hotmart pra apontar pra URL do Make
- [ ] Adicionar módulo HTTP no Make pra criar subscriber via API Manychat
- [ ] Adicionar módulo HTTP no Make pra adicionar tag
- [ ] No Manychat: ajustar trigger do fluxo pra ser por TAG (não por webhook)
- [ ] Teste end-to-end com abandono real
- [ ] Pausar webhook nativo Manychat-Hotmart pra evitar duplicação

## Configuração técnica documentada

### Webhook nativo Manychat-Hotmart (atual)
- URL: `https://hooks.manychat.com/hotmartWebhook/process?p=TEpBajk5Q244MEhyRVdmakg1dWtUZz09fEpQMEJsTENPdmNaMjhQUWZoVk9laWc9PQ`
- Eventos atuais configurados: 
  - "Carrinho Abandonado CG - Manychat" → só Abandono de carrinho
  - "Compra Aprovada e Abandono de Carrinho - Manychat" → Compra aprovada (carrinho foi removido após investigação)

### Padrão de comportamento dos webhooks Hotmart
- Cada evento dispara **3x** automaticamente (retry/redundância da Hotmart)
- Comportamento normal e sistêmico, não é bug
- Manychat lida bem com isso pra eventos de compra

## API Manychat — referência rápida pra implementação

### Endpoint pra criar subscriber
```
POST https://api.manychat.com/fb/subscriber/createSubscriber
Header: Authorization: Bearer {API_KEY}
Body:
{
  "first_name": "...",
  "last_name": "...",
  "phone": "+5511999999999",
  "whatsapp_phone": "+5511999999999",
  "consent_phrase": "..."
}
```

### Endpoint pra adicionar tag
```
POST https://api.manychat.com/fb/subscriber/addTag
Header: Authorization: Bearer {API_KEY}
Body:
{
  "subscriber_id": "...",
  "tag_name": "Carrinho Abandonado CG"
}
```

## Mensagem inicial (já configurada no Manychat)

```
Oi [Primeiro Nome], tudo bem?

Sou a Vitória, do Conexão Gestantes 💚

Vi que você quase garantiu seu acesso ontem e quis te chamar pessoalmente. Algumas obstetras me procuram com dúvidas antes de fechar e gosto de estar por perto pra ajudar.

Me conta: você ficou com alguma dúvida sobre nossos materiais ou posso te ajudar de outra forma?
```

Vídeo anexado: `Materiais Conexão Gestantes.mp4`
Atraso: 5 minutos após captura, das 8h-21h
Identidade fixa: Vitória (manter consistência)

## Próximos passos pendentes na próxima conversa

1. Concluir implementação Make (módulos HTTP API Manychat)
2. Criar mensagem 2 (cobrança/follow-up — Felipe definiu intervalo de +24h como preferência teórica)
3. Documentar SOP do processo completo
4. Testar end-to-end e validar
