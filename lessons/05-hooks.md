# Lição 05 — Hooks: automação por eventos

## Objetivos
- Entender o que são hooks e quando eles disparam
- Conhecer os tipos principais de hooks disponíveis
- Criar um hook que reage a mudanças de arquivo

## Conceito Principal

Hooks são scripts ou comandos que o Claude Code executa automaticamente em resposta a eventos. Você define "quando X acontecer, execute Y" — e o Claude garante que isso sempre ocorra, sem você precisar lembrar.

**Analogia:** São como sensores automáticos — quando algo acontece, eles reagem. É o mesmo princípio dos webhooks em APIs ou dos Git hooks em repositórios.

## Tipos de Hooks

| Hook | Quando dispara |
|------|---------------|
| `PreToolUse` | Antes do Claude usar uma ferramenta (ex: antes de editar arquivo) |
| `PostToolUse` | Depois que uma ferramenta é usada (ex: depois de salvar arquivo) |
| `Notification` | Quando o Claude quer notificar o usuário |
| `Stop` | Quando a sessão do Claude encerra |

## Como Configurar

Hooks ficam no `settings.json` do Claude Code (`.claude/settings.json` ou `~/.claude/settings.json`):

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write",
        "hooks": [
          {
            "type": "command",
            "command": "echo 'Arquivo salvo!' && pnpm lint --fix"
          }
        ]
      }
    ]
  }
}
```

## Casos de Uso Comuns

- Rodar lint automaticamente após salvar arquivos
- Executar testes relacionados após editar um módulo
- Enviar notificação (via ntfy, Slack, etc.) quando o Claude termina uma tarefa longa
- Fazer backup automático antes de edições grandes

## Exercício

Configure um hook `PostToolUse` que roda `echo "Arquivo modificado: {arquivo}"` sempre que o Claude salvar um arquivo. Isso simula um sistema de log de mudanças.

**Passos:**
1. Crie ou edite `.claude/settings.json`
2. Adicione o hook para o evento `Write`
3. Peça ao Claude para criar qualquer arquivo e observe o hook disparar

## Critérios de Validação

Você concluiu esta lição quando:
- [ ] O `settings.json` tem a configuração do hook
- [ ] Ao salvar um arquivo, o comando do hook é executado automaticamente
- [ ] Você consegue explicar a diferença entre PreToolUse e PostToolUse
