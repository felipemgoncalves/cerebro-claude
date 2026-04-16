---
tags: [projeto/crm, bounces, email, automacao]
criado: 2026-04-16
atualizado: 2026-04-16
---

# 📤 Bounces — Sistema de detecção

## Objetivo

Detectar automaticamente **e-mails que voltam como inválidos** (bounce) ao enviar prospecção a partir do domínio UOL, e **logar** na aba `Bounces` do CRM.

## Arquitetura

```
E-mail enviado (domínio UOL)
       ↓
E-mail volta (bounce) → inbox
       ↓
Make escuta a inbox (ou Apps Script via Gmail API)
       ↓
Parse do payload → identifica endereço inválido
       ↓
Append row na aba "Bounces" do CRM Sheets
       ↓
Marca contato original como "email-invalido"
```

## Campos da aba Bounces

| Campo | Descrição |
|---|---|
| `data` | Timestamp do bounce |
| `email` | E-mail que retornou |
| `motivo` | Classificação (hard / soft / caixa cheia / não existe) |
| `assunto_original` | Assunto do e-mail que bateu bounce |
| `status` | "novo" / "processado" |

## Classificação

### Hard bounce (definitivo)
- Endereço não existe
- Domínio inválido
- → **Marcar contato como inválido**, não reenviar

### Soft bounce (temporário)
- Caixa cheia
- Servidor temporariamente indisponível
- → **Aguardar** e tentar novamente em X dias

### Outras razões
- Anti-spam agressivo
- Bloqueio corporativo
- → Buscar contato alternativo via [[Apollo.io]]

## Fluxo operacional

1. Prospecção enviada
2. Bounces aparecem na aba → notificação (se configurada)
3. Felipe / Debora revisam aba periodicamente
4. Contatos inválidos → **buscar novo contato** na mesma empresa (Apollo)
5. Atualizar contato no CRM

## Próximas evoluções

- [ ] Notificação automática por e-mail/Slack quando bounce acontece
- [ ] Regra automática: **3 hard bounces** numa empresa → flag para revisão do domínio
- [ ] Relatório semanal: taxa de bounce por campanha de prospecção

## Relacionado
- [[Arquitetura Apps Script v3]]
- [[Make (Integromat)]]
- [[ZeroBounce]]
- [[Prospecção B2B]]
