# Lição 04 — Skills: superpoderes reutilizáveis

## Objetivos
- Entender o que são skills e como diferem de comandos
- Saber quando usar cada um
- Criar uma skill simples e funcional

## Conceito Principal

Skills são arquivos de instrução mais ricos que comandos — eles têm contexto mais profundo, podem receber parâmetros e descrevem comportamentos complexos que o Claude usa como referência.

**Analogia:** Se comandos são atalhos, skills são superpoderes — mais contexto, mais inteligência. Um comando diz "faça X". Uma skill diz "você é especialista em X, sabe estas nuances, e quando chamado, age assim."

## Comandos vs Skills

| Comandos | Skills |
|----------|--------|
| Tarefa pontual | Comportamento contínuo ou especializado |
| Chamado com `/` | Referenciado pelo Claude ou mencionado no contexto |
| Mais curto | Pode ser mais detalhado |
| `.claude/commands/` | `.claude/skills/` ou `~/.claude/skills/` |

## Estrutura de uma Skill

```markdown
# Skill: Formatar Código

## Quando usar
Quando o usuário pedir para limpar, organizar ou formatar código.

## Comportamento
- Identifique a linguagem automaticamente
- Aplique as convenções padrão da linguagem
- Não altere a lógica, apenas a formatação
- Aponte se encontrar code smells óbvios (não corrija sem pedir)

## Exemplos de entrada/saída
[exemplo de código bagunçado → código limpo]
```

## Casos de Uso Comuns

- Skill de revisão de código com checklist específico
- Skill de escrita técnica (tom, formato, nível de detalhe)
- Skill de debug sistemático (hipótese → teste → conclusão)
- Skill de geração de testes com cobertura de edge cases

## Exercício

Crie uma skill chamada `format-code` que instrui o Claude a formatar código mantendo a lógica intacta, aplicando convenções da linguagem detectada automaticamente, e avisando sobre code smells sem corrigir.

**Passos:**
1. Crie `.claude/skills/format-code.md`
2. Descreva o comportamento desejado com clareza
3. Teste: cole um trecho de código desorganizado e mencione a skill

## Critérios de Validação

Você concluiu esta lição quando:
- [ ] A skill `format-code.md` existe com instruções completas
- [ ] Você conseguiu usar a skill para formatar um trecho de código
- [ ] Consegue explicar quando usar skill vs comando
