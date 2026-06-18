# Hermes Marketing by CCB

![Demonstração](docs/imagens/demo.gif)

> **Falta o GIF de demonstração.** Grave 15–30s mostrando você pedindo um post pelo Telegram
> e o agente respondendo um comentário/DM no Instagram (qualificando um lead). Exporte como GIF e salve em
> `docs/imagens/demo.gif` (ferramentas: QuickTime + Gifski, ScreenToGif, ou `asciinema`+`agg`).
> Passo a passo em [docs/imagens/COMO-GRAVAR-O-GIF.md](docs/imagens/COMO-GRAVAR-O-GIF.md).

## 1. O que é
Um agente que cuida do Instagram da **sua agência de marketing/social media**: responde dúvidas sobre os serviços, qualifica leads e convida para uma reunião de diagnóstico, além de criar posts — tudo controlado pelo seu **Telegram**, sem você precisar mexer em código.

## 2. Benefícios
- **Nenhum lead esfria.** Aquela DM das 23h ("quanto custa gestão de tráfego?") é respondida na hora, qualificada e encaminhada — em vez de virar conversa morta no dia seguinte.
- **Você só entra no momento certo.** O agente filtra curiosos, qualifica quem tem fit e só te chama no Telegram quando é lead bom ou hora de marcar a reunião.
- **Prospecção que não dorme.** Ele trabalha o Instagram como um SDR 24/7: responde, faz as perguntas de qualificação e puxa para o diagnóstico.
- **Padroniza seu pitch.** Sempre dentro do seu tom e das suas regras — nada de funcionário improvisando preço ou prometendo resultado.
- **Não queima a venda.** Por padrão, nunca fecha contrato, valor ou promete número de vendas: qualifica e leva para a reunião, onde você fecha.

## 3. Casos de uso reais
- **"Quanto custa gestão de tráfego?"** — o agente explica que o investimento depende de um diagnóstico, faz 2-3 perguntas de qualificação e convida para uma reunião. Te avisa no Telegram.
- **"Vocês fazem social media pra clínica?"** — explica os serviços, mostra como ajuda o negócio da pessoa, qualifica e puxa para o diagnóstico.
- **DM de lead interessado** — faz as perguntas de qualificação (qual negócio, objetivo, orçamento se a regra permitir) e marca a call. Te manda o resumo do lead no Telegram.
- **Comentário "como cresço no Instagram?"** — responde em público com uma dica de valor de verdade, mostra autoridade e convida a seguir + chamar no Direct.
- **"Tô começando do zero, vale a pena?"** — acolhe, qualifica o objetivo e convida para um diagnóstico em vez de cravar pacote ou preço.

Veja os roteiros completos em [docs/CASOS-DE-USO.md](docs/CASOS-DE-USO.md).

## 4. Pré-requisitos
1. Uma **VPS** com o **Hermes Agent já instalado** (Docker **ou** nativo). (Material da CCB.)
2. O Hermes com um **modelo de IA configurado** (`hermes setup`).
3. **Telegram** no celular.
4. Uma conta no **Zernio** (zernio.com) com o **Instagram da agência conectado**.
5. Uma conta **Google** com uma agenda — o assistente te guia a conectar (via "conta de serviço") para o agente **marcar reuniões de diagnóstico sozinho** na sua Google Agenda.

## 5. Como instalar (1 comando)
Conecte na sua VPS por SSH e cole:

```bash
curl -fsSL https://raw.githubusercontent.com/kleinelizeu/marketing-ccb/main/install.sh | sudo bash
```

O assistente abre sozinho e te guia. Depois, a qualquer momento:

```bash
hermes-marketing            # roda/continua o assistente
hermes-marketing doctor     # confere tudo e corrige problemas comuns
hermes-marketing info       # mostra endereço do webhook, chave e nome do bot
hermes-marketing contexto   # mostra o texto da sua agência para colar no bot
```

## 6. Como usar no dia a dia
No Telegram do seu bot, é só pedir em português normal:
- "Crie um post sobre os 3 erros que fazem o Instagram não vender, com uma imagem moderna. Me mostra antes de publicar."
- "Responde quem comentou perguntando preço qualificando o lead e chamando pra uma reunião de diagnóstico."
- "Quantos leads me mandaram DM hoje querendo tráfego pago?"
- "Muda meu tom de voz pra mais próximo e moderno."

## 7. Perguntas frequentes + comandos
**Preciso saber programar?** Não. O assistente faz tudo e explica onde clicar.

**O agente vai fechar contrato e cravar preço?** Não. Por padrão ele qualifica o lead e convida para a reunião de diagnóstico — quem fecha proposta e valor é você.

**Mexe no meu Hermes que já uso?** Cria um agente **separado** (`marketing`), sem mexer no que você já tem.

**Onde ficam minhas senhas e chaves?** Só na **sua VPS**, em `/root/.marketing-ccb/` (protegida).

**Testei do meu próprio Instagram e não respondeu.** Normal: o Zernio só dispara para **outra** pessoa.

**As respostas pararam.** Rode `hermes-marketing doctor` — costuma detectar e corrigir.

Mais detalhes em [docs/COMO-FUNCIONA.md](docs/COMO-FUNCIONA.md), [docs/CASOS-DE-USO.md](docs/CASOS-DE-USO.md) e [docs/PROBLEMAS-COMUNS.md](docs/PROBLEMAS-COMUNS.md).
