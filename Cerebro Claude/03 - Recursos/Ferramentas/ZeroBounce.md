---
tags: [ferramenta, zerobounce, email, validacao]
criado: 2026-04-16
---

# ✅ ZeroBounce

## O que é
Serviço de **validação de e-mail** — identifica endereços inválidos, descartáveis, armadilhas de spam, antes do envio.

## Uso no Conectta Hub

Após export do [[Apollo.io]]:
1. Upload da lista de e-mails no ZeroBounce
2. Processamento (alguns minutos)
3. Download com status por e-mail

## Status importantes

| Status | Ação |
|---|---|
| **Valid** | Usar (segurança alta) |
| **Catch-all** | Usar com cautela (pode aceitar qualquer coisa) |
| **Unknown** | Evitar (risco de bounce) |
| **Invalid** | Descartar |
| **Spam trap** | Descartar (perigoso — pode queimar domínio) |
| **Abuse** | Descartar |

## Por que é crítico

Enviar para lista não validada → **bounces altos** → **reputação do domínio cai** → e-mails legítimos vão para spam.

O [[Bounces - Sistema de detecção]] é a **rede de segurança** depois; o ZeroBounce é a **prevenção** antes.

## Relacionado
- [[Apollo.io]]
- [[Bounces - Sistema de detecção]]
- [[Prospecção B2B]]
