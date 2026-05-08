---
tags: [conexao-gestantes, continuidade, proxima-conversa]
data: 2026-05-08
status: ativo
---

# Conexão Gestantes — Continuidade pra Próxima Conversa

> Versão 08/05/2026 — substitui a de 05/05/2026.
> Sessão 07-08/05 cobriu: Manychat carrinho abandonado completo, análise tráfego dias 13-14, hipótese das sessões curtas no Clarity.

## Estado atual em uma linha

Fase 1 com ROAS 4,08x (5,95x sem Camp 04 em aprendizado), Manychat carrinho abandonado em produção aguardando primeiro lead real, próxima checagem 12/05 com decisão Camp 04.

## O que estávamos fazendo quando paramos

Análise da LP via Clarity após implementar Manychat carrinho abandonado. Felipe identificou volume alto de sessões com menos de 5 segundos e levantou hipótese: o tráfego nominal não é igual ao tráfego qualificado.

### Onde paramos exatamente

- Manychat carrinho abandonado completo (ver nota dedicada)
- Análise comparativa Pré vs Pós otimizações da LP feita
- Heatmap de scroll analisado — linha de morte na 1ª seção descritiva pós-hero
- Diretrizes de análise de gravações entregues
- Felipe parou em: descobriu volume alto de sessões menores que 5s, vai analisar offline

### Próximo passo técnico imediato

Quantificar as sessões curtas:

1. No CSV do Clarity (organizado por duração), contar:
   - Total de sessões no período
   - Quantas com 5 segundos ou menos
   - Quantas entre 5-30 segundos
   - Quantas com mais de 30 segundos
2. Olhar 3-5 gravações de 1-3s pra entender se são bots, cliques acidentais, ou outro tipo
3. Recalcular conversão excluindo sessões curtas — vai mostrar a conversão da LP qualificada
4. Se hipótese se confirmar (30%+ são curtas), o problema é qualificação upstream (criativo, audience), não LP

## Frentes pendentes em ordem de prioridade

### Alta — fazer já

1. Análise das sessões curtas no Clarity (Felipe vai fazer offline)
2. Aguardar primeiro lead real no Manychat carrinho abandonado pra validar end-to-end
3. Reverter atrasos do fluxo Manychat se ainda estiver em modo teste

### Média — semana que vem

4. Checkpoint dia 12/05 — decisão sobre Camp 04 conforme régua:
   - Verde: ROAS maior ou igual a 3x, CPA menor ou igual R$80, CTR maior ou igual 1% — manter/escalar
   - Amarelo: ROAS entre 2-3x, CPA R$80-120 — mais 7 dias
   - Vermelho: ROAS menor que 2x, ou CPA maior que R$120, ou 0 vendas em 7 dias — pausar
5. Análise de gravações Clarity (8-12 sessões em 4 categorias) — diretrizes prontas
6. Pendências estruturais da LP (social proof strip, price anchor, urgência) — escolher 1-2 pra atacar

### Baixa — após estabilização

7. HTTP Module no Make pra cobrir subscribers existentes do carrinho abandonado
8. Refinar tag duplicada Clicou link no Manychat (aplica 2x)
9. Tagueamento de cliques no WhatsApp via GTM
10. Considerar campanha dedicada Vídeo 14 (ROAS 18x latente)
11. LL3% Compradores como próxima escalada de público
12. Inlead/quiz como mudança estrutural de funil
13. Conteúdo orgânico pra alimentar seed Visitantes LP
14. Próxima rodada de otimização técnica LP — auditoria mensal

## Aprendizados que NÃO podem se perder

### Da sessão 06/05 e anteriores

1. 3 ajustes técnicos transformaram a Fase 1 (pausa Camp 03 + botões unificados + imagens otimizadas). ROAS +144%, CPA -55%.
2. Botões CTA da LP tinham bug crítico: 80 dos 96 cliques (84%) não funcionavam. Diagnóstico via Clarity heatmap.
3. LP em deterioração silenciosa. Performance 84 caiu pra 73 em 1 mês. Auditoria mensal necessária.
4. PageSpeed Insights tem oscilação alta. Sempre validar com GTmetrix.
5. Vídeo 4 está oficialmente morto. Vídeo 15 é o novo hero.
6. Vídeo 14 é underdog promissor. ROAS 18x latente em volume baixo.
7. Atribuição via WhatsApp pós-anúncio funciona. Meta atribui pela janela de clique. Confiar nas vendas marcadas pelo gerenciador.
8. NÃO aumentar verba em campanha existente. Solução: campanhas novas.

### Da sessão 07-08/05 (esta)

