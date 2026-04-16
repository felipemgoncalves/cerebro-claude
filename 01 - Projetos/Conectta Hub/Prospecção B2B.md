---
tags: [projeto/conectta-hub, prospeccao, b2b, operacao]
criado: 2026-04-16
atualizado: 2026-04-16
---

# 🎯 Prospecção B2B

## Fluxo operacional

```
1. Identificar marca-alvo
       ↓
2. Buscar contatos no Apollo.io por domínio
       ↓
3. Validar e-mails no ZeroBounce
       ↓
4. Registrar contatos no CRM (Sheets + Apps Script)
       ↓
5. Enviar e-mails via domínio UOL
       ↓
6. Make detecta bounces → loga na aba "Bounces"
       ↓
7. Acompanhamento em Sheets / Dashboard
```

## Ferramentas

| Ferramenta | Função |
|---|---|
| [[Apollo.io]] | Descoberta de contatos por domínio |
| [[ZeroBounce]] | Validação de e-mail |
| [[Make (Integromat)]] | Automação de bounces |
| [[CRM - Hub]] | Gestão em Sheets com Apps Script v3 |
| UOL (hospedagem) | Envio a partir de domínio próprio |

## Playbooks de e-mail

### E-mail de prospecção (first touch)
- Assunto curto, personalizado por marca
- Menção a contexto específico da marca
- Oferta clara (não vender na primeira mensagem — propor conversa)
- CTA de calendário

### E-mail de reativação (marcas dormentes)
- Referência a histórico prévio
- Novidade genuína (ativo novo, caso novo, insight novo)
- Re-abertura de conversa

## Marcas ativas na prospecção / base

- [[Cliente - Bio-Oil]]
- [[Cliente - Natura]]
- [[Cliente - L'Oréal]]
- [[Cliente - Softys-Ontex]]
- [[Cliente - CIMED (playbook)]] (playbook de recuperação)

## Tratamento de bounces

Sistema dedicado — ver [[Bounces - Sistema de detecção]].

- Automação Make escuta e-mails do domínio UOL
- Identifica bounces e loga na aba **Bounces** do CRM Sheets
- Bounce recorrente → contato marcado como inválido
- Alternativas: buscar contato secundário da mesma marca no Apollo

## Métricas a acompanhar

| Métrica | Onde ver |
|---|---|
| Taxa de bounce | Aba Bounces + Dashboard HTML |
| Taxa de resposta | Manual no CRM |
| Taxa de agendamento | Manual no CRM |
| Taxa de fechamento | Manual no CRM |

## Próximos passos

- [ ] Consolidar métricas no [[Dashboard HTML]]
- [ ] Criar templates de e-mail versionados no vault
- [ ] Documentar critério de scoring de leads
- [ ] Reengajar CIMED (playbook pronto)

## Relacionado
- [[Conectta Hub - Hub]]
- [[CRM - Hub]]
- [[Comercial B2B]]
