# Como funciona (em linguagem simples)

O Hermes Marketing liga três coisas: o **Instagram** da sua agência, o **Zernio** e o seu **agente Hermes**, com o **Telegram** como seu "painel de controle".

## As duas demonstrações

### Demo 1 — Posts com imagem
Você pede um post pelo Telegram (ex.: "crie um post sobre os 3 erros que fazem o Instagram não vender, com uma imagem moderna"). O agente escreve a legenda, gera a imagem e mostra para você aprovar. Aprovou, ele publica no Instagram pelo Zernio.

### Demo 2 — Respostas automáticas e qualificação de leads
Quando alguém comenta ou manda DM no Instagram da agência, o Zernio avisa o seu agente na hora (*webhook*). O agente lê, responde seguindo as regras da agência (tira a dúvida, faz as perguntas de qualificação, convida para a reunião de diagnóstico — sem fechar contrato sozinho) e te manda um resumo do lead no Telegram.

```
Comentário/DM no Instagram
        │
        ▼
     Zernio  ──(internet, HTTPS)──►  seu agente Hermes
        ▲                                  │
        │                                  ├─ responde e qualifica no Instagram
        └────────── publica posts ◄────────┤
                                           └─ te avisa no Telegram (resumo do lead)
```

## Por que precisa de "endereço HTTPS"
Para o Zernio falar com o seu agente pela internet, o agente precisa de um endereço seguro (https).

- **Docker:** o Traefik do seu Hermes cria esse endereço automaticamente (estável).
- **Nativo:** usamos o **Cloudflare Tunnel** (cloudflared). Esse endereço pode mudar se a VPS reiniciar — por isso existe o `hermes-marketing doctor`, que detecta o novo e te avisa para atualizar no Zernio.

## Onde ficam suas informações
Tudo que você digita (tokens, chave do Zernio, dados da agência) fica só na sua VPS, em `/root/.marketing-ccb/`, com acesso restrito. As "instruções de trabalho" do agente você mesmo cola no bot do Telegram para ele guardar na memória.

## O agente qualifica, mas não fecha
O agente é configurado para fazer o trabalho de SDR: tirar dúvidas, qualificar (qual negócio, objetivo e — se a regra permitir — orçamento) e convidar para a reunião de diagnóstico. Ele **nunca** fecha proposta, valor ou contrato sozinho, e não promete número de vendas ou seguidores: quem decide e fecha é você. Lead bom ou pedido de reunião, ele te avisa no Telegram.