9. Manychat carrinho abandonado: integração nativa NÃO suporta PURCHASE_OUT_OF_SHOPPING_CART. Solução é Make como ponte.
10. Subscribers existentes na base do Manychat dão erro 400 no Create. Solução MVP: Resume handler. Solução robusta: HTTP Module com Custom Field phone_lookup.
11. Subscribers importados via CSV NÃO disparam fluxo automatizado mesmo com tag aplicada. Manychat tem proteção contra spam. Solução: tratar manualmente.
12. TODOS os botões CTA da LP levam pro formulário de pré-checkout. "Enviar formulário" no Clarity é igual a Initiate Checkout do Meta.
13. Funil correto da LP CG: LP visit, Click CTA, Form pré-checkout, Hotmart, Compra.
14. Linha de morte no heatmap está na 1ª seção descritiva pós-hero. ~50% saem ali. Quem clica converte excelente.
15. 88,86% dos visitantes saem antes de clicar em qualquer CTA. Mas boa parte pode ser ruído (sessões curtas).
16. Otimizações da LP de 30/04-01/05 sustentaram efeito por 7+ dias. LP-IC subiu de 2,64% pra ~10%.
17. Conversion rate LP-Compra: 4,55%. Excepcional pra info-product B2B (padrão típico 1-3%).
18. Padrão Manychat: estilo positivo + OR + setas vermelhas = consistência. NUNCA misturar Tag está com Tag não é na mesma Condição.
19. Plano C (Default Reply) sozinho NÃO interrompe fluxo automatizado. Só aplica tag. Pra interromper, precisa Condições nos 4 pontos do fluxo.
20. Lead Frio do fluxo carrinho usa tag específica (CG Lead Frio - Carrinho), separada da genérica CG Lead Frio.

## Performance consolidada (23/04 - 07/05, 14 dias)

| Período | Dias | Gasto | Vendas | Receita | ROAS |
|---|---|---|---|---|---|
| A: 23-30/04 | 7 | R$969,18 | 9 | R$2.376,99 | 2,45x |
| B: 01-04/05 | 4 | R$483,92 | 10 | R$2.892,83 | 5,98x |
| C: 05-07/05 | 3 | R$538,03 | 8+OB | R$2.196,79 | 4,08x |
| Total | 14 | R$1.991,13 | 27+OB | R$7.466,61 | 3,75x |

ROAS Período C excluindo Camp 04: 5,95x (consistente com Período B)

### Por campanha (Período C, 05-07/05)

- Camp 01 LL1% Compradores: R$186,68, 4 vendas, ROAS 5,66x
- Camp 02 Aberto BR 25-55: R$182,72, 4 vendas, ROAS 5,78x
- Camp 04 LL1% ViewContent 90D: R$168,63, 0 vendas, ROAS 0x (em aprendizado)

### Comparativo Pré vs Pós otimizações da LP

| Métrica | Pré (23-27/04) | Pós B (01-04/05) | Pós C (05-07/05) |
|---|---|---|---|
| Sessões/dia | ~53 | ~54 | ~58 |
| LP-IC | 2,64% | 11,68% | 9,20% |
| LP-Venda | ~2,8% | 4,67% | 4,60% |
| Dead clicks | 4-9% | 0% | 0% |
| Forms enviados/dia | 1-3 | 6-10 | 5-6 |

Conclusão: otimizações sustentaram efeito por 7+ dias. Não foi pico isolado.

## Configuração ativa atual

3 campanhas rodando:
- Camp 01 LL1% Compradores: R$60/dia
- Camp 02 Aberto: R$60/dia
- Camp 04 LL1% ViewContent 90D: R$60/dia (decisão 12/05)

Investimento total: R$180/dia

4 anúncios em cada: Vídeos 13, 14, 15 + Estático 17. Algoritmo distribui 80%+ pro Vídeo 15.

Manychat:
- Fluxo Carrinho Abandonado LIVE (aguardando primeiro lead real)
- Webhook nativo Hotmart pra Compra Aprovada ativo (aplica Membro CG)
- Default Reply trigger global ativo (Plano C)
- Cenário Make CG Carrinho Abandonado ativo com Resume handler

## Pra próxima conversa — checklist do que levar

### Documentos do vault atualizados
- Manychat - Carrinho Abandonado.md
- Continuidade-Proxima-Conversa.md (esta nota)

### Arquivos a subir na próxima conversa
- CSV do Clarity organizado por duração de sessão
- Relatório Meta dos próximos dias até checkpoint 12/05
- Relatório Hotmart até 12/05
- Prints Clarity dos próximos dias se houver mudança significativa

### Contexto pra retomar rápido
- Estamos no dia 14 da Fase 1
- Próximo checkpoint oficial: 12/05 (decisão Camp 04)
- Hipótese aberta: sessões curtas inflam denominador
- Manychat aguardando primeiro lead real
- 27 leads históricos tratados manualmente

## Hipóteses abertas

1. Sessões com menos de 5s representam ruído significativo — se confirmado, taxa real é maior que 4,55% e foco deve ser qualificação upstream
2. Camp 02 Aberto pode estar esgotando (CTR caiu de 1,93% pra 1,40% em 04/05, estabilizou em 1,49%)
3. Camp 04 LL1% ViewContent 90D pode não converter como Camp 01

## Lembrete operacional

Antes de qualquer ação no fluxo Manychat: confirmar que os atrasos estão revertidos pros valores de produção (23h, 1h) e não nos valores de teste (30s).
