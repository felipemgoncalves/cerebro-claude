---
tags: [projeto/conexao-gestantes, automacao, manychat, hotmart, integracao]
criado: 2026-04-16
atualizado: 2026-04-16
status: diagnostico-completo
---

# 🔗 Integração Manychat + Hotmart

## Objetivo

Recuperar **carrinho abandonado** do Hotmart via **WhatsApp** (Manychat).

## Limitação estrutural diagnosticada

> [!warning] Descoberta importante
> A recuperação via WhatsApp **só funciona para contatos que já estão no Manychat**. Se o lead **nunca interagiu** com o WhatsApp da marca, o Manychat não tem permissão/sessão para iniciar conversa.
>
> Implicação: **necessário capturar o contato no WhatsApp antes do checkout** (ou pelo menos em algum ponto do funil anterior).

## Abordagem diagnóstica adotada

- **Webhook.site** usado como endpoint de inspeção
- Finalidade: entender exatamente quais dados o Hotmart envia no evento de abandono
- Permitiu mapear payload antes de conectar ao Manychat de verdade

## Arquitetura desejada

```
Lead visita landing
       ↓
Clica em CTA → vai para WhatsApp (Manychat captura)
       ↓
Manychat envia para checkout Hotmart (link personalizado)
       ↓
Se paga → fim do fluxo
Se abandona → Hotmart webhook → Manychat → mensagem de recuperação
```

## Componentes

### Manychat
- Gatilho de entrada: clique no CTA do WhatsApp na landing
- Flow de pré-checkout (captura nome + envia link Hotmart)
- Flow de recuperação (disparado pelo webhook)

### Hotmart
- Webhook de "carrinho abandonado" apontado para Manychat (ou intermediário)
- Possível uso de Make/Zapier como ponte para transformação de dados

### Webhook.site (fase de diagnóstico)
- URL temporária apenas para observar payload
- Substituída em produção pelo endpoint real

## Próximos passos

- [ ] Definir se Manychat recebe direto ou se passa por [[Make (Integromat)|Make]]
- [ ] Ajustar CTA da landing para **forçar passagem pelo WhatsApp** antes do checkout
- [ ] Criar flow de recuperação com 2-3 mensagens escalonadas
- [ ] Testar cenário real com compra abandonada de teste
- [ ] Monitorar taxa de recuperação pós-implementação

## Riscos

- **Atrito maior no funil** se todos passarem pelo WhatsApp antes do checkout
- Considerar versão **híbrida**: checkout direto para quem veio aquecido, WhatsApp para tráfego pago frio

## Relacionado
- [[Manychat]]
- [[Hotmart]]
- [[Make (Integromat)]]
- [[Automação e Ferramentas]]
