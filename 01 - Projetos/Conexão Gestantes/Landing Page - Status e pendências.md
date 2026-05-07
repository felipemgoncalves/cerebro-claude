---
tags: [projeto/conexao-gestantes, landing-page, conversao, pendencias]
criado: 2026-04-16
atualizado: 2026-05-06
status: parcialmente-otimizada
relacionado: "[[Fase1-Retomada AbrilMaio 2026]]"
---

# 🖥️ Landing Page — Status e pendências

## Status geral

LP em produção e gerando conversões. Performance técnica recuperada após auditoria de 01/05 (89 mobile / 99% desktop). Próxima fronteira é **arquitetura de conversão** (scroll depth ~37% indica que maioria não chega na seção de preço).

URL: https://conecttahub.com.br/conexaogestantes
Hospedagem: Hotmart Pages com domínio próprio (AWS S3 + CloudFront via GRU3)

## ✅ Concluído

- [x] Revisão de H1 e H2 (novo copy aplicado em 24/04)
- [x] Ajustes de linguagem alinhados à [[Copy - Diretrizes]]
- [x] Tratamento feminino aplicado ("obstetras")
- [x] Correção de prova social (2.000 → 350 obstetras, consistência com criativos)
- [x] **Unificação dos 3 botões CTA (30/04)** — antes só o último botão funcionava (84% dos cliques eram dead). Após: todos abrem pop-up imediatamente. Initiate Checkouts dispararam de ~1/dia pra 6,75/dia.
- [x] **Otimização de imagens (01/05)** — Performance 73 → 89 mobile / 99% desktop. LCP 5,2s → 2,9s. Ver [[Playbook - Otimizacão LP Hotmart]] para método.
- [x] Pixel Meta validado disparando corretamente
- [x] Pixel de conversão de compra validado em checkout

## 🛠️ Pendências estruturais (ativas)

### 1. Price anchor — reposicionamento
- [ ] Price anchor visível antes do price box
- [ ] Contextualizar o ancoramento (comparativo com serviço/produto equivalente)
- [ ] Apresentar o "de/por" de forma clara

### 2. Social proof strip
- [ ] Inserir faixa de prova social (logos, números, depoimentos curtos)
- [ ] Posicionamento ideal: logo após o hero
- [ ] Mobile: carrossel ou linha com scroll horizontal

### 3. Urgência
- [ ] Adicionar elementos de urgência (quantidade limitada, contador, oferta com prazo)
- [ ] Urgência **honesta** (sem falsa escassez)
- [ ] Visível em mobile sem invadir leitura

### 4. Hierarquia do price box
- [ ] Preço em destaque (maior peso visual)
- [ ] Bônus listados com ícones
- [ ] CTA do price box em cor de destaque
- [ ] Garantia / segurança em linha secundária
- [ ] Formas de pagamento visíveis

### 5. CTA sticky no mobile
- [ ] CTA flutuante persistente (acompanha scroll)
- [ ] Texto curto e direto
- [ ] Não sobrepor conteúdo crítico

### 6. Arquitetura de conversão (scroll depth)
- [ ] Diagnóstico via Clarity heatmap focado em comportamento
- [ ] Reorganizar ordem das seções
- [ ] Considerar trazer preço/oferta mais cedo
- [ ] Possivelmente vídeo curto na primeira dobra
- **Quando atacar:** após estabilização da Camp 04 (~14/05). Não mexer em LP enquanto há dados sendo coletados pra validar campanhas.

## Princípios para revisão

> [!tip] Checklist mental
> - Passa o "**teste dos 5 segundos**"? (O que é? Para quem? Por quanto?)
> - Mobile-first: hierarquia visual funciona sem zoom?
> - Cada seção responde a uma **objeção específica**?
> - CTA nunca fica a mais de uma rolagem de tela
> - Performance Score mobile >85 antes de publicar

## Ordem sugerida de execução (próxima rodada)

1. **Diagnóstico Clarity** — identificar onde scroll morre
2. **Reorganização estrutural** baseada em dados (não opinião)
3. **Price box** (impacto direto na conversão)
4. **Social proof strip** (confiança)
5. **Urgência** (empurrão final)
6. **Auditoria de performance** pós-mudanças (ver Playbook)

## Após qualquer mudança significativa

- [ ] Revisão geral em desktop e mobile
- [ ] Teste de velocidade (PageSpeed mobile + GTmetrix desktop)
- [ ] Pixel Meta conferido
- [ ] Pixel de conversão de compra validado em checkout
- [ ] Validar com Clarity nos primeiros 7 dias

## Relacionado

- [[Fase1-Retomada AbrilMaio 2026]]
- [[Playbook - Otimizacão LP Hotmart]]
- [[Copy - Diretrizes]]
- [[Conexão Gestantes - Hub]]
