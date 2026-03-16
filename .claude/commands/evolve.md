IMPORTANT: Always use proper Portuguese (Brasil) accents in all responses (é, ã, ç, ô, etc.). Never write "voce", "nao", "ja" — always "você", "não", "já".

Read `.claude-mentor-state.json`. Check the `completedLessons` array.

## If lessons 1 and 2 are NOT both completed:

Tell the user (in Portuguese, with correct accents) that to evolve the workspace they should first complete at least lessons 1 and 2, since those cover the foundational concepts (what Claude Code is and how CLAUDE.md works). Suggest running `/learn` to continue.

## If lessons 1 and 2 are completed:

Ask the user: "O que você quer construir?" and offer examples to spark ideas:
- Um site ou landing page
- Uma API ou backend
- Automações e scripts
- Geração de conteúdo (posts, vídeos, etc.)
- Estudos e aprendizado
- Um projeto pessoal específico

Wait for their answer. Based on what they describe, propose a personalized transformation plan. The plan should cover exactly what changes to make to turn this learning environment into their workspace:

1. **CLAUDE.md** — What context to add: their stack, goals, workflow preferences, tools they use
2. **Commands** — Which slash commands would help them (e.g., `/new-post`, `/deploy`, `/test`, `/research`)
3. **Skills** — Any reusable prompt files that would save them time
4. **Agents** — Whether any tasks benefit from isolated agent calls
5. **MCP servers** — Which integrations make sense (e.g., filesystem, browser, GitHub, databases)

Present the full plan clearly. Ask: "Posso executar esse plano?" and wait for confirmation.

## If confirmed:

Execute step by step. For each change:
- Say what you're about to do (one sentence)
- Do it
- Confirm it's done

At the end, tell the user their workspace is ready and briefly explain how to use what was set up.

Always communicate with the user in Portuguese (Brasil), with correct accents.
