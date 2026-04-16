---
tags: [projeto/crm, apps-script, arquitetura, tecnico]
criado: 2026-04-16
atualizado: 2026-04-16
versao: v3
---

# ⚙️ Arquitetura Apps Script v3

## Histórico de versões

| Versão | Marco |
|---|---|
| v1 | Primeiro script funcional (import manual + envio) |
| v2 | Adição de histórico de interações |
| **v3** | **Atual:** detecção de bounces + dashboard HTML standalone |

## Estrutura de funções (esqueleto)

```javascript
// ===== CONFIG =====
const CONFIG = {
  sheetId: "...",
  contatosAba: "Contatos",
  bouncesAba: "Bounces",
  // ...
};

// ===== ENTRADAS =====
function onOpen() { /* menu customizado */ }
function importarContatos() { /* Apollo → Contatos */ }
function detectarBounces() { /* e-mails → aba Bounces */ }

// ===== HELPERS =====
function getSheet(name) { /* ... */ }
function logInteracao(contato, tipo, detalhes) { /* ... */ }

// ===== DASHBOARD =====
function doGet() { /* serve HTML webapp */ }
function getMetricas() { /* dados para dashboard */ }
```

## Triggers configurados

- **Tempo:** detecção de bounces roda a cada X minutos (configurável)
- **onOpen:** adiciona menu customizado na planilha
- **doGet:** endpoint do dashboard HTML

## Permissões necessárias

- Google Sheets (leitura/escrita)
- Gmail (leitura — para detectar bounces)
- Drive (se houver export/import)

## Pontos de atenção

> [!warning] Limites do Apps Script
> - **Execução:** 6 min por trigger (gratuito)
> - **URL fetch:** 20k por dia
> - **Gmail:** 100 leituras/dia no trigger gratuito
>
> Se volume crescer, migrar parte para [[Make (Integromat)|Make]].

## Manutenção

### Rotina mensal
- [ ] Exportar código `.gs` para Drive (backup)
- [ ] Checar logs de erro (Apps Script > Executions)
- [ ] Limpar linhas antigas da aba Bounces (>90 dias)

### Em caso de bug
1. Desligar triggers automáticos
2. Rodar função problemática manualmente no editor
3. Inspecionar logs (`console.log`)
4. Testar em planilha cópia antes de aplicar fix

## Relacionado
- [[CRM - Hub]]
- [[Bounces - Sistema de detecção]]
- [[Dashboard HTML]]
- [[Google Apps Script]]
