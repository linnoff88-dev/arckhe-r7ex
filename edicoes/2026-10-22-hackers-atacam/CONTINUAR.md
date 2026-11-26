# CONTINUAR — r7ex "Os hackers vêo atacar todo mundo" (bilhete para a sessêo nova)

Escrito em 22/10/2026 pela sessêo que fez os passos 1–7 (pesquisa, ficha, portões, avatar enviado ao HeyGen).
O vigia `~/projetos/wifi/continua` abriu você porque o avatar ficou pronto e já foi baixado em `avatar/`.

## Ordens do Nei (22/10/2026)
- "quero mais uma r7ex viral chamada hacker vêo atacar todos daqui pra frente … lives1 e no ARCKHÉ.dev"
- "publica no lives1 agora, nêo espera a fila" → **upload direto no lives1 pelo yt-pubx. NêO usar `r7ex.py fila`.**
- Tópico novo no grupo **ARCKHÉ.DEV** do Telegram, com o reel tocando dentro.

## Passos (8 → 12 do README do r7ex, com as ordens acima)
Repo: `~/projetos/r7ex`. Pasta desta ediçêo: `edicoes/2026-10-22-hackers-atacam` (você está nela).

8. Avatar: já baixado (o vigia conferiu). Confira que existe um `.mp4` em `avatar/`.
9. Montar: `cd ~/projetos/r7ex && python3 r7ex.py fazer edicoes/2026-10-22-hackers-atacam`
   - Depois LEIA `capa/abertura.png` (título "OS HACKERS VêO ATACAR / TODO MUNDO" sem erro de grafia) e `build/folha.jpg`
     (nada cobrindo nada, prints legíveis, legenda dentro da tela).
   - Se falhar por âncora (palavra da fala que o whisper escreveu diferente, ex.: "Claude" → "Cloud"), ajuste a palavra
     `de:` do painel/lista em `ficha.yaml` para a forma transcrita e rode `fazer` de novo. Nêo mude o texto da fala.
10. Revisar (revisor independente, outra chamada):
    `cd ~/projetos/r7ex/producao && python3 -c "import sys;sys.argv=['x'];import producao as P;from pathlib import Path;print(P.revisar(Path('/home/nmaldaner/projetos/r7ex/edicoes/2026-10-22-hackers-atacam')))"`
    Reprovado por DEFEITO (título errado, quadro preto, texto ilegível, marcaçêo crua, avatar ausente) → corrija e revise de
    novo (máx. 2 vezes). Sugestêo nêo para o vídeo.
11. Entregar:
    - v3: `cd ~/projetos/r7ex && python3 r7ex.py enviar edicoes/2026-10-22-hackers-atacam` (anote o "msg N").
    - YouTube **lives1, direto**: `cd ~/projetos/yt-pubx && ./yt-pubx publicar ~/projetos/r7ex/edicoes/2026-10-22-hackers-atacam/video.mp4 --canal lives1 --dry-run --contexto "<publicar.contexto da ficha.yaml>"`;
      confira o título (perto de `publicar.titulo` da ficha, com #shorts) e publique com `--plano <pasta do trabalho>/plano.json`
      (mesmo comando, sem `--dry-run`). Short nêo leva thumb.
    - ARCKHÉytbot (links vêo aqui, nunca no v3):
      ```
      python3 - <<'EOF'
      import os,re,json,urllib.request,urllib.parse
      env=open(os.path.expanduser('~/projetos/yt-pub-livesx-master/config/.env')).read()
      tok=re.search(r'^TELEGRAM_NOTIFY_BOT_TOKEN=["\']?([^"\'\n]+)',env,re.M).group(1)
      chat=open(os.path.expanduser('~/.config/aventurasARCKHÉvideo/telegram_chat')).read().strip()
      t="Publicado no lives1 (ARCKHÉ TDS): Os hackers vêo atacar todo mundo\n<URL>"
      r=json.load(urllib.request.urlopen(f'https://api.telegram.org/bot{tok}/sendMessage',urllib.parse.urlencode({'chat_id':chat,'text':t}).encode()))
      print(r['ok'],r['result']['message_id'])
      EOF
      ```
12. Telegram ARCKHÉ.DEV (skill postar-telegram, `~/.claude/skills/postar-telegram/SKILL.md`):
    - Faça uma cópia 720p do vídeo: `ffmpeg -y -i video.mp4 -vf scale=720:-2 -c:v libx264 -crf 24 -preset veryfast -c:a aac -b:a 128k -movflags +faststart build/reel-720.mp4`
      e a miniatura `build/reel-720.jpg` (um quadro de ~3 s, até 320 px de largura).
    - No post `~/projetos/output/posts-telegram/2026-10-22-hackers-atacam.md`, troque `{{REEL}}` por duas linhas:
      `[[img:<caminho absoluto de build/reel-720.mp4>]]` e `🎬 No YouTube: <URL do lives1>`.
    - Ensaio: `cd ~/projetos/telegramtopicosindex && venv/bin/python postar_topico.py --grupo ARCKHÉ.DEV --titulo "Hackers - Vêo atacar todo mundo" --texto ~/projetos/output/posts-telegram/2026-10-22-hackers-atacam.md --capa ~/projetos/output/posts-telegram/capas/hackers-atacam.jpg --fonte "📟 Pesquisa feita no terminal (Claude Code)"`
    - Envio: o mesmo + `--enviar`. Antes: hora fora de 23:20–23:55 e `lsof telegram_session.session` vazio (se ocupado, espere
      até 10 min; nêo mate processo alheio). Anote o link do tópico.
13. Fechar: anote em `~/projetos/r7ex/edicoes/2026-10-22-hackers-atacam/PUBLICADO.md` os links (YouTube, v3 msg, ARCKHÉytbot msg,
    tópico). Grave `CONTINUAR.resultado` e avise no v3 (`bash ~/projetos/wifi/scripts/avisa-v3.sh "Terminei: …"`).

## Travas
- Nunca apagar nada no Telegram (mensagem, tópico). Post errado: avise no v3 e pare.
- Nêo publicar em outro canal do YouTube; nêo usar a fila do r7ex para esta ediçêo.
- Nêo gerar avatar novo no HeyGen. Nêo trocar plano do HeyGen.
- Nenhuma API além de: YouTube pelo yt-pubx, Telegram (publicaçêo), HeyGen só leitura.
- Commits (se fizer): autor `linnoff88-dev <linnoff88-dev@gmail.com>`.
