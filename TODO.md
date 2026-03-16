# Claude Mentor — Melhorias Mapeadas

## Bugs / Ajustes Urgentes

- [ ] **JSON sendo lido toda vez**: o Claude lê `.claude-mentor-state.json` a cada interação mesmo já estando no contexto. Instruir no CLAUDE.md pra ler só no início da sessão ou quando um comando explicitamente pedir
- [ ] **Explicar permissões do Claude Code**: na lição 1 ou no /start, ensinar que o Claude Code pede permissão pra agir (ler, escrever, executar) e que: `1` = aceita uma vez, `2` = aceita sempre aquele tipo de ação. Isso é fundamental pro leigo não travar na primeira interação
- [ ] **Exercício da lição 1 precisa de "UAU"**: em vez de "ler o arquivo de volta", abrir o arquivo no PC do usuário com `xdg-open` (Linux), `open` (macOS) ou `code` (VS Code). Primeira impressão tem que ser impactante — "a IA criou um arquivo E abriu ele pra mim!"

## Melhorias de UX

- [ ] **Lição 0 implícita**: antes da lição 1, o /start deveria explicar brevemente como funciona a interação (digitar texto, apertar Enter, aceitar permissões). Muita gente nunca viu um terminal
- [ ] **Progresso visual mais rico**: mostrar barra de progresso, não só "1/8"
- [ ] **Dicas contextuais**: quando o Claude faz uma ação (Write, Read), explicar o que aquele "badge" significa na primeira vez que aparece
- [ ] **Rate limit**: adicionar detecção/explicação quando o usuário bater no limite

## Conteúdo

- [ ] **Lições em outros idiomas**: inglês como prioridade
- [ ] **Templates de /evolve**: pré-configurações pra nichos (blog, API, automação, marketing)
- [ ] **Lição bônus**: como economizar tokens (usar /compact, escolher modelo certo, etc.)

## Infraestrutura

- [ ] **CONTRIBUTING.md**: guia pra contribuidores
- [ ] **GitHub Issues como backlog**: migrar esses TODOs pra issues
- [ ] **CI**: validar que os .md files têm acentuação correta
- [ ] **Screenshots no README**: adicionar após validação do fluxo
