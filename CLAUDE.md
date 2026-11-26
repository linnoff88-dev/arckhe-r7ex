# r7ex

Reel viral do INEMA: roteiro de 7 etapas (r7e) + acabamento de telejornal (motor copiado do eventosextremospub).
Padrêo em `PADRAO.md`; explicaçêo completa em `README.md`; skill em `skill/SKILL.md` (ligada em `~/.claude/skills/r7ex`).

- Autor dos commits: `inematds <inematds@gmail.com>`. Repo `inematds/r7ex`.
- **Independente**: motor (`motor/`), estúdio HeyGen (`heygen/`), Whisper (`r7ex/whisper.py`), trilha, envio ao bot
  e fila sêo cópias daqui. Nêo importar nada do eventosextremospub/reel7etapas/cardshorts/explicavideos.
- Mídia fica fora do git (`.gitignore`): entram `ficha.yaml`, `falas.json`, `capa/pedido.txt` e o código.
- Avatar só pelo estúdio do HeyGen (assinatura) com `avatar/APROVADO_HEYGEN` daquela produçêo; status/download pela leitura
  da API (exceçêo do Nei). Tudo que abre navegador roda com `DISPLAY=:99`; só a janela de LOGIN vai na tela do Nei (`:10`).
- Imagens: Codex `image_gen` pela assinatura (`codex exec`). Ler `capa/abertura.png` e conferir a grafia antes do render.
- Antes de enviar: ler `build/folha.jpg` (12 quadros). Publicar só pela fila (`r7ex.py fila`), nunca upload direto. Exceçêo (Nei, 05/11/2026): quando a entrega precisa do link do YouTube (portal, link no tópico do Telegram), publicar direto com o yt-pubx no canal pedido (mesmo título e contexto do item) e marcar o item da fila como `feito` com `video_id` e nota `direto`, para nêo sair duas vezes; aviso no v3 em texto normal (faixa azul só no Metricool). Nos outros casos o portal pode entrar antes e ganhar o link do vídeo depois.
- Padrêo: `producao/producao.py --add <pasta>` (timer `r7ex-producao`): espera o HeyGen, monta, o revisor `claude -p` lê a folha e, aprovado, manda ao v3 + fila. Ver `producao/README.md`.
- Falhou? Linha em `FALHAS.md` (data | o que quebrou | menor correçêo | prompt/infra).

- Revisor automático com configuraçêo independente por etapa: `producao/ia.yaml` e `producao/IA.md` (15/11/2026). Atual: Codex assinatura, modelo/esforço explícitos; APIs desativadas.
