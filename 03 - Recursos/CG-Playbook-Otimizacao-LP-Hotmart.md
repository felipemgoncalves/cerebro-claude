---
tags: [conexao-gestantes, hotmart-pages, performance, lp, playbook, recurso]
data: 2026-05-01
ultima-atualizacao: 2026-05-05
relacionado: "[[CG-Fase1-Retomada-AbrilMaio2026]]"
---

# Playbook de Otimização da LP — Hotmart Pages

Documento criado a partir da auditoria de 01/05/2026, quando a LP estava com Performance 73 e foi otimizada pra 89 (mobile) / 99% (desktop) em 15 minutos.

## Contexto do achado original

LP foi publicada em mar/2026 com Performance 84. Ao longo de 1 mês, sem ninguém adicionar imagens conscientemente, o score caiu pra 73. Causa: ferramentas de tracking acumuladas + cache da Hotmart Pages comportamento agressivo + imagens com dimensões erradas (até 13x maiores que tamanho de exibição).

**Aprendizado central:** Hotmart Pages requer auditoria periódica de performance. Não confiar em "publicou e ficou rápido pra sempre".

## Métricas-alvo

| Métrica | Bom | Ideal |
|---|---|---|
| Performance Score (mobile) | >85 | 90+ |
| LCP | <2,5s | <1,5s |
| FCP | <2,0s | <1,5s |
| TBT | <200ms | <100ms |
| CLS | <0,1 | 0 |

## Ferramentas de medição

1. **PageSpeed Insights** (pagespeed.web.dev) — Google, gratuito, mas com oscilação alta. Use pra ter referência geral.
2. **GTmetrix** (gtmetrix.com) — mais estável, faz desktop por padrão. Versão paga pra mobile.
3. **WebPageTest** (webpagetest.org) — mais detalhado, escolha região Brasil.
4. **Microsoft Clarity** — fonte mais fiel porque mede experiência real de usuários reais, não simulação.

**Regra:** sempre validar resultados de PageSpeed em pelo menos uma segunda ferramenta antes de decisões. PageSpeed pode dar 73 num teste e 99 no outro com 30min de diferença.

## Diagnóstico cirúrgico de imagens

No PageSpeed → seção "Melhorar a entrega de imagens" → expandir:

A coluna "Dimensões reais vs exibidas" é a mais importante. Procurar por:
- Imagens com **largura real >2x da largura exibida** = candidata a otimização
- Imagens com **>50 KiB** que não são hero
- Imagens **duplicadas** (mesma URL aparecendo 2+ vezes na lista)

Priorizar pelo campo **"Economia estimada"** — focar nos 3 maiores.

## Compressão padrão

**Ferramenta:** Squoosh (squoosh.app)

**Configuração padrão pra imagens secundárias:**
- Formato: WebP
- Qualidade: 75-80%
- Dimensões: 2x do tamanho real de exibição (Retina-ready)

**Configuração pra hero/imagens principais (qualidade visual importa mais):**
- Formato: WebP
- Qualidade: 88-90%
- Dimensões: 2x do tamanho real de exibição

**Alternativa se WebP perder muita qualidade visual:**
- MozJPEG qualidade 85% (preserva texturas e gradientes melhor que WebP em alguns casos)

## Tamanhos-alvo após compressão

- Hero (primeira dobra): 30-60 KB
- Imagens secundárias: 15-40 KB
- Mockups e cards: 10-30 KB
- Ícones e logos: <10 KB

## Limitações conhecidas da Hotmart Pages

Coisas que **não dá pra resolver**, são da plataforma:

1. **Cache de 10 segundos** (cache-control: max-age=10). Força CloudFront a revalidar muito frequentemente.
2. **DOM grande** (~2.800 elementos). Plataforma cria muito código pra cada bloco.
3. **Sem controle direto de minificação** de CSS/JS.
4. **Sem font-display: swap** customizável.
5. **Tamanho HTML grande** (599KB) por causa de imagens em base64 e estrutura.

