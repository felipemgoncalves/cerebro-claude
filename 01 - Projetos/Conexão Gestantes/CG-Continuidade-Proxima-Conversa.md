---
tags: [conexao-gestantes, continuidade, proxima-conversa, top-of-mind]
data: 2026-05-05
status: ativo
---

# Conexão Gestantes — Continuidade pra Próxima Conversa

## Estado atual em uma linha

Fase 1 da retomada está em **5,98x ROAS** após otimizações, Camp 04 acabou de ser ativada (05/05), próxima checagem oficial **12/05**.

## O que estávamos fazendo quando paramos

**Implementando solução Manychat carrinho abandonado via Make.**

### Onde paramos exatamente

- ✅ Investigação completa: confirmamos que integração nativa Manychat-Hotmart NÃO cria subscriber pra evento de carrinho abandonado
- ✅ API Key do Manychat já obtida
- ✅ Cenário Make criado
- ✅ Módulo Webhook (Custom webhook) adicionado
- ✅ Webhook capturou primeira execução de teste (apareceu "1" no módulo)
- ⏸ Felipe travou em: **não conseguiu visualizar os dados capturados** clicando no número 1

### Próximo passo técnico imediato

Felipe precisa ver a estrutura do JSON capturado pelo webhook. Caminhos sugeridos:
1. Botão direito no módulo → "Show interface" ou balão branco
2. Aba "History" (canto inferior esquerdo) → clica execução mais recente
3. Forçar nova execução: botão direito → "Run this module only" → faz outro teste

Quando conseguir ver, manda screenshot da estrutura pra continuar com:
- Adicionar módulos HTTP no Make pra criar subscriber via API Manychat
- Adicionar módulo HTTP pra adicionar tag
- Configurar webhook na Hotmart pra apontar pra URL do Make
- Ajustar trigger do fluxo no Manychat pra ser por TAG
- Teste end-to-end
- Pausar webhook nativo Manychat-Hotmart

## Frentes pendentes em ordem de prioridade

### Alta — fazer já

1. **Concluir implementação Manychat via Make** (em andamento, travado em visualização do JSON)
2. **Criar Mensagem 2 do fluxo WhatsApp** (cobrança/follow-up, +24h após mensagem 1)
3. **Monitorar Camp 04 sem mexer** até 12/05

### Média — semana que vem

4. **Avaliar Camp 04 no dia 12/05** (régua: ROAS ≥3x, CPA ≤R$80, CTR ≥1%)
5. **Confirmar tendência de esgotamento Camp 02 Aberto** (CTR caiu de 1,93% pra 1,40% entre 03 e 04/05)
6. **Documentar SOP** do processo de carrinho abandonado completo

### Baixa — após estabilização

7. **Próxima rodada de otimização LP** — atacar scroll depth (~37% atual). Reorganizar arquitetura.
8. **Tagueamento de cliques no WhatsApp via GTM**
9. **Considerar campanha dedicada Vídeo 14** (ROAS 18x latente)
10. **LL3% Compradores** como próxima escalada de público
11. **Inlead/quiz** como mudança estrutural de funil
12. **Conteúdo orgânico** pra alimentar seed Visitantes LP
13. **Melhorar visualmente "O Nascimento de uma Mãe"** pra usar em criativos

## Aprendizados que NÃO podem se perder

1. **3 ajustes técnicos pequenos transformaram a Fase 1** (pausa Camp 03 + botões unificados + imagens otimizadas). Aumento de ROAS de 144%, queda de CPA de 55%, sem mexer em criativo nem público.

2. **Botões CTA da LP tinham bug crítico:** 80 dos 96 cliques (84%) não funcionavam. Diagnóstico via Clarity heatmap. Correção foi de maior impacto.

3. **LP estava em deterioração silenciosa.** Performance 84 → 73 em 1 mês sem ninguém adicionar imagens conscientes. Causa: scripts acumulados + cache Hotmart Pages + imagens com dimensões erradas.

4. **PageSpeed Insights tem oscilação alta.** Sempre validar com GTmetrix antes de decisões.

5. **Camp 03 (teste isolado V4) custou ROAS 3,0x → 2,45x**, mas validou definitivamente fadiga do criativo histórico.

6. **Vídeo 4 está oficialmente morto.** Não recuperar.

7. **Vídeo 15 é o novo hero.** Replica fórmula do Vídeo 4 antigo (mesa madeira, POV).

8. **Vídeo 14 é underdog promissor.** ROAS 18x latente em volume baixo.

9. **Atribuição via WhatsApp pós-anúncio funciona.** Pessoas vêm do anúncio, perguntam no WhatsApp, fecham via link enviado. Meta atribui pela janela de clique.

10. **Order Bump começou a aparecer.** R$251,73 em 4 dias. Pode ser sinal de público mais qualificado.

11. **NÃO aumentar verba em campanha existente.** Padrão histórico de 9 meses confirma que desestabiliza. Solução: criar conjuntos/campanhas novas.

12. **Manter consistência em "Vitória"** como identidade WhatsApp em todas as mensagens.

## Configuração ativa atual

**3 campanhas rodando:**
- Camp 01 LL1% Compradores: R$60/dia
- Camp 02 Aberto: R$60/dia (monitorar esgotamento)
- Camp 04 LL1% ViewContent 90D: R$60/dia (recém-ativada 05/05)

**Investimento total:** R$180/dia

**4 anúncios em cada:** Vídeos 13, 14, 15 + Estático 17. Algoritmo distribuiu praticamente tudo pro Vídeo 15.

## Régua de decisão Camp 04 (12/05)

- **Verde (manter/escalar):** ROAS ≥ 3x, CPA ≤ R$80, CTR ≥ 1%
- **Amarelo (mais 7 dias):** ROAS 2-3x, CPA R$80-120
- **Vermelho (pausar):** ROAS < 2x ou CPA > R$120 ou 0 vendas em 7 dias

## Links pra outras notas relacionadas

- [[CG-Fase1-Retomada-AbrilMaio2026]] — projeto principal
- [[CG-Manychat-Carrinho-Abandonado]] — em andamento (técnico)
- [[CG-Fluxo-WhatsApp]] — mensagens e estratégia
- [[CG-Analise-12dias-Fase1]] — dados consolidados
- [[CG-Estrutura-Criativos-Fase1]] — referência criativos
- [[CG-Playbook-Otimizacao-LP-Hotmart]] — recurso reutilizável
