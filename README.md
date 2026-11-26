ï»¿# r7ex ê¢â¬â o reel viral do INEMA

[![r7ex ê¢â¬â o reel viral do INEMA](guia/assets/banner.jpg)](https://inematds.github.io/r7ex/guia/)

**ê°Å¸â¡Â§ê°Å¸â¡Â· [PortuguêÂªs](README.md) êÂ· ê°Å¸â¡Âºê°Å¸â¡Â¸ [English](README.en.md) êÂ· ê°Å¸â¡Âªê°Å¸â¡Â¸ [EspaêÂ±ol](README.es.md)**

## O que êÂ©

O r7ex êÂ© a linha de produêÂ§êÂ£o de reels verticais (9:16) do INEMA. VocêÂª entrega uma ideia forte, a tese, e ele monta um vêÂ­deo de 40 a 50 segundos (30ê¢â¬â37 s de fala num ritmo calmo + 9 s de cartêÂ£o do comentêÂ¡rio) com o avatar do Nei falando, imagens geradas pelo Codex e um acabamento de telejornal: têÂ­tulo na abertura, painêÂ©is que entram na palavra certa, contador e legenda que acende junto com a fala. O roteiro segue 7 etapas de gatilho, do gancho com nêÂºmero atêÂ© o pedido de comentêÂ¡rio, sempre levando a pessoa ao inema.club. Para usar êÂ© preciso Python, Node, o Codex e a assinatura do HeyGen, rodando na mêÂ¡quina do INEMA.

## ê°Å¸Å½Â¬ VêÂ­deos sobre o r7ex

Feitos com o prêÂ³prio r7ex (19/10/2026):

- [Reel 1 ê¢â¬â "Meus reels tiveram zero visualizaêÂ§êÂ£o, 4 lotes atêÂ© acertar"](https://inematds.github.io/r7ex/guia/assets/videos/r7ex-divulga.mp4)
- [Reel 2 ê¢â¬â "O reel de 7 etapas ficou velho, agora tem o r7ex"](https://inematds.github.io/r7ex/guia/assets/videos/r7e-para-r7ex.mp4)

TambêÂ©m tocam no guia, seêÂ§êÂ£o Exemplos.

## ê°Å¸ââ Guia de uso

Guia completo (landing + passo a passo): **https://inematds.github.io/r7ex/guia/**

---

**r7ex = r7e + x.** O **r7e** (reel7etapas) dêÂ¡ o **roteiro**: 7 etapas de gatilho, do gancho ao comentêÂ¡rio.
O **x** vem do **eventosextremospub**: o **acabamento de telejornal** que viraliza mais.
Objetivo de todo reel: **trazer gente para o inema.club.**

Este repo funciona **sozinho**: tem cêÂ³pia prêÂ³pria do motor de render, dos scripts do estêÂºdio do HeyGen, da transcriêÂ§êÂ£o,
da trilha, do envio ao bot e da fila de publicaêÂ§êÂ£o. Mudar algo aqui **nêÂ£o afeta** o eventosextremospub, o reel7etapas,
o explicavideos nem o cardshorts.

- PadrêÂ£o fixo (a regra curta): [`PADRAO.md`](PADRAO.md)
- Ficha de exemplo (o reel do hacker): [`modelo/ficha.yaml`](modelo/ficha.yaml)

---

## O processo, do inêÂ­cio ao fim (12 passos)

ê°Å¸Â§Â  = sessêÂ£o com o Nei (gasta tokens) êÂ· ê¢Å¡â¢ê¯Â¸Â = script/timer (zero token) êÂ· ê°Å¸Â¤â = `claude -p` curto (sessêÂ£o nova)

**Parte 1: com o Nei, na sessêÂ£o**

| # | Passo | Comando / o que acontece | Quem |
|---|---|---|---|
| 1 | Pedido | o Nei diz o tema, o canal e o que citar | Nei |
| 2 | Pesquisa | conferir fatos e fontes (vêÂ£o para `plano.fatos` com a origem) + **ganchos de quem fala do tema** (v1.5.4): têÂ­tulos com `yt-dlp --flat-playlist "ytsearch15:<termo>"` e a 1êÂª fala (0ê¢â¬â35 s) pela legenda automêÂ¡tica ê¢â â `gancho.referencias` (3ê¢â¬â5 `{canal, titulo, abertura, gatilho}`; nêÂºmero de terceiro nêÂ£o entra no roteiro, sêÂ³ serve de rêÂ©gua) | ê°Å¸Â§Â  |
| 3 | Ficha | `python3 r7ex.py novo <slug>` + escrever o **gancho** (tipo, manchete do quadro 0, objeto com dano, prova, absolviêÂ§êÂ£o, entrega ê¢â¬â v1.3.1; tipo `provocacao` no PADRAO êÂ§2.2), as 7 partes, a abertura, os painêÂ©is e `publicar`. VêÂ¡rios temas ê¢â â um vêÂ­deo por tema | ê°Å¸Â§Â  |
| 4 | PortêÂ£o da ficha | `python3 r7ex.py checar <pasta>`: 7 partes, objetivo 620 e teto 900 caracteres (D26), print sem repetir, palavras dos painêÂ©is na fala, **gancho** (tipo vêÂ¡lido, manchete ê¢â°Â¤ 6 palavras ê¢â°Â  fala, prova atêÂ© ~20 s, absolviêÂ§êÂ£o; lista reprova); **fecho** (v1.4.4: pergunta + inema ponto club, sem "me pede o link"/"comenta PALAVRA", tambêÂ©m em `cta.b`/`cta.comentario`); **avisos** v1.5.4: sem `gancho.referencias` (3ê¢â¬â5) e sem frase de comunidade antes da pergunta da parte 7 | ê¢Å¡â¢ê¯Â¸Â |
| 5 | PortêÂ£o viral | `python3 r7ex.py plano <pasta>`: crêÂ­tico (`producao/ia.yaml`, etapa `critico_plano`, com trava de cota e reserva) dêÂ¡ nota por parte; sem bloqueio, gancho ê¢â°Â¥ 8, mêÂ©dia ê¢â°Â¥ 7,5; compara o gancho com a melhor `gancho.referencias` e cobra a frase de comunidade na parte 7 (v1.5.4) | ê°Å¸Â¤â |
| 6 | Entregar êÂ  produêÂ§êÂ£o | `avatar/APROVADO_HEYGEN` + `python3 producao/producao.py --add <pasta>` | ê°Å¸Â§Â  |
| 7 | Enviar o avatar | o timer `r7ex-producao` manda a fala ao estêÂºdio HeyGen (tela :99; todas as pendentes na mesma rodada, sem esperar a anterior ficar pronta ê¢â¬â 25/10/2026) | ê¢Å¡â¢ê¯Â¸Â |

**Parte 2: sem sessêÂ£o aberta**

| # | Passo | Comando / o que acontece | Quem |
|---|---|---|---|
| 8 | Esperar o avatar | `r7ex.py avatar-conferir` (HeyGen, sêÂ³ leitura) atêÂ© "pronto" e baixa. **Minutos a horas** | ê¢Å¡â¢ê¯Â¸Â |
| 9 | Montar | `r7ex.py fazer`: Codex desenha a **capa chocante** (com prova `capa/abertura.codex.json`; o render recusa sem ela, D24) e as imagens, prints, tempos das palavras, **ritmo** (`r7ex/ritmo.py`: fala esticada atêÂ© ~182 palavras/min, ~0,75 s de silêÂªncio antes da mêÂ¡xima, cartêÂ£o do comentêÂ¡rio 9 s depois da êÂºltima palavra com o gesto de comentar ê¢â¬â 28/10/2026), legenda, render e `build/folha.jpg` | ê¢Å¡â¢ê¯Â¸Â |
| 10 | Revisar | revisor (`producao/ia.yaml`, etapa `revisao_visual`) + `producao/revisor.md` lêÂª a folha: aprova, aprova com ê°Å¸Å¸Â¥ SUGESTêÆO ou para com o motivo | ê°Å¸Â¤â |
| 11 | Entregar | `r7ex.py enviar` (v3) + `r7ex.py fila` (fila do canal); aviso "Terminei" no v3 | ê¢Å¡â¢ê¯Â¸Â |
| 12 | Publicar | o timer da fila sobe 1 a cada 2 h (9 hê¢â¬â21 h) pelo yt-pubx e avisa no v3 | ê¢Å¡â¢ê¯Â¸Â |

**Pelo bot, sem sessêÂ£o nenhuma (22/10/2026): `/r7ex <tema>` no inemaccbot.** (Desde 05/11/2026 o `/rtex` do bot roda o repo `rtex` e existe o `/rtexjp`; atêÂ© entêÂ£o o `/rtex` era apelido deste.)

| # | Passo | Comando / o que acontece | Quem |
|---|---|---|---|
| B1 | Pedido | o Nei manda `/r7ex <tema, canal, "agora">` no inemaccbot; o comando jêÂ¡ êÂ© o OK do avatar | Nei |
| B2 | Ficha + portêÂµes | fase `ficha` (`prompts/bot-ficha.md`): passos 2ê¢â¬â6 acima, canal em `publicar.fila`, "agora" ê¢â â `FRENTE`, `APROVADO_HEYGEN`, `producao.py --add`; mostra o `BOT-RESUMO.md` no chat | ê°Å¸Â¤â |
| B3 | ProduêÂ§êÂ£o | passos 7ê¢â¬â11 pelo timer `r7ex-producao`, como sempre | ê¢Å¡â¢ê¯Â¸Â |
| B4 | Fim no bot | fase `producao`: `producao/esperar.py <pasta>` espera `na_fila` e mostra o `BOT-FIM.md`; `parado` ê¢â â falha com o motivo | ê¢Å¡â¢ê¯Â¸Â |

DefiniêÂ§êÂ£o: `flow.json` (prefixo `RX`), ajuda do bot em `HELP.md`. O bot nêÂ£o faz upload direto nem têÂ³pico no Telegram:
isso continua pela sessêÂ£o + vigia `continua` (abaixo). O `/r7ex` no terminal segue igual.

**Quando o Nei pede algo fora do caminho padrêÂ£o** ("publica agora sem fila", "posta no INEMA.DEV", links no inemaytbot),
os passos 8ê¢â¬â12 vêÂ£o pelo vigia **`continua`** do wifi (`~/projetos/wifi/continua`): a sessêÂ£o escreve
`<pasta>/CONTINUAR.md` com o que falta, as ordens e as travas, tira a ediêÂ§êÂ£o da produêÂ§êÂ£o e registra
`continua.py --add <pasta> --cwd ~/projetos/r7ex --confere "python3 r7ex.py avatar-conferir <pasta>"`. Quando o avatar
fica pronto, o vigia abre uma **sessêÂ£o nova** (`claude -p`) que lêÂª sêÂ³ o bilhete e segue atêÂ© o fim. O `--add` avisa no v3
("ê¢ÂÂ³ Fase 1 concluêÂ­da", msg N) e a sessêÂ£o termina dizendo "pode fechar o terminal, acompanhe pela msg N"; o Terminei/Falhou
da fase 2 chega como resposta a essa mensagem. Detalhes: `~/projetos/wifi/continua/README.md`.
Primeiro uso: `edicoes/2026-10-22-hackers-atacam` (22/10/2026).

---

## 1. Como chegamos aqui (18/10/2026) ê¢â¬â 4 lotes, o que mudou em cada um

| Lote | ConteêÂºdo (o que se fala) | Forma (o que se vêÂª) | Resultado |
|---|---|---|---|
| **1. r7e antigo** (deepseek, faxina, opencode, contexto, diga) | Assunto do dia (divulgar guia/repo), pêÂºblico de nicho, gancho = **promessa** ("SEU AGENTE OBEDECE E GASTA MENOS"), 7 etapas em ordem fixa, medo fraco e êÂ s vezes desarmado na hora | Motor do r7e: foto de banco de imagens desfocada atrêÂ¡s do rosto em meia tela, letra Anton com êÂ¢mbar apagado | Sem visualizaêÂ§êÂ£o no TikTok/Instagram |
| **2. r7e "-gatilho"** (os mesmos 5, mesmo avatar) | Fala igual (a voz êÂ s vezes contrariava a tela) | SêÂ³ o gancho mudou: medo/novidade/provocaêÂ§êÂ£o com nêÂºmero, imagem nêÂ­tida dramêÂ¡tica, amarelo #FACC15 com contorno | Melhor, mas "ainda padrêÂ£o" |
| **3. r7e D10** (5 teses do Nei + hacker refeito; 2 de gestêÂ£o) | **Plano antes da fala** (pessoa, o que quer, gancho com nêÂºmero, nota, destino no inema.club), **fala nova** com o gatilho primeiro e o alêÂ­vio no meio, CTA fixo, prints reais das pêÂ¡ginas | Motor do r7e com tarja e diagramas em Pillow | "Ficou padrêÂ£o" |
| **4. r7ex** (os mesmos 7, **mesmo avatar e fala do lote 3**) | Nenhum conteêÂºdo novo: a fala dividida em 7 blocos, cada um com imagem e painel tirados da prêÂ³pria fala | **Motor do eventosextremospub**: têÂ­tulo dentro da arte, preto e dourado, faixa de telejornal, painêÂ©is no tempo da fala, contador, karaokêÂª, CTA em pergunta | Formato padrêÂ£o a partir de agora |

LiêÂ§êÂ£o: o **conteêÂºdo** acertou no lote 3 (teses fortes, gatilho, plano) e a **forma** acertou no lote 4 (motor do eventos).

### Links no YouTube

| O quêÂª | Link |
|---|---|
| O de referêÂªncia que funcionou (evento extremo, r7e antigo com flagrante + nêÂºmero) | https://www.youtube.com/shorts/DfdtX9HbkWg (lives10) |
| Lote 1 ê¢â¬â Faxina no setup (promessa, sem visualizaêÂ§êÂ£o) | https://www.youtube.com/shorts/E5Y94BLfuJU (lives4) |
| Lote 1 ê¢â¬â Camada de contexto (promessa, sem visualizaêÂ§êÂ£o) | https://www.youtube.com/shorts/XflFkvIl4mw (lives4) |
| Lote 3 ê¢â¬â DemissêÂ£o em massa de gerentes (motor r7e) | https://www.youtube.com/shorts/xpDV5qQe5oE (lives3) |
| Lote 3 ê¢â¬â FuncionêÂ¡rio que nêÂ£o êÂ© gente (motor r7e) | https://www.youtube.com/shorts/cMhIavjhdh0 (lives3) |
| **Lote 4 / r7ex ê¢â¬â Hackers roubaram as chaves** | https://youtube.com/shorts/DG30IdeqWcg (lives7) |
| Lote 4 / r7ex ê¢â¬â os outros 6 | na fila do lives7 (1 a cada 2 h); `python3 fila/fila.py --status` |

## 2. Como o conteêÂºdo êÂ© formado (o plano)

Antes de escrever uma palavra da fala:

1. **Pessoa:** pêÂºblico geral (IA traduzida para o dia a dia), nêÂ£o o nicho.
2. **O que ela quer:** ganhar algo, resolver uma dor ou chegar a um desejo.
3. **Gancho:** contrêÂ¡rio, perda, estatêÂ­stica, terceiro (histêÂ³ria de alguêÂ©m com nêÂºmero), notêÂ­cia (desta semana), provocaêÂ§êÂ£o,
   promessa ou acusaêÂ§êÂ£o (a dor/desejo da pessoa em "vocêÂª", v1.4.4) ê¢â¬â **com nêÂºmero, fato ou dor/desejo** e fonte. Nunca lista ("5 novidadesê¢â¬Â¦"), "vocêÂª sabiaê¢â¬Â¦" ou "eu fizê¢â¬Â¦". Um tema por vêÂ­deo.
   Regras completas do quadro 0 e dos 3 primeiros segundos: [PADRAO.md êÂ§2.1](PADRAO.md).
4. **Nota de potencial (0ê¢â¬â10):** "um desconhecido rolando o feed para aqui?" Abaixo de 8, troque o êÂ¢ngulo ou o tema.
5. **Destino:** a pêÂ¡gina do inema.club que resolve (vira o print de prova).

Base real: leio a pêÂ¡gina do curso/guia antes (nome, quantas aulas, se êÂ© grêÂ¡tis). Nunca invento nêÂºmero;
"grêÂ¡tis" sêÂ³ quando a pêÂ¡gina diz ou o Nei afirma.

## 3. As 7 etapas ê¢â¬â exemplo real (o reel do hacker)

| Etapa | Fala | Tela |
|---|---|---|
| 1. Gancho (terceiro) | "Um cara foi dormir e acordou com mil e setecentos dêÂ³lares de conta de IAê¢â¬Â¦" | manchete "ACORDOU DEVENDO US$ 1.700" desenhada na capa com a chave partida; cortes de aproximaêÂ§êÂ£o em 1 s e 2 s |
| 2. Medo | "A chave êÂ© a senha que a IA usaê¢â¬Â¦ a sua pode ser a prêÂ³xima. E nêÂ£o êÂ© descuido seu: ninguêÂ©m te avisou" | encapuzado puxando a chave + painel vermelho |
| 3. Desejo | "Imagina dormir sabendo queê¢â¬Â¦ o prejuêÂ­zo tem teto" | homem dormindo + "prejuêÂ­zo com teto" |
| 4. Facilidade | "VocêÂª nêÂ£o precisa ser especialista, nem programador" | painel de limite + "sem ser especialista" |
| 5. Descoberta | "SêÂ£o trêÂªs ajustes: limite, uma chave por uso, alarmeê¢â¬Â¦" | cadeado, chaves e sino + os 3 ajustes entrando |
| 6. BenefêÂ­cio | "O susto vira um aviso no celularê¢â¬Â¦" | fatura rasgada + "sem limite êâ com limite" |
| 7. ComentêÂ¡rio | "Toda semana tem kit novo, grêÂ¡tis, no inema.club. E vocêÂª, jêÂ¡ê¢â¬Â¦?" (comunidade antes, depois a pergunta de verdade, sem pedir link, v1.5.4) | print do inema.club + CTA vermelho em pergunta |

A ordem 2ê¢â¬â6 se adapta ao tema (ex.: no "Quem fatura em 2027" a etapa 3 virou **prova**: "jêÂ¡ aconteceu 3 vezes"),
mas sêÂ£o sempre 7 partes (~30ê¢â¬â37 s de fala + 9 s de cartêÂ£o desde 28/10/2026).

## 4. O que o motor faz

O motor **nêÂ£o cria conteêÂºdo nem imagem**: ele **sincroniza e anima**. êâ° uma pêÂ¡gina web (`motor/mapa.html`) que vira vêÂ­deo.

- **Recebe:**
  - o avatar (HeyGen) e o tempo de cada palavra dele (`r7ex/retempo.py`, Whisper local);
  - as imagens (Codex) e os prints;
  - a `cena.js`, gerada da ficha por `r7ex/cena.py`: qual imagem em qual frase, painêÂ©is, contadores, CTA, cores.
- **Desenha em camadas, quadro a quadro:**
  1. fundo preto (o mapa 3D dos vêÂ­deos de clima fica tapado);
  2. a imagem da vez, com entrada suave e zoom leve;
  3. a faixa do topo (marca + selo vermelho) e a linha de fonte;
  4. o painel, com os itens entrando no segundo da palavra e o contador subindo;
  5. a legenda karaokêÂª;
  6. o CTA em pergunta e a pêÂ­lula do inema.club.
- **Filma** a pêÂ¡gina a 30 quadros por segundo (`motor/render.mjs`, Chrome escondido na tela `:99`).
- **Antes, acerta o ritmo** (`r7ex/ritmo.py` v2, D26 17/11/2026): a fala fica na velocidade natural do HeyGen (sem esticar,
  sem pausa congelada) e o vêÂ­deo segue 9 s depois da êÂºltima palavra, jêÂ¡ sem o rosto (o original fica em
  `avatar/avatar-heygen.mp4`; a decisêÂ£o em `avatar/ritmo.json`). Nesses 9 s o motor encena o comentêÂ¡rio: campo, texto
  digitando, "Publicar", comentêÂ¡rio publicado.
- **Junta** (`motor/compor_avatar.sh`):
  - o rosto na caixinha do canto;
  - a voz a ê¢Ëâ14 LUFS;
  - a trilha baixinha, que abaixa quando vocêÂª fala, some na pausa antes da mêÂ¡xima e continua durante o cartêÂ£o final.

Em uma frase: **o Claude escreve, o Codex desenha, o HeyGen fala e o motor sincroniza tudo com a voz.**

## 5. O que veio de cada lugar

| Do **r7e** (reel7etapas) | Do **eventosextremospub** |
|---|---|
| As 7 etapas de gatilho e a ordem | O motor de render (`mapa.html`, `render.mjs`, `compor_avatar.sh`) |
| O gancho = gatilho com nêÂºmero (D9) | O visual de telejornal: faixa, selo, linha de fonte |
| O plano antes da fala e o CTA fixo do inema.club (D10) | A abertura com o têÂ­tulo desenhado pelo Codex (`abertura-desce`) |
| O avatar do Nei pelo estêÂºdio do HeyGen | A paleta preto + amarelo, vermelho sêÂ³ no perigo |
| Os prints reais das pêÂ¡ginas como prova | Os painêÂ©is com itens no tempo da fala e os contadores |
| A fila e o envio ao bot v3 | A legenda karaokêÂª colorida e o CTA vermelho em pergunta |
| | O `retempo` (dividir o avatar nas falas) |
| TambêÂ©m: a transcriêÂ§êÂ£o Whisper (cêÂ³pia do cardshorts) | |

Tudo isso foi **copiado** para cêÂ¡ (nêÂ£o êÂ© link): `motor/`, `heygen/`, `r7ex/whisper.py`, `r7ex/retempo.py`,
`assets/trilha.mp3`, `bin/enviar_bot_v3.mjs`, `fila/`.

## 6. Como usar

```bash
cd ~/projetos/r7ex
python3 r7ex.py novo <slug>                 # cria edicoes/<data>-<slug>/ficha.yaml a partir do modelo
#   ê¢â â escreva o plano, o gancho (PADRAO êÂ§2.1), a abertura, as 7 partes (fala + imagem/print + painel), o CTA e "publicar"
python3 r7ex.py checar edicoes/<pasta>      # portêÂ£o da ficha (inclui o gancho v1.3.1)
python3 r7ex.py plano edicoes/<pasta>       # crêÂ­tico de viralidade (D15): sem bloqueios, gancho ê¢â°Â¥ 8, mêÂ©dia ê¢â°Â¥ 7,5, nenhuma < 6
#   produto citado ê¢â â `logos:` (logo real, D13); lista no alto (`lista:`), embaixo uma coisa sêÂ³ (`painel.titulo|contador|logo`, D14)
echo 'Nei, <data>: "<frase do OK>"' > edicoes/<pasta>/avatar/APROVADO_HEYGEN   # sêÂ³ com o OK do Nei para esta produêÂ§êÂ£o
python3 r7ex.py fazer edicoes/<pasta>       # imagens + avatar ê¢â â cena ê¢â â render ê¢â â folha de revisêÂ£o
#   (ou --de <avatar.mp4> para reaproveitar um avatar pronto)
# LER edicoes/<pasta>/capa/abertura.png (grafia) e edicoes/<pasta>/build/folha.jpg
python3 r7ex.py enviar edicoes/<pasta>      # bot v3
python3 r7ex.py fila edicoes/<pasta>        # fim da fila do canal (padrêÂ£o lives7)
```

Passo a passo separado: `avatar`, `imagens`, `cena`, `render`, `revisar` (ver `python3 r7ex.py`).

## 7. Como mudar

### Mudar o layout (o que se vêÂª)
| Quero mudar | Onde |
|---|---|
| Cores, fonte, tamanho e posiêÂ§êÂ£o da faixa, painel, legenda, CTA | `motor/mapa.html` (CSS e desenho das camadas) |
| PosiêÂ§êÂ£o e tamanho do rosto, moldura, nome | `motor/compor_avatar.sh` (`LAYOUT=canto`: 400x453 em x 640, y 1290) + `motor/meia_filtro.py` (meia tela 1080x960 em y 960 nos trechos de `avatar/meia.txt`) |
| Quando o rosto fica em meia tela | `r7ex/cena.py` (parte 1 sempre; `avatar: meia` na parte) e `body.mt` em `motor/mapa.html` (o que sobe/some) ê¢â¬â D16 |
| Onde a abertura desce, o cartêÂ£o do print, o brilho do print | `r7ex/pecas.py` (`abertura`, `print_card`) |
| Estilo das imagens (paleta, robêÂ´, sem texto) | `ESTILO` em `r7ex.py` |
| Cores das palavras na legenda | `cores:` na ficha (por reel) |
| Trilha | `assets/trilha.mp3` |
| Ritmo da fala, pausa antes da mêÂ¡xima, duraêÂ§êÂ£o do cartêÂ£o final | `r7ex/ritmo.py` (`ALVO_WPM`, `K_MAX`, `PAUSA`, `CAUDA`); `ritmo.pausa_antes` na ficha; `R7X_SEM_RITMO=1` desliga |
| O gesto de comentar no cartêÂ£o final | `comenta()` em `motor/mapa.html`; texto em `cta.comentario` |

### Mudar a estrutura (quantas partes, o que cada uma tem)
- As partes sêÂ£o a lista `partes:` da ficha. O motor aceita qualquer quantidade. O portêÂ£o `checar` exige 7
  (padrêÂ£o); mude lêÂ¡ se o padrêÂ£o mudar.
- Cada parte pode ter `imagem` (o Codex desenha) **ou** `print` (pêÂ¡gina real), e um `painel`
  (`itens`, `contador`, `borda`).
- O painel entra na palavra `de:` e cada item na sua palavra. Escolha palavras que existem na fala daquela parte.

### Mudar o planejamento (o que se fala)
- `plano:` na ficha (pessoa, quer, gancho, nota, destino) e as regras do êÂ§2.
- As regras fixas estêÂ£o em `PADRAO.md` e no kit `inema-design` (D9, D10, D11). MudanêÂ§a de padrêÂ£o:
  primeiro o kit (`DECISOES.md` + `HISTORICO.md`), depois aqui.

## 8. HeyGen e publicaêÂ§êÂ£o

- **Avatar:** estêÂºdio do HeyGen pela assinatura (`heygen/heygen-studio.mjs`), sempre na tela escondida `:99`.
  Status e download pela leitura da API (exceêÂ§êÂ£o autorizada). Gerar sêÂ³ com `avatar/APROVADO_HEYGEN` daquela produêÂ§êÂ£o.
- **SessêÂ£o do HeyGen caiu** ("nêÂ£o estêÂ¡ logada"): abrir **sêÂ³ a janela de login** na tela do Nei (`:10`); ele entra
  com Google. A sessêÂ£o dura ~30 dias; o aviso vermelho chega no v3 um dia antes (`~/projetos/wifi/heygen-aviso`).
- **PublicaêÂ§êÂ£o:** sempre pela fila (`fila/fila.py`, timer systemd `fila-lives7`, 9 h êÂ s 21 h, 1 a cada 2 h),
  nunca upload direto. Cada publicaêÂ§êÂ£o avisa no v3.
  ExceêÂ§êÂ£o (Nei, 05/11/2026): quando a entrega precisa do link do YouTube (portal, link no têÂ³pico do Telegram), publicar direto com o yt-pubx no canal pedido (mesmo têÂ­tulo e contexto do item) e marcar o item da fila como `feito` com `video_id` e nota `direto`, para nêÂ£o sair duas vezes; aviso no v3 em texto normal (faixa azul sêÂ³ no Metricool). Nos outros casos o portal pode entrar antes e ganhar o link do vêÂ­deo depois.

## LicenêÂ§a
MIT.

---

Projeto  - ARCKHÉe