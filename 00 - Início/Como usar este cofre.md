---
tags: [meta, guia]
criado: 2026-04-16
---

# 📖 Como usar este cofre

## Filosofia

Este vault é um **segundo cérebro colaborativo**: metade construído pelo Claude com base no histórico de conversas, metade construído por você ao longo do tempo. Ele não substitui a memória nativa do Claude — ele **amplia** e **persiste** o que importa.

## Estrutura (método PARA adaptado)

| Pasta | Para quê serve |
|---|---|
| **00 - Início** | Dashboard, índices, navegação |
| **01 - Projetos** | Iniciativas com começo, meio e fim (Conexão Gestantes, Conectta Hub, Summit, CRM) |
| **02 - Áreas** | Domínios permanentes de responsabilidade (tráfego pago, copy, comercial) |
| **03 - Recursos** | Ferramentas, templates, glossários, referências |
| **04 - Arquivo** | Projetos finalizados ou histórico de conversas |
| **05 - Meta** | Perfil, instruções para o Claude, log do cofre |

## Convenções

- **Wikilinks:** `[[Nome da nota]]` para conectar ideias
- **Tags:** `#projeto/conexao-gestantes`, `#area/trafego`, `#ferramenta/apollo`
- **Frontmatter YAML:** cada nota tem `tags`, `criado`, `atualizado`
- **Callouts:** `> [!note]`, `> [!warning]`, `> [!tip]` para destacar pontos
- **Emojis nos hubs** (🏠, 🎯, 🛠️) para escaneamento visual rápido

## Como usar com o Claude

Quando iniciar uma conversa nova, você pode:

1. **Colar o conteúdo** de uma nota relevante para dar contexto
2. **Pedir para atualizar** uma nota específica com base na conversa
3. **Pedir notas novas** ao final de uma conversa ("crie uma nota sobre X")
4. **Revisar o log** ([[Log de atualizações]]) para ver o que mudou

> [!tip] Dica prática
> No início de cada conversa importante, cole o conteúdo do [[Perfil - Felipe]] + o hub do projeto em questão. O Claude entra no contexto em segundos.

## Fluxos recomendados

### Fluxo "decisão estratégica"
1. Conversa com Claude → decisão tomada
2. Criar nota nova em `01 - Projetos/[projeto]/Decisão - [tema].md`
3. Usar [[Template - Decisão estratégica]]
4. Linkar do hub do projeto

### Fluxo "aprendizado novo"
1. Descobriu algo útil (ex.: Vídeo 10 performa melhor)
2. Nota atômica em `02 - Áreas/[área]/[aprendizado].md`
3. Referenciar projetos onde se aplica

### Fluxo "reset de contexto"
Quando o Claude "esquecer" algo → abra o hub relevante → copie → cole na conversa.

## Plugins Obsidian recomendados (opcional)

- **Dataview** — queries dinâmicas (listar todas as notas por tag)
- **Templater** — templates avançados com variáveis
- **Calendar** — visão de notas diárias
- **Excalidraw** — diagramas à mão livre

Nenhum é obrigatório. O vault funciona só com Obsidian padrão.
