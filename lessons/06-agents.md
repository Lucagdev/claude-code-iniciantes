# Lição 06 — Agentes: especialistas sob demanda

## Objetivos
- Entender o que são sub-agentes e por que contexto isolado importa
- Saber escolher o modelo certo para cada tipo de tarefa
- Criar um agente real de revisão de código em `.claude/agents/`

## Conceito Principal

Imagina que você tem uma equipe: um designer, um redator, um analista de dados. Cada um é especialista em uma coisa. Você não pede pro designer analisar dados — você usa cada um no que sabe melhor.

**Agentes no Claude Code funcionam igual** — você pode criar "funcionários virtuais" com funções específicas. Em vez de jogar tudo numa conversa só (que fica cara e lenta), você delega tarefas para agentes que começam frescos, fazem o trabalho, e retornam o resultado.

## Contexto Isolado

Cada agente recebe **apenas o que precisa** — não o histórico inteiro da conversa. Isso é o "contexto isolado".

Por que isso importa:
- Menos tokens = mais barato e mais rápido
- Agente focado comete menos erros por distração
- Você pode rodar vários agentes ao mesmo tempo
- Os resultados são mais precisos quando o escopo é claro

**Exemplo prático:** Se você quer revisar o arquivo `auth.ts`, o agente revisor recebe só esse arquivo — não a conversa inteira, não outros arquivos, não o histórico. Só o que importa.

## Escolhendo o Modelo

Pense assim: você não chama o diretor da empresa pra formatar uma planilha. Você usa quem é certo pra cada tarefa.

| Modelo | Analogia | Quando usar |
|--------|----------|-------------|
| **Haiku** | O estagiário eficiente | Tarefas mecânicas: buscar texto, formatar código, listar arquivos, rodar lint |
| **Sonnet** | O analista sênior | Tarefas que precisam de julgamento: escrever código, revisar, pesquisar, implementar |
| **Opus** | O diretor | Tarefas complexas: planejar, decidir arquitetura, orquestrar outros agentes |

Regra prática: use o modelo mais barato que consegue fazer o trabalho bem. Haiku é muito mais rápido e barato que Opus — use-o sempre que possível.

## Como os Agentes São Invocados

Agentes no Claude Code ficam em `.claude/agents/`. O próprio Claude decide quando acionar um agente (via ferramenta Agent), ou você pode pedir explicitamente:

> "Delega a revisão do arquivo `src/auth.ts` para um agente revisor."

O Claude lê o arquivo do agente em `.claude/agents/`, cria uma instância com contexto limpo, passa só o que é necessário, e traz o resultado de volta pra você.

## Exercício

Crie um agente revisor de código chamado `revisor`. O arquivo vai em `.claude/agents/revisor.md`.

**Formato do arquivo de agente:**

```markdown
---
name: revisor
description: Revisa arquivos de código buscando problemas de qualidade
---

Você é um revisor de código especializado. Quando acionado:
1. Leia os arquivos modificados
2. Verifique: erros de lógica, código duplicado, nomes confusos
3. Dê feedback construtivo em português do Brasil
4. Classifique os problemas: crítico, aviso, sugestão
```

**Passos:**
1. Crie a pasta `.claude/agents/` se não existir
2. Crie `.claude/agents/revisor.md` com o conteúdo acima
3. Peça ao Claude: "Use o agente revisor no arquivo [algum arquivo do seu projeto]"
4. Observe o feedback estruturado que o agente retorna

## Critérios de Validação

Você concluiu esta lição quando:
- [ ] O arquivo `.claude/agents/revisor.md` existe com o frontmatter `name` e `description` corretos
- [ ] Você invocou o agente num arquivo real e recebeu feedback classificado (crítico / aviso / sugestão)
- [ ] Consegue explicar a diferença entre Haiku, Sonnet e Opus com suas próprias palavras
- [ ] Entende o que é "contexto isolado" e por que ele economiza tokens