Se a LP precisar de Performance >95 estável, é caso de migrar pra plataforma mais flexível (Cartpanda, Vercel/Netlify custom, etc).

## Auditoria recomendada

**Frequência:** mensal ou após qualquer mudança significativa na LP.

**Checklist:**

1. Roda PageSpeed mobile + GTmetrix desktop no mesmo horário
2. Compara com último benchmark salvo
3. Se Performance caiu >5 pontos, expande "Melhorar a entrega de imagens"
4. Identifica os 3 vilões (maior economia)
5. Otimiza no Squoosh
6. Republica e mede de novo

**Sinal de alerta:** se LCP passa de 3s no mobile, é caso pra ação imediata. Cada segundo extra custa ~7-10% de conversão em tráfego pago.

## Análise via Clarity (heatmaps + gravações)

**Quando usar:** após auditoria técnica OK, mas conversão ainda baixa.

### Heatmap de cliques
- Identifica botões com cliques mortos (caso famoso: 3 botões CTA da LP CG, dos quais só 1 funcionava)
- Mostra elementos que recebem cliques sem ser links
- Revela se botão WhatsApp está canibalizando CTA principal

### Heatmap de scroll
- Mostra "linha de morte" da página
- Se 50% das pessoas param antes da seção de preço, problema crítico
- Indica se precisa reorganizar arquitetura da LP

### Gravações
- Filtrar por duração >30s pra cortar bots/abandono imediato
- Olhar 5-8 sessões: 2-3 que converteram, 2-3 que chegaram perto e desistiram, 1-2 que saíram rápido
- Padrões revelam fricções específicas

## Histórico de medições — LP Conexão Gestantes

| Data | Performance (mobile) | LCP | FCP | Contexto |
|---|---|---|---|---|
| 25/03/2026 | 84 | 1,9s | 1,9s | Publicação inicial |
| 14/04/2026 | 84 | — | — | Após ajustes pós-publicação |
| 01/05/2026 (manhã) | 73 | 5,2s | 2,8s | **Antes da auditoria** — degradação silenciosa em 1 mês |
| 01/05/2026 (após otimização) | 89 | 2,9s | 1,9s | PageSpeed mobile |
| 01/05/2026 (GTmetrix) | 99% | 782ms | 663ms | Desktop |

## Lições do diagnóstico cirúrgico de 01/05/2026

### Os 3 vilões reais identificados (256 KiB de 450 KiB potenciais = 57% do problema)

1. **Foto da Sueli (testimonial textual)** — 879×1280 pixels exibida em 236×343 = 13x maior que necessário. Sozinha valia 25% da economia possível.

2. **Composição dos mockups (duplicada na LP)** — 1283×738 exibida em 581×341. **Carregada DUAS VEZES** com mesma imagem. 75 KiB cada × 2 = 150 KiB de economia só ajustando uma e removendo duplicata.

3. **Hero principal** — apesar de já razoavelmente otimizado, ainda dava pra ganhar.

**Os depoimentos NÃO eram o problema principal.** Felipe estava preocupado com perder qualidade visual deles, mas representavam apenas 129 KiB somados (vs 256 KiB dos 3 vilões). Foco cirúrgico evitou trabalho desnecessário.

### Estratégia visual vs performance

- Hero: usar qualidade 88-90% (visualmente melhor)
- Imagens secundárias: 75-80% (imperceptível pro usuário)
- Volatilidade do PageSpeed exige validar com 2ª ferramenta antes de decisões

## Próximo nível de otimização (a fazer no futuro)

Performance técnica está OK. **Próxima fronteira é arquitetura da LP:**

- Scroll depth de ~37% indica que maioria não chega na seção de preço
- Reorganizar ordem das seções
- Considerar trazer preço/oferta mais cedo
- Possivelmente vídeo curto na primeira dobra
- Próxima auditoria via Clarity heatmap focada em comportamento

**Quando atacar:** após estabilização da Camp 04 (~14/05). Não mexer em LP enquanto há dados sendo coletados pra validar campanhas.
