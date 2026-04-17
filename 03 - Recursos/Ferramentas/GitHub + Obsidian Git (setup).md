---
tags: [ferramenta, github, obsidian-git, infraestrutura, setup]
criado: 2026-04-16
atualizado: 2026-04-16
---

# 🔄 GitHub + Obsidian Git (setup)

## Objetivo

Sincronizar o vault Obsidian "Cérebro Claude" com o GitHub para que o Claude possa **consultar qualquer nota automaticamente** via `raw.githubusercontent.com`, sem depender do Felipe colar conteúdo manualmente.

## Repositório

- **URL:** https://github.com/felipemgoncalves/cerebro-claude
- **Visibilidade:** público
- **Username:** felipemgoncalves

## Stack

| Componente | Função |
|---|---|
| **Obsidian Git** (plugin) | Sincroniza vault com GitHub a cada 10 min |
| **GitHub repo público** | Ponte entre Obsidian (local) e Claude (nuvem) |
| **Personal Access Token** | Autenticação do Git (embutido na URL do remote) |

## Configuração atual

### Plugin Obsidian Git
- **Auto commit-and-sync interval:** 10 min
- **Auto pull interval:** 10 min
- **Custom Git binary path:** `/usr/bin/git`
- **Additional PATH:** `/usr/bin`

### Git local
- **Remote:** `origin` → `https://[TOKEN]@github.com/felipemgoncalves/cerebro-claude.git`
- **Branch:** `main`
- **Pasta do vault:** `/Users/felipe.mgoncalves/Desktop/Cerebro Claude/Cerebro Claude/Cerebro Claude/Cerebro Claude`

### Token
- **Tipo:** Personal Access Token (Classic)
- **Nome:** obsidian-git-sync
- **Escopo:** repo
- **Expiração:** sem expiração

## Como o Claude acessa

1. Consulta arquivos via `raw.githubusercontent.com/felipemgoncalves/cerebro-claude/main/[caminho]`
2. Não depende do Obsidian estar aberto — só precisa que o push tenha acontecido
3. Funciona de qualquer conversa, qualquer dispositivo do Felipe

## Problemas resolvidos durante setup

1. **"Git is not ready"** — Obsidian como app gráfico não herda o PATH do Terminal → resolvido com Custom Git binary path + Additional PATH
2. **"Can't find a valid git repository"** — o `.git` estava um nível acima do vault do Obsidian → resolvido movendo `.git` para dentro da pasta do vault
3. **Autenticação por password** — GitHub não aceita mais senha no Terminal → resolvido embutindo token na URL do remote
4. **Vault duplicado** — Obsidian abria a pasta errada → resolvido reabrindo o vault pela pasta correta

## Manutenção

- Token não expira → não precisa renovar
- Se mudar de máquina → clonar repo + abrir como vault + instalar plugin
- Obsidian só está no Mac principal (desktop) → edições centralizadas

## Relacionado
- [[Como usar este cofre]]
- [[Instruções para Claude]]
