# Lição 02 — CLAUDE.md: o manual da sua IA

## Objetivos
- Entender o que é um arquivo CLAUDE.md e por que ele existe
- Saber onde colocar e como estruturar um CLAUDE.md
- Criar um CLAUDE.md básico para um projeto real

## Conceito Principal

`CLAUDE.md` é um arquivo de texto que o Claude Code lê automaticamente toda vez que inicia uma sessão. Ele define regras, contexto e personalidade para aquela sessão — sem você precisar repetir as mesmas instruções toda vez.

**Analogia:** É o manual de instruções que a IA lê toda vez que acorda. Sem ele, a IA começa do zero. Com ele, já sabe como você trabalha, quais ferramentas usa e o que esperar.

## Onde Colocar

O Claude lê CLAUDE.md de três lugares (em ordem):

1. `~/.claude/CLAUDE.md` — regras globais (valem para todos os projetos)
2. `./.claude/CLAUDE.md` ou `./CLAUDE.md` — regras do projeto atual
3. Subdiretórios — contexto específico de pastas

Dica: comece com um global e refine por projeto.

## O que Colocar

Um bom CLAUDE.md tem:

```markdown
## Linguagem
Sempre responda em português.

## Stack
- Backend: Node.js com Fastify
- Banco: PostgreSQL
- Testes: Vitest

## Regras
- Nunca use `npm`, sempre `pnpm`
- Commits no padrão conventional commits
- Sem comentários óbvios no código

## Contexto do Projeto
API de agendamentos para clínicas. Multitenancy por schema no PostgreSQL.
```

## O Segredo: Feedback Loop

Aqui vai uma dica que poucos sabem, mesmo entre programadores experientes:

Toda vez que a IA fizer algo errado — ela usou a linguagem errada, esqueceu uma regra, fez algo que você não queria — adicione uma regra no CLAUDE.md pra prevenir que isso aconteça de novo.

Por exemplo:
- A IA respondeu em inglês? Adicione: "Sempre responda em português do Brasil"
- Ela criou um arquivo no lugar errado? Adicione: "Crie arquivos apenas na pasta src/"
- Ela usou npm em vez de pnpm? Adicione: "Use sempre pnpm, nunca npm"

Isso transforma o CLAUDE.md num documento vivo que fica mais inteligente com o tempo. Cada erro vira uma regra que evita erros futuros.

**Analogia:** É como treinar um novo funcionário. No início ele erra bastante, mas a cada correção ele aprende e vai melhorando. O CLAUDE.md é o "caderno de treinamento" da IA.

## Exercício

Crie junto com o Claude Code um `CLAUDE.md` para um projeto hipotético: uma loja virtual com Next.js, Prisma e PostgreSQL. Peça ao Claude para sugerir o que incluir.

**Sugestão de prompt:**
> "Me ajuda a criar um CLAUDE.md para uma loja virtual com Next.js, Prisma e PostgreSQL. Quero que inclua regras de linguagem, stack, e boas práticas do projeto."

## Critérios de Validação

Você concluiu esta lição quando:
- [ ] Entende por que o CLAUDE.md existe e o que ele faz
- [ ] Sabe os três lugares onde ele pode ficar
- [ ] Criou (ou planejou) um CLAUDE.md com pelo menos linguagem, stack e regras
