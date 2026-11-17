# r7ex â€” o reel viral do INEMA

[![r7ex â€” o reel viral do INEMA](guia/assets/banner.jpg)](https://inematds.github.io/r7ex/guia/)

**ðŸ‡§ðŸ‡· [PortuguÃªs](README.md) Â· ðŸ‡ºðŸ‡¸ [English](README.en.md) Â· ðŸ‡ªðŸ‡¸ [EspaÃ±ol](README.es.md)**

## O que Ã©

O r7ex Ã© a linha de produÃ§Ã£o de reels verticais (9:16) do INEMA. VocÃª entrega uma ideia forte, a tese, e ele monta um vÃ­deo de 40 a 50 segundos (30â€“37 s de fala num ritmo calmo + 9 s de cartÃ£o do comentÃ¡rio) com o avatar do Nei falando, imagens geradas pelo Codex e um acabamento de telejornal: tÃ­tulo na abertura, painÃ©is que entram na palavra certa, contador e legenda que acende junto com a fala. O roteiro segue 7 etapas de gatilho, do gancho com nÃºmero atÃ© o pedido de comentÃ¡rio, sempre levando a pessoa ao inema.club. Para usar Ã© preciso Python, Node, o Codex e a assinatura do HeyGen, rodando na mÃ¡quina do INEMA.

## ðŸŽ¬ VÃ­deos sobre o r7ex

Feitos com o prÃ³prio r7ex (19/10/2026):

- [Reel 1 â€” "Meus reels tiveram zero visualizaÃ§Ã£o, 4 lotes atÃ© acertar"](https://inematds.github.io/r7ex/guia/assets/videos/r7ex-divulga.mp4)
- [Reel 2 â€” "O reel de 7 etapas ficou velho, agora tem o r7ex"](https://inematds.github.io/r7ex/guia/assets/videos/r7e-para-r7ex.mp4)

TambÃ©m tocam no guia, seÃ§Ã£o Exemplos.

## ðŸ“– Guia de uso

Guia completo (landing + passo a passo): **https://inematds.github.io/r7ex/guia/**

---

**r7ex = r7e + x.** O **r7e** (reel7etapas) dÃ¡ o **roteiro**: 7 etapas de gatilho, do gancho ao comentÃ¡rio.
O **x** vem do **eventosextremospub**: o **acabamento de telejornal** que viraliza mais.
Objetivo de todo reel: **trazer gente para o inema.club.**

Este repo funciona **sozinho**: tem cÃ³pia prÃ³pria do motor de render, dos scripts do estÃºdio do HeyGen, da transcriÃ§Ã£o,
da trilha, do envio ao bot e da fila de publicaÃ§Ã£o. Mudar algo aqui **nÃ£o afeta** o eventosextremospub, o reel7etapas,
o explicavideos nem o cardshorts.

- PadrÃ£o fixo (a regra curta): [`PADRAO.md`](PADRAO.md)
- Ficha de exemplo (o reel do hacker): [`modelo/ficha.yaml`](modelo/ficha.yaml)

---

## O processo, do inÃ­cio ao fim (12 passos)

ðŸ§  = sessÃ£o com o Nei (gasta tokens) Â· âš™ï¸ = script/timer (zero token) Â· ðŸ¤– = `claude -p` curto (sessÃ£o nova)

**Parte 1: com o Nei, na sessÃ£o**

| # | Passo | Comando / o que acontece | Quem |
|---|---|---|---|
| 1 | Pedido | o Nei diz o tema, o canal e o que citar | Nei |
| 2 | Pesquisa | conferir fatos e fontes (vÃ£o para `plano.fatos` com a origem) + **ganchos de quem fala do tema** (v1.5.4): tÃ­tulos com `yt-dlp --flat-playlist "ytsearch15:<termo>"` e a 1Âª fala (0â€“35 s) pela legenda automÃ¡tica â†’ `gancho.referencias` (3â€“5 `{canal, titulo, abertura, gatilho}`; nÃºmero de terceiro nÃ£o entra no roteiro, sÃ³ serve de rÃ©gua) | ðŸ§  |
| 3 | Ficha | `python3 r7ex.py novo <slug>` + escrever o **gancho** (tipo, manchete do quadro 0, objeto com dano, prova, absolviÃ§Ã£o, entrega â€” v1.3.1; tipo `provocacao` no PADRAO Â§2.2), as 7 partes, a abertura, os painÃ©is e `publicar`. VÃ¡rios temas â†’ um vÃ­deo por tema | ðŸ§  |
| 4 | PortÃ£o da ficha | `python3 r7ex.py checar <pasta>`: 7 partes, objetivo 620 e teto 900 caracteres (D26), print sem repetir, palavras dos painÃ©is na fala, **gancho** (tipo vÃ¡lido, manchete â‰¤ 6 palavras â‰  fala, prova atÃ© ~20 s, absolviÃ§Ã£o; lista reprova); **fecho** (v1.4.4: pergunta + inema ponto club, sem "me pede o link"/"comenta PALAVRA", tambÃ©m em `cta.b`/`cta.comentario`); **avisos** v1.5.4: sem `gancho.referencias` (3â€“5) e sem frase de comunidade antes da pergunta da parte 7 | âš™ï¸ |
| 5 | PortÃ£o viral | `python3 r7ex.py plano <pasta>`: crÃ­tico (`producao/ia.yaml`, etapa `critico_plano`, com trava de cota e reserva) dÃ¡ nota por parte; sem bloqueio, gancho â‰¥ 8, mÃ©dia â‰¥ 7,5; compara o gancho com a melhor `gancho.referencias` e cobra a frase de comunidade na parte 7 (v1.5.4) | ðŸ¤– |
| 6 | Entregar Ã  produÃ§Ã£o | `avatar/APROVADO_HEYGEN` + `python3 producao/producao.py --add <pasta>` | ðŸ§  |
| 7 | Enviar o avatar | o timer `r7ex-producao` manda a fala ao estÃºdio HeyGen (tela :99; todas as pendentes na mesma rodada, sem esperar a anterior ficar pronta â€” 25/10/2026) | âš™ï¸ |

**Parte 2: sem sessÃ£o aberta**

| # | Passo | Comando / o que acontece | Quem |
|---|---|---|---|
| 8 | Esperar o avatar | `r7ex.py avatar-conferir` (HeyGen, sÃ³ leitura) atÃ© "pronto" e baixa. **Minutos a horas** | âš™ï¸ |
| 9 | Montar | `r7ex.py fazer`: Codex desenha a **capa chocante** (com prova `capa/abertura.codex.json`; o render recusa sem ela, D24) e as imagens, prints, tempos das palavras, **ritmo** (`r7ex/ritmo.py`: fala esticada atÃ© ~182 palavras/min, ~0,75 s de silÃªncio antes da mÃ¡xima, cartÃ£o do comentÃ¡rio 9 s depois da Ãºltima palavra com o gesto de comentar â€” 28/10/2026), legenda, render e `build/folha.jpg` | âš™ï¸ |
| 10 | Revisar | revisor (`producao/ia.yaml`, etapa `revisao_visual`) + `producao/revisor.md` lÃª a folha: aprova, aprova com ðŸŸ¥ SUGESTÃƒO ou para com o motivo | ðŸ¤– |
| 11 | Entregar | `r7ex.py enviar` (v3) + `r7ex.py fila` (fila do canal); aviso "Terminei" no v3 | âš™ï¸ |
| 12 | Publicar | o timer da fila sobe 1 a cada 2 h (9 hâ€“21 h) pelo yt-pubx e avisa no v3 | âš™ï¸ |

**Pelo bot, sem sessÃ£o nenhuma (22/10/2026): `/r7ex <tema>` no inemaccbot.** (Desde 05/11/2026 o `/rtex` do bot roda o repo `rtex` e existe o `/rtexjp`; atÃ© entÃ£o o `/rtex` era apelido deste.)

| # | Passo | Comando / o que acontece | Quem |
|---|---|---|---|
| B1 | Pedido | o Nei manda `/r7ex <tema, canal, "agora">` no inemaccbot; o comando jÃ¡ Ã© o OK do avatar | Nei |
| B2 | Ficha + portÃµes | fase `ficha` (`prompts/bot-ficha.md`): passos 2â€“6 acima, canal em `publicar.fila`, "agora" â†’ `FRENTE`, `APROVADO_HEYGEN`, `producao.py --add`; mostra o `BOT-RESUMO.md` no chat | ðŸ¤– |
| B3 | ProduÃ§Ã£o | passos 7â€“11 pelo timer `r7ex-producao`, como sempre | âš™ï¸ |
| B4 | Fim no bot | fase `producao`: `producao/esperar.py <pasta>` espera `na_fila` e mostra o `BOT-FIM.md`; `parado` â†’ falha com o motivo | âš™ï¸ |

DefiniÃ§Ã£o: `flow.json` (prefixo `RX`), ajuda do bot em `HELP.md`. O bot nÃ£o faz upload direto nem tÃ³pico no Telegram:
isso continua pela sessÃ£o + vigia `continua` (abaixo). O `/r7ex` no terminal segue igual.

**Quando o Nei pede algo fora do caminho padrÃ£o** ("publica agora sem fila", "posta no INEMA.DEV", links no inemaytbot),
os passos 8â€“12 vÃ£o pelo vigia **`continua`** do wifi (`~/projetos/wifi/continua`): a sessÃ£o escreve
`<pasta>/CONTINUAR.md` com o que falta, as ordens e as travas, tira a ediÃ§Ã£o da produÃ§Ã£o e registra
`continua.py --add <pasta> --cwd ~/projetos/r7ex --confere "python3 r7ex.py avatar-conferir <pasta>"`. Quando o avatar
fica pronto, o vigia abre uma **sessÃ£o nova** (`claude -p`) que lÃª sÃ³ o bilhete e segue atÃ© o fim. O `--add` avisa no v3
("â³ Fase 1 concluÃ­da", msg N) e a sessÃ£o termina dizendo "pode fechar o terminal, acompanhe pela msg N"; o Terminei/Falhou
da fase 2 chega como resposta a essa mensagem. Detalhes: `~/projetos/wifi/continua/README.md`.
Primeiro uso: `edicoes/2026-10-22-hackers-atacam` (22/10/2026).

---

## 1. Como chegamos aqui (18/10/2026) â€” 4 lotes, o que mudou em cada um

| Lote | ConteÃºdo (o que se fala) | Forma (o que se vÃª) | Resultado |
|---|---|---|---|
| **1. r7e antigo** (deepseek, faxina, opencode, contexto, diga) | Assunto do dia (divulgar guia/repo), pÃºblico de nicho, gancho = **promessa** ("SEU AGENTE OBEDECE E GASTA MENOS"), 7 etapas em ordem fixa, medo fraco e Ã s vezes desarmado na hora | Motor do r7e: foto de banco de imagens desfocada atrÃ¡s do rosto em meia tela, letra Anton com Ã¢mbar apagado | Sem visualizaÃ§Ã£o no TikTok/Instagram |
| **2. r7e "-gatilho"** (os mesmos 5, mesmo avatar) | Fala igual (a voz Ã s vezes contrariava a tela) | SÃ³ o gancho mudou: medo/novidade/provocaÃ§Ã£o com nÃºmero, imagem nÃ­tida dramÃ¡tica, amarelo #FACC15 com contorno | Melhor, mas "ainda padrÃ£o" |
| **3. r7e D10** (5 teses do Nei + hacker refeito; 2 de gestÃ£o) | **Plano antes da fala** (pessoa, o que quer, gancho com nÃºmero, nota, destino no inema.club), **fala nova** com o gatilho primeiro e o alÃ­vio no meio, CTA fixo, prints reais das pÃ¡ginas | Motor do r7e com tarja e diagramas em Pillow | "Ficou padrÃ£o" |
| **4. r7ex** (os mesmos 7, **mesmo avatar e fala do lote 3**) | Nenhum conteÃºdo novo: a fala dividida em 7 blocos, cada um com imagem e painel tirados da prÃ³pria fala | **Motor do eventosextremospub**: tÃ­tulo dentro da arte, preto e dourado, faixa de telejornal, painÃ©is no tempo da fala, contador, karaokÃª, CTA em pergunta | Formato padrÃ£o a partir de agora |

LiÃ§Ã£o: o **conteÃºdo** acertou no lote 3 (teses fortes, gatilho, plano) e a **forma** acertou no lote 4 (motor do eventos).

### Links no YouTube

| O quÃª | Link |
|---|---|
| O de referÃªncia que funcionou (evento extremo, r7e antigo com flagrante + nÃºmero) | https://www.youtube.com/shorts/DfdtX9HbkWg (lives10) |
| Lote 1 â€” Faxina no setup (promessa, sem visualizaÃ§Ã£o) | https://www.youtube.com/shorts/E5Y94BLfuJU (lives4) |
| Lote 1 â€” Camada de contexto (promessa, sem visualizaÃ§Ã£o) | https://www.youtube.com/shorts/XflFkvIl4mw (lives4) |
| Lote 3 â€” DemissÃ£o em massa de gerentes (motor r7e) | https://www.youtube.com/shorts/xpDV5qQe5oE (lives3) |
| Lote 3 â€” FuncionÃ¡rio que nÃ£o Ã© gente (motor r7e) | https://www.youtube.com/shorts/cMhIavjhdh0 (lives3) |
| **Lote 4 / r7ex â€” Hackers roubaram as chaves** | https://youtube.com/shorts/DG30IdeqWcg (lives7) |
| Lote 4 / r7ex â€” os outros 6 | na fila do lives7 (1 a cada 2 h); `python3 fila/fila.py --status` |

## 2. Como o conteÃºdo Ã© formado (o plano)

Antes de escrever uma palavra da fala:

1. **Pessoa:** pÃºblico geral (IA traduzida para o dia a dia), nÃ£o o nicho.
2. **O que ela quer:** ganhar algo, resolver uma dor ou chegar a um desejo.
3. **Gancho:** contrÃ¡rio, perda, estatÃ­stica, terceiro (histÃ³ria de alguÃ©m com nÃºmero), notÃ­cia (desta semana), provocaÃ§Ã£o,
   promessa ou acusaÃ§Ã£o (a dor/desejo da pessoa em "vocÃª", v1.4.4) â€” **com nÃºmero, fato ou dor/desejo** e fonte. Nunca lista ("5 novidadesâ€¦"), "vocÃª sabiaâ€¦" ou "eu fizâ€¦". Um tema por vÃ­deo.
   Regras completas do quadro 0 e dos 3 primeiros segundos: [PADRAO.md Â§2.1](PADRAO.md).
4. **Nota de potencial (0â€“10):** "um desconhecido rolando o feed para aqui?" Abaixo de 8, troque o Ã¢ngulo ou o tema.
5. **Destino:** a pÃ¡gina do inema.club que resolve (vira o print de prova).

Base real: leio a pÃ¡gina do curso/guia antes (nome, quantas aulas, se Ã© grÃ¡tis). Nunca invento nÃºmero;
"grÃ¡tis" sÃ³ quando a pÃ¡gina diz ou o Nei afirma.

## 3. As 7 etapas â€” exemplo real (o reel do hacker)

| Etapa | Fala | Tela |
|---|---|---|
| 1. Gancho (terceiro) | "Um cara foi dormir e acordou com mil e setecentos dÃ³lares de conta de IAâ€¦" | manchete "ACORDOU DEVENDO US$ 1.700" desenhada na capa com a chave partida; cortes de aproximaÃ§Ã£o em 1 s e 2 s |
| 2. Medo | "A chave Ã© a senha que a IA usaâ€¦ a sua pode ser a prÃ³xima. E nÃ£o Ã© descuido seu: ninguÃ©m te avisou" | encapuzado puxando a chave + painel vermelho |
| 3. Desejo | "Imagina dormir sabendo queâ€¦ o prejuÃ­zo tem teto" | homem dormindo + "prejuÃ­zo com teto" |
| 4. Facilidade | "VocÃª nÃ£o precisa ser especialista, nem programador" | painel de limite + "sem ser especialista" |
| 5. Descoberta | "SÃ£o trÃªs ajustes: limite, uma chave por uso, alarmeâ€¦" | cadeado, chaves e sino + os 3 ajustes entrando |
| 6. BenefÃ­cio | "O susto vira um aviso no celularâ€¦" | fatura rasgada + "sem limite Ã— com limite" |
| 7. ComentÃ¡rio | "Toda semana tem kit novo, grÃ¡tis, no inema.club. E vocÃª, jÃ¡â€¦?" (comunidade antes, depois a pergunta de verdade, sem pedir link, v1.5.4) | print do inema.club + CTA vermelho em pergunta |

A ordem 2â€“6 se adapta ao tema (ex.: no "Quem fatura em 2027" a etapa 3 virou **prova**: "jÃ¡ aconteceu 3 vezes"),
mas sÃ£o sempre 7 partes (~30â€“37 s de fala + 9 s de cartÃ£o desde 28/10/2026).

## 4. O que o motor faz

O motor **nÃ£o cria conteÃºdo nem imagem**: ele **sincroniza e anima**. Ã‰ uma pÃ¡gina web (`motor/mapa.html`) que vira vÃ­deo.

- **Recebe:**
  - o avatar (HeyGen) e o tempo de cada palavra dele (`r7ex/retempo.py`, Whisper local);
  - as imagens (Codex) e os prints;
  - a `cena.js`, gerada da ficha por `r7ex/cena.py`: qual imagem em qual frase, painÃ©is, contadores, CTA, cores.
- **Desenha em camadas, quadro a quadro:**
  1. fundo preto (o mapa 3D dos vÃ­deos de clima fica tapado);
  2. a imagem da vez, com entrada suave e zoom leve;
  3. a faixa do topo (marca + selo vermelho) e a linha de fonte;
  4. o painel, com os itens entrando no segundo da palavra e o contador subindo;
  5. a legenda karaokÃª;
  6. o CTA em pergunta e a pÃ­lula do inema.club.
- **Filma** a pÃ¡gina a 30 quadros por segundo (`motor/render.mjs`, Chrome escondido na tela `:99`).
- **Antes, acerta o ritmo** (`r7ex/ritmo.py` v2, D26 17/11/2026): a fala fica na velocidade natural do HeyGen (sem esticar,
  sem pausa congelada) e o vÃ­deo segue 9 s depois da Ãºltima palavra, jÃ¡ sem o rosto (o original fica em
  `avatar/avatar-heygen.mp4`; a decisÃ£o em `avatar/ritmo.json`). Nesses 9 s o motor encena o comentÃ¡rio: campo, texto
  digitando, "Publicar", comentÃ¡rio publicado.
- **Junta** (`motor/compor_avatar.sh`):
  - o rosto na caixinha do canto;
  - a voz a âˆ’14 LUFS;
  - a trilha baixinha, que abaixa quando vocÃª fala, some na pausa antes da mÃ¡xima e continua durante o cartÃ£o final.

Em uma frase: **o Claude escreve, o Codex desenha, o HeyGen fala e o motor sincroniza tudo com a voz.**

## 5. O que veio de cada lugar

| Do **r7e** (reel7etapas) | Do **eventosextremospub** |
|---|---|
| As 7 etapas de gatilho e a ordem | O motor de render (`mapa.html`, `render.mjs`, `compor_avatar.sh`) |
| O gancho = gatilho com nÃºmero (D9) | O visual de telejornal: faixa, selo, linha de fonte |
| O plano antes da fala e o CTA fixo do inema.club (D10) | A abertura com o tÃ­tulo desenhado pelo Codex (`abertura-desce`) |
| O avatar do Nei pelo estÃºdio do HeyGen | A paleta preto + amarelo, vermelho sÃ³ no perigo |
| Os prints reais das pÃ¡ginas como prova | Os painÃ©is com itens no tempo da fala e os contadores |
| A fila e o envio ao bot v3 | A legenda karaokÃª colorida e o CTA vermelho em pergunta |
| | O `retempo` (dividir o avatar nas falas) |
| TambÃ©m: a transcriÃ§Ã£o Whisper (cÃ³pia do cardshorts) | |

Tudo isso foi **copiado** para cÃ¡ (nÃ£o Ã© link): `motor/`, `heygen/`, `r7ex/whisper.py`, `r7ex/retempo.py`,
`assets/trilha.mp3`, `bin/enviar_bot_v3.mjs`, `fila/`.

## 6. Como usar

```bash
cd ~/projetos/r7ex
python3 r7ex.py novo <slug>                 # cria edicoes/<data>-<slug>/ficha.yaml a partir do modelo
#   â†’ escreva o plano, o gancho (PADRAO Â§2.1), a abertura, as 7 partes (fala + imagem/print + painel), o CTA e "publicar"
python3 r7ex.py checar edicoes/<pasta>      # portÃ£o da ficha (inclui o gancho v1.3.1)
python3 r7ex.py plano edicoes/<pasta>       # crÃ­tico de viralidade (D15): sem bloqueios, gancho â‰¥ 8, mÃ©dia â‰¥ 7,5, nenhuma < 6
#   produto citado â†’ `logos:` (logo real, D13); lista no alto (`lista:`), embaixo uma coisa sÃ³ (`painel.titulo|contador|logo`, D14)
echo 'Nei, <data>: "<frase do OK>"' > edicoes/<pasta>/avatar/APROVADO_HEYGEN   # sÃ³ com o OK do Nei para esta produÃ§Ã£o
python3 r7ex.py fazer edicoes/<pasta>       # imagens + avatar â†’ cena â†’ render â†’ folha de revisÃ£o
#   (ou --de <avatar.mp4> para reaproveitar um avatar pronto)
# LER edicoes/<pasta>/capa/abertura.png (grafia) e edicoes/<pasta>/build/folha.jpg
python3 r7ex.py enviar edicoes/<pasta>      # bot v3
python3 r7ex.py fila edicoes/<pasta>        # fim da fila do canal (padrÃ£o lives7)
```

Passo a passo separado: `avatar`, `imagens`, `cena`, `render`, `revisar` (ver `python3 r7ex.py`).

## 7. Como mudar

### Mudar o layout (o que se vÃª)
| Quero mudar | Onde |
|---|---|
| Cores, fonte, tamanho e posiÃ§Ã£o da faixa, painel, legenda, CTA | `motor/mapa.html` (CSS e desenho das camadas) |
| PosiÃ§Ã£o e tamanho do rosto, moldura, nome | `motor/compor_avatar.sh` (`LAYOUT=canto`: 400x453 em x 640, y 1290) + `motor/meia_filtro.py` (meia tela 1080x960 em y 960 nos trechos de `avatar/meia.txt`) |
| Quando o rosto fica em meia tela | `r7ex/cena.py` (parte 1 sempre; `avatar: meia` na parte) e `body.mt` em `motor/mapa.html` (o que sobe/some) â€” D16 |
| Onde a abertura desce, o cartÃ£o do print, o brilho do print | `r7ex/pecas.py` (`abertura`, `print_card`) |
| Estilo das imagens (paleta, robÃ´, sem texto) | `ESTILO` em `r7ex.py` |
| Cores das palavras na legenda | `cores:` na ficha (por reel) |
| Trilha | `assets/trilha.mp3` |
| Ritmo da fala, pausa antes da mÃ¡xima, duraÃ§Ã£o do cartÃ£o final | `r7ex/ritmo.py` (`ALVO_WPM`, `K_MAX`, `PAUSA`, `CAUDA`); `ritmo.pausa_antes` na ficha; `R7X_SEM_RITMO=1` desliga |
| O gesto de comentar no cartÃ£o final | `comenta()` em `motor/mapa.html`; texto em `cta.comentario` |

### Mudar a estrutura (quantas partes, o que cada uma tem)
- As partes sÃ£o a lista `partes:` da ficha. O motor aceita qualquer quantidade. O portÃ£o `checar` exige 7
  (padrÃ£o); mude lÃ¡ se o padrÃ£o mudar.
- Cada parte pode ter `imagem` (o Codex desenha) **ou** `print` (pÃ¡gina real), e um `painel`
  (`itens`, `contador`, `borda`).
- O painel entra na palavra `de:` e cada item na sua palavra. Escolha palavras que existem na fala daquela parte.

### Mudar o planejamento (o que se fala)
- `plano:` na ficha (pessoa, quer, gancho, nota, destino) e as regras do Â§2.
- As regras fixas estÃ£o em `PADRAO.md` e no kit `inema-design` (D9, D10, D11). MudanÃ§a de padrÃ£o:
  primeiro o kit (`DECISOES.md` + `HISTORICO.md`), depois aqui.

## 8. HeyGen e publicaÃ§Ã£o

- **Avatar:** estÃºdio do HeyGen pela assinatura (`heygen/heygen-studio.mjs`), sempre na tela escondida `:99`.
  Status e download pela leitura da API (exceÃ§Ã£o autorizada). Gerar sÃ³ com `avatar/APROVADO_HEYGEN` daquela produÃ§Ã£o.
- **SessÃ£o do HeyGen caiu** ("nÃ£o estÃ¡ logada"): abrir **sÃ³ a janela de login** na tela do Nei (`:10`); ele entra
  com Google. A sessÃ£o dura ~30 dias; o aviso vermelho chega no v3 um dia antes (`~/projetos/wifi/heygen-aviso`).
- **PublicaÃ§Ã£o:** sempre pela fila (`fila/fila.py`, timer systemd `fila-lives7`, 9 h Ã s 21 h, 1 a cada 2 h),
  nunca upload direto. Cada publicaÃ§Ã£o avisa no v3.
  ExceÃ§Ã£o (Nei, 05/11/2026): quando a entrega precisa do link do YouTube (portal, link no tÃ³pico do Telegram), publicar direto com o yt-pubx no canal pedido (mesmo tÃ­tulo e contexto do item) e marcar o item da fila como `feito` com `video_id` e nota `direto`, para nÃ£o sair duas vezes; aviso no v3 em texto normal (faixa azul sÃ³ no Metricool). Nos outros casos o portal pode entrar antes e ganhar o link do vÃ­deo depois.

## LicenÃ§a
MIT.

---

Projeto adaptado da comunidade INEMA TDS - Marca Arckhe