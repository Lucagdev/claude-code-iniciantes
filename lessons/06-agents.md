# Lição 06 — Agentes: especialistas sob demanda

## Objetivos
- Entender o que são sub-agentes e por que contexto isolado importa
- Saber escolher o modelo certo para cada tipo de tarefa
- Criar e invocar um agente simples de revisão de código

## Conceito Principal

Sub-agentes são instâncias do Claude invocadas com um contexto limpo e focado. Em vez de acumular tudo numa conversa só (que fica cara e lenta), você delega tarefas específicas para agentes que começam frescos, fazem o trabalho, e retornam o resultado.

**Analogia:** É como ter uma equipe de especialistas — cada um faz o que sabe melhor, sem precisar saber tudo que os outros fazem. O arquiteto planeja, o desenvolvedor implementa, o QA testa — cada um com seu contexto.

## Por que Contexto Isolado Importa

- Menos tokens = mais barato e mais rápido
- Agente focado comete menos erros por distração
- Resultados são mais precisos quando o escopo é claro
- Você pode rodar múltiplos agentes em paralelo

## Escolhendo o Modelo

| Modelo | Quando usar |
|--------|-------------|
| **Haiku** | Tarefas mecânicas: lint, busca, formatação, checklists |
| **Sonnet** | Implementação, pesquisa, arquitetura, decisões com julgamento |
| **Opus** | Planejamento, orquestração, revisão final, decisões críticas |

Regra prática: use o modelo mais barato que consegue fazer o trabalho bem.

## Como Invocar um Agente

No Claude Code, você pode criar um agente via comando ou referenciando uma skill de agente:

```
Use the Agent tool to: revise o arquivo src/auth.ts e liste problemas de segurança.
Use model: claude-haiku-4-5
Context: apenas o conteúdo do arquivo, sem histórico da conversa.
```

## Exercício

Crie uma skill chamada `code-review` que define um agente revisor de código. O agente deve:
- Receber apenas o arquivo a ser revisado
- Listar problemas por categoria (segurança, performance, legibilidade)
- Usar modelo Haiku (é suficiente para revisão simples)

**Passos:**
1. Crie `.claude/skills/code-review.md` com as instruções do agente
2. Peça ao Claude para usar a skill num arquivo real do seu projeto
3. Compare a revisão com o que você esperaria de um colega

## Critérios de Validação

Você concluiu esta lição quando:
- [ ] A skill `code-review.md` descreve claramente o comportamento do agente
- [ ] Você invocou o agente num arquivo real e recebeu feedback estruturado
- [ ] Entende quando usar Haiku vs Sonnet vs Opus
