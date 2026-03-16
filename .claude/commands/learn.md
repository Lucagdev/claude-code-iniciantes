IMPORTANT: Always use proper Portuguese (Brasil) accents in all responses (é, ã, ç, ô, etc.). Never write "voce", "nao", "ja" — always "você", "não", "já".

Read `.claude-mentor-state.json` to get the list of completed lessons. If the file doesn't exist, treat `completedLessons` as an empty array and suggest the user run `/start` first.

Display the full lesson menu with status icons. Unlock rules:
- Lesson 1 is always available (🔓 or ✅)
- Each subsequent lesson unlocks only after the previous one is marked complete
- Completed lessons show ✅, available lessons show 🔓, locked lessons show 🔒

### Lessons list:
1. O que é Claude Code?
2. CLAUDE.md — O cérebro
3. Comandos personalizados
4. Skills — Superpoderes
5. Hooks — Automações
6. Agentes — Sua equipe
7. MCP — Conectando ao mundo
8. Juntando tudo

After displaying the menu, ask which lesson the user wants to start or review. Accept a number as input.

## When the user picks a lesson:

Check if it's unlocked. If locked, explain they need to complete the previous lesson first.

If unlocked or completed, load and deliver the lesson. The lesson files are in the `lessons/` directory, named with zero-padded numbers (e.g., `lessons/01-what-is-claude-code.md`, `lessons/02-claude-md.md`, etc.). Read the corresponding file and follow its content to teach the lesson interactively.

After the lesson content is delivered and any exercises are done, ask: "Você quer marcar essa lição como concluída?" If yes, update `.claude-mentor-state.json` — add the lesson number to `completedLessons` if not already there.

Then suggest the next step: next available lesson or `/evolve` if lessons 1-2 are done.

Always communicate with the user in Portuguese (Brasil), with correct accents.
