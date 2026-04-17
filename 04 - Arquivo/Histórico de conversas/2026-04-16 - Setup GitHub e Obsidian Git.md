---
tags: [arquivo, historico, conversa]
data: 2026-04-16
projeto: Cérebro Claude (infraestrutura)
---

# 📜 2026-04-16 — Setup GitHub e Obsidian Git

## Contexto

Após criar o vault Obsidian, Felipe quis que o Claude pudesse acessar automaticamente as notas sem depender de copiar/colar. Solução escolhida: sincronizar vault com GitHub público via plugin Obsidian Git.

## Decisões tomadas

1. **Repo público** (não privado) — porque web_fetch do Claude não suporta headers de autenticação para repos privados
2. **Token sem expiração** — para não quebrar a sincronização periodicamente
3. **Auto-sync a cada 10 min** — equilíbrio entre frequência e performance
4. **Obsidian só no Mac principal** — edições centralizadas, sem conflito multi-máquina
5. **Dois gatilhos** para gerar neurônios: Felipe pede ("salva") ou Claude avisa proativamente

## Problemas resolvidos

| Problema | Causa | Solução |
|---|---|---|
| Git is not ready | Obsidian não herda PATH do Terminal | Custom Git binary path + Additional PATH |
| Can't find git repository | `.git` e `.obsidian` em pastas diferentes | Mover `.git` para dentro da pasta do vault |
| Authentication failed | GitHub não aceita senha pelo Terminal | Token embutido na URL do remote |
| Plugin sem campos de config | Git não inicializado na pasta do vault | Inicializar Git primeiro, depois configurar plugin |
| Vault duplicado no Obsidian | Obsidian abria pasta pai | Reabrir vault pela pasta correta |

## Aprendizado

Setup de Obsidian Git no Mac tem armadilhas de PATH e nível de pasta. Documentar em [[GitHub + Obsidian Git (setup)]] para referência futura.

## Relacionado
- [[GitHub + Obsidian Git (setup)]]
- [[Como usar este cofre]]
