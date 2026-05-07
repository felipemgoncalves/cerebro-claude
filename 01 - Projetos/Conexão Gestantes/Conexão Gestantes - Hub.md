---
tags: [projeto, hub, conexao-gestantes]
projeto: Conexão Gestantes
status: ativo
criado: 2026-04-16
atualizado: 2026-05-06
---

# 🤰 Conexão Gestantes — Hub

## O que é

Plataforma digital / infoproduto que vende **materiais clínicos editáveis prontos** para obstetras. Ticket único de **R$297 por compra**, com **~350 clientes ativos pagantes** na base.

## Modelo

- **Produto:** biblioteca de materiais editáveis (prescrições, orientações, checklists, protocolos clínicos)
- **Público:** obstetras (tratamento feminino — "obstetras", "Dra.")
- **Aquisição:** tráfego pago Meta Ads (Felipe gerencia direto)
- **Plataforma de checkout:** Hotmart
- **Conversão conversacional:** WhatsApp via Manychat (identidade fixa "Vitória")
- **Hospedagem LP:** Hotmart Pages (https://conecttahub.com.br/conexaogestantes)

## Status atual

> [!success] Fase 1 da retomada — em andamento (dia 13)
> Tráfego rodando desde 23/04/2026. Após otimizações de 30/04 e 01/05, métricas saltaram pra zona verde. Régua técnica de aprovação Fase 2 já atingida.

### Indicadores acumulados (período 01-04/05, 4 dias pós-otimização)

| Métrica | Atual | Meta verde | Status |
|---|---|---|---|
| ROAS | 5,98x | >3,0x | ✅✅✅ |
| CPA | R$48,39 | <R$80 | ✅✅ |
| CTR | 1,46% | >1,0% | ✅ |
| Vendas/dia | 2,5 | ≥2 | ✅ |

### Configuração ativa

- **Camp 01 LL1% Compradores** — R$60/dia, ROAS 5,17x últimos 4 dias
- **Camp 02 Aberto** — R$60/dia (monitorar esgotamento, CTR caindo)
- **Camp 04 LL1% ViewContent 90D** — R$60/dia, **ativada em 05/05/2026** (não mexer até 12/05)
- **Investimento total:** R$180/dia · ~R$1.260/semana
- **4 anúncios ativos:** Vídeos 13, 14, 15 + Estático 17. Algoritmo concentrou em Vídeo 15.

### Próxima checagem oficial: **12/05/2026** (régua de aprovação Camp 04)

## Notas principais

### Status e operação atual
- [[Fase1-Retomada AbrilMaio 2026]] — documento mestre da retomada
- [[Analise - 12dias Fase1]] — análise quantitativa consolidada
- [[Continuidade-Proxima-Conversa]] — handoff entre conversas

### Criativo
- [[Criativos - Estrutura Fase 1]] — fórmula vencedora dos 4 criativos atuais
- [[Criativos - Vídeo 10 (referência)]] — referência histórica
- [[Copy - Diretrizes]] — princípios atemporais

### Conversão e LP
- [[Landing Page - Status e pendências]] — pendências estruturais ativas
- [[Playbook - Otimizacão LP Hotmart]] — playbook técnico de performance
- [[WhatsApp - Fluxo de mensagens]] — fluxo conversacional Manychat

### Automação em curso
- [[Manychat - Carrinho Abandonado]] — investigação + solução em implementação (Make)

### Produto / futuro
- [[Prototipo - App Gestantes]] — exploração de evolução

## Aprendizados consolidados

> [!tip] Insights validados na Fase 1
> 1. **3 ajustes técnicos pequenos transformaram a Fase 1** (pausa Camp 03 + botões unificados + imagens otimizadas). ROAS +144%, CPA -55%, sem mexer em criativo nem público.
> 2. **Botões CTA da LP tinham bug crítico** que custava 84% dos cliques. Diagnóstico via Clarity heatmap.
> 3. **LP em deterioração silenciosa** (84 → 73 em 1 mês) por scripts acumulados + cache Hotmart Pages + imagens com dimensões erradas. Auditoria periódica é necessária.
> 4. **PageSpeed Insights tem oscilação alta.** Sempre validar com GTmetrix antes de decisões.
> 5. **Vídeo 4 está oficialmente morto.** Vídeo 15 é o novo hero (replica fórmula POV mesa madeira). Vídeo 14 é underdog promissor (ROAS 18x latente em volume baixo).
> 6. **Atribuição via WhatsApp pós-anúncio funciona.** Pessoas vêm do anúncio, perguntam no WhatsApp, fecham via link. Meta atribui pela janela de clique.
> 7. **Order Bump (Kit Check-in)** começou a aparecer (R$251,73 em 4 dias). Pode ser sinal de público mais qualificado.
> 8. **NÃO aumentar verba em campanha existente.** Padrão histórico de 9 meses confirmado. Solução: criar conjuntos/campanhas novas.
> 9. **Manter consistência em "Vitória"** como identidade WhatsApp.
> 10. **Inflar prova social é veneno.** "2.000 obstetras" → "350 obstetras" (base real).

## Frentes ativas em prioridade

### Alta — fazer já
1. **Concluir implementação Manychat carrinho abandonado via Make** (travado em visualização do JSON do webhook)
2. **Criar Mensagem 2 do fluxo WhatsApp** (cobrança/follow-up, +24h após mensagem 1)
3. **Monitorar Camp 04 sem mexer** até 12/05

### Média — semana que vem
4. **Avaliar Camp 04 no dia 12/05** (régua: ROAS ≥3x, CPA ≤R$80, CTR ≥1%)
5. **Confirmar tendência de esgotamento Camp 02 Aberto** (CTR caiu de 1,93% pra 1,40% entre 03 e 04/05)
6. **Documentar SOP** do processo de carrinho abandonado completo

### Baixa — após estabilização
7. **Próxima rodada de otimização LP** — atacar scroll depth (~37%). Reorganizar arquitetura.
8. **Tagueamento de cliques no WhatsApp via GTM**
9. **Considerar campanha dedicada Vídeo 14** (ROAS 18x latente)
10. **LL3% Compradores** como próxima escalada de público
11. **Inlead/quiz** como mudança estrutural de funil
12. **Conteúdo orgânico** pra alimentar seed Visitantes LP
13. **Melhorar visualmente "O Nascimento de uma Mãe"** pra usar em criativos

## Régua de monitoramento padrão

| Métrica | Verde | Amarelo | Vermelho |
|---|---|---|---|
| CTR (link) | >1,0% | 0,7-1,0% | <0,7% |
| CPA | <R$80 | R$80-120 | >R$120 |
| ROAS Hotmart | >3,0x | 2,0-3,0x | <2,0x |
| Vendas/dia | ≥2 | 1 | 0 por 3+ dias |
| Frequência | <2,0 | 2,0-3,0 | >3,0 |
| Scroll depth (Clarity) | >50% | 30-50% | <30% |
| Taxa LP→IC | >8% | 4-8% | <4% |
| Taxa IC→Compra | >40% | 25-40% | <25% |

## Configuração técnica de tracking

- **Pixel Meta:** 1050936263908154
- **Microsoft Clarity:** instalado via GTM Web em 23/04/2026
- **GTM:** Web + Servidor (Stape)
- **UTMs Meta:** `src=ig|paid|{{campaign.id}}|{{adset.id}}|{{ad.id}}&sck={{campaign.name}}` no campo "Parâmetros de URL"
