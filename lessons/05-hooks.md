# Lição 05 — Hooks: automação por eventos

## Objetivos
- Entender o que são hooks e quando eles disparam
- Conhecer os tipos principais de hooks disponíveis
- Criar um hook que mostra uma notificação quando o Claude cria um arquivo

## Conceito Principal

Hooks são comandos que o Claude Code executa automaticamente quando algo acontece. Você define "quando X ocorrer, execute Y" — e isso acontece sempre, sem você precisar lembrar.

**Analogia:** É como o corretor automático do celular. Toda vez que você escreve algo, ele ajusta sozinho — você não precisa apertar nenhum botão. Com hooks, toda vez que o Claude edita um arquivo, ele pode formatar, verificar ou notificar você automaticamente.

## Tipos de Hooks

| Hook | Quando dispara |
|------|---------------|
| `PreToolUse` | Antes do Claude fazer algo (ex: antes de editar um arquivo) |
| `PostToolUse` | Depois que o Claude faz algo (ex: depois de salvar um arquivo) |
| `Notification` | Quando o Claude quer te avisar sobre algo |
| `Stop` | Quando a sessão do Claude encerra |

## Exemplos do Mundo Real

### Exemplo 1 — Auto-formatação após edição (PostToolUse)

Imagine que você tem um time de marketing que cria posts. Toda vez que alguém escreve um post, uma assistente revisa automaticamente o texto antes de publicar. Você não precisa lembrar de pedir — acontece sempre.

Com hooks, toda vez que o Claude editar um arquivo de código, você pode rodar automaticamente uma ferramenta que formata e organiza o código:

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write|Edit",
        "command": "pnpm lint --fix"
      }
    ]
  }
}
```

Isso garante que o código sempre fique organizado, mesmo que o Claude esqueça de formatar.

### Exemplo 2 — Bloqueio na branch principal (PreToolUse)

Imagine que você tem uma pasta chamada "versão final para o cliente". Você não quer que ninguém edite ela por acidente — só a versão aprovada fica lá.

No desenvolvimento de software, existe o mesmo conceito: a **branch main** (ou master) é a versão oficial do projeto. Editar ela diretamente é perigoso.

Com um hook `PreToolUse`, você pode bloquear o Claude de editar arquivos quando estiver nessa branch:

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Write|Edit",
        "command": "if [ \"$(git branch --show-current)\" = 'main' ] || [ \"$(git branch --show-current)\" = 'master' ]; then echo 'ERRO: Voce esta na branch main. Crie uma branch antes de editar.' && exit 1; fi"
      }
    ]
  }
}
```

Se o Claude tentar editar qualquer arquivo enquanto você está na branch `main`, o hook bloqueia a ação e mostra um aviso.

### Exemplo 3 — Scanner de senhas (PreToolUse)

Imagine que você tem um cofre com as senhas do seu negócio — as chaves do seu Instagram, do seu banco, dos seus clientes. Você nunca mostraria esse cofre pra um estagiário, certo?

No Claude Code, existe um arquivo chamado `.env` onde ficam as senhas e credenciais do sistema. Com um hook de segurança, você pode impedir que o Claude acesse esse tipo de arquivo:

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Read|Write|Edit",
        "command": "echo \"$CLAUDE_TOOL_INPUT\" | grep -q '\\.env\\|credentials\\|secrets' && echo 'BLOQUEADO: arquivo sensível detectado' && exit 1 || exit 0"
      }
    ]
  }
}
```

Isso é uma camada extra de segurança — mesmo que o Claude tente ler um arquivo `.env` por engano, o hook impede.

## Onde Ficam os Hooks

Hooks ficam no arquivo `settings.json` do Claude Code. Existem dois lugares:

- **`.claude/settings.json`** — só para o projeto atual
- **`~/.claude/settings.json`** — para todos os seus projetos

## Exercício

Vamos criar um hook que mostra uma mensagem toda vez que o Claude cria ou edita um arquivo.

**O que vamos fazer:**
1. Criar (ou editar) o arquivo `.claude/settings.json`
2. Adicionar um hook `PostToolUse` com um comando simples
3. Pedir ao Claude para criar um arquivo e ver o hook disparar

**A configuração:**

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write",
        "command": "echo 'Arquivo criado/editado!'"
      }
    ]
  }
}
```

**Passos:**
1. Se a pasta `.claude` não existir, crie ela na raiz do projeto
2. Crie o arquivo `.claude/settings.json` com o conteúdo acima
3. Peça ao Claude: "Crie um arquivo chamado `teste-hook.txt` com qualquer texto"
4. Observe a mensagem "Arquivo criado/editado!" aparecer no terminal

**Quer ir além?** Troque o comando por algo mais útil:
```json
"command": "echo 'Claude editou um arquivo em:' $(date '+%H:%M:%S')"
```

Agora ele mostra o horário exato de cada edição — como um log automático.

## Critérios de Validação

Você concluiu esta lição quando:
- [ ] O `.claude/settings.json` tem a configuração do hook
- [ ] Ao pedir ao Claude para criar um arquivo, a mensagem do hook aparece no terminal
- [ ] Você consegue explicar a diferença entre `PreToolUse` (antes) e `PostToolUse` (depois)
- [ ] Você entende por que o Exemplo 2 (bloqueio na main) protege o projeto
