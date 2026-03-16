# Lição 03 — Comandos Customizados

## Objetivos
- Entender o que são comandos customizados e como funcionam
- Saber onde criar e como estruturar um comando
- Criar seu primeiro comando funcional

## Conceito Principal

Comandos customizados são atalhos que você cria para tarefas repetitivas. Você os chama com `/nome-do-comando` dentro do Claude Code, e ele executa as instruções do arquivo correspondente.

**Analogia:** São atalhos personalizados, como macros no Excel. Você grava uma sequência de passos uma vez, e depois é só apertar o botão.

## Como Funcionam

1. Crie um arquivo `.claude/commands/meu-comando.md`
2. Escreva as instruções dentro dele (linguagem natural)
3. No Claude Code, chame com `/meu-comando`

O Claude vai ler o arquivo e executar o que está descrito.

## Estrutura de um Comando

```markdown
# Nome do Comando

Descrição breve do que ele faz.

## Instruções

1. Faça isso
2. Depois faça aquilo
3. Mostre o resultado

## Contexto Extra (opcional)

Qualquer informação que o Claude precisa saber para executar bem.
```

## Casos de Uso Comuns

- `/review` — revisa o código atual e aponta problemas
- `/commit` — cria um commit com mensagem padronizada
- `/test` — roda os testes e resume os resultados
- `/deploy` — checklist de deploy para produção

## Exercício

Crie um comando `/hello` que, quando chamado, cumprimente o usuário pelo nome e conte uma piada de programador.

**Passos:**
1. Crie o arquivo `.claude/commands/hello.md`
2. Escreva as instruções (pode pedir o nome do usuário ou usar um fixo)
3. Teste com `/hello` no Claude Code

**Sugestão de conteúdo para o arquivo:**
> "Cumprimente o usuário com entusiasmo, pergunte como ele está, e conte uma piada curta sobre programação. Seja divertido e informal."

## Critérios de Validação

Você concluiu esta lição quando:
- [ ] O arquivo `.claude/commands/hello.md` existe com instruções claras
- [ ] Ao rodar `/hello`, o Claude executa o comportamento descrito
- [ ] Você entende onde os comandos ficam e como são chamados
