# Lição 08 — Tudo junto: seu setup ideal

## Objetivos
- Revisar como todos os conceitos se conectam
- Ver um exemplo real de setup completo
- Desenhar o setup do seu próprio projeto

## Revisão dos Conceitos

Você chegou até aqui. Veja como tudo se encaixa:

| Peça | Papel |
|------|-------|
| **Claude Code** | O assistente que vive no terminal |
| **CLAUDE.md** | Define quem ele é e como trabalha no projeto |
| **Comandos** | Atalhos para tarefas repetitivas |
| **Skills** | Comportamentos especializados e reutilizáveis |
| **Hooks** | Automação que dispara em eventos |
| **Agentes** | Trabalhadores isolados para tarefas específicas |
| **MCP** | Conexão com o mundo externo |

## Como Funcionam Juntos

Exemplo: você pede `/deploy` (comando) → o comando instrui o Claude a usar a skill `deployment-checklist` → um hook `PreToolUse` bloqueia se os testes não passaram → um agente Haiku verifica o diff final → MCP do GitHub cria a PR automaticamente.

Cada peça resolve um problema. Juntas, formam um fluxo de trabalho que se autogerencia.

## Boas Práticas

- **CLAUDE.md primeiro**: antes de qualquer coisa, defina o contexto do projeto
- **Comandos para o que repete**: se você digita a mesma instrução mais de 3 vezes, vire um comando
- **Skills para expertise**: quando precisar de comportamento consistente e especializado
- **Hooks para garantias**: o que nunca pode ser esquecido vira hook
- **Agentes para tarefas isoladas**: não polua o contexto principal com trabalho pesado
- **MCP quando precisar do mundo**: banco, navegador, APIs externas

## Padrões Comuns

**Setup mínimo viável:**
```
CLAUDE.md (regras e stack)
.claude/commands/review.md
.claude/commands/commit.md
```

**Setup intermediário:**
```
+ .claude/skills/code-review.md
+ .claude/skills/debug.md
+ hooks de lint automático
```

**Setup avançado:**
```
+ MCP para banco de dados
+ Agentes especializados por domínio
+ Pipeline automatizado de deploy
```

## Exercício Final

Projete o setup completo de Claude Code para um projeto seu (real ou imaginário). Defina:

1. O que vai no `CLAUDE.md` (linguagem, stack, regras)
2. Quais comandos você criaria (liste 3-5)
3. Que skills fariam sentido
4. Quais hooks seriam úteis
5. Se precisaria de MCP — e qual

**Sugestão de prompt:**
> "Vou te descrever meu projeto [descrição]. Me ajuda a desenhar o setup completo de Claude Code para ele — CLAUDE.md, comandos, skills, hooks e MCP se necessário."

## Critérios de Validação

Você concluiu esta lição (e o curso base) quando:
- [ ] Consegue descrever o papel de cada peça sem consultar as lições
- [ ] Tem um plano de setup para um projeto real
- [ ] Sabe por onde começar quando abrir um novo projeto com Claude Code

---

**Próximo passo:** use `/evolve` para receber um desafio personalizado com base no que você aprendeu.
