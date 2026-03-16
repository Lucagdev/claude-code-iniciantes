# Lição 01 — O que é o Claude Code?

## Objetivos
- Entender o que é o Claude Code e como ele difere de outras IAs de chat
- Saber navegar pelos comandos básicos
- Completar sua primeira interação real no terminal

## Conceito Principal

Claude Code é um assistente de IA que roda **dentro do seu terminal**. Diferente do ChatGPT ou do Claude.ai (que vivem no navegador), o Claude Code tem acesso direto ao seu sistema de arquivos, pode rodar comandos, ler código, criar arquivos e executar tarefas sem que você precise copiar e colar nada.

**Analogia:** É como ter um programador sênior sentado do seu lado no terminal — você pede algo em linguagem natural e ele executa, lê o resultado, corrige o erro, e te avisa quando terminou.

### Claude.ai vs Claude Code

| Claude.ai | Claude Code |
|-----------|-------------|
| Navegador | Terminal |
| Você copia o código | Ele edita o arquivo diretamente |
| Sem acesso ao seu sistema | Lê, cria e executa arquivos |
| Ótimo para conversas | Ótimo para trabalho real |

## Comandos Básicos

Você não precisa aprender sintaxe especial — só digitar naturalmente já funciona. Mas existem alguns comandos úteis:

- `/help` — lista todos os comandos disponíveis
- `/compact` — comprime o histórico da conversa (economiza tokens)
- `/clear` — limpa o contexto e começa uma conversa nova
- `/exit` ou `Ctrl+C` — sai do Claude Code

## Permissões

Porque o Claude Code tem acesso real ao seu computador, ele **pede permissão antes de agir**. Isso é uma proteção — ele não faz nada às escondidas.

Quando você vê uma mensagem assim no terminal:

```
Do you want to proceed?
1. Yes, for this session
2. Yes, always
3. No
```

Isso é o Claude pedindo sua autorização. Veja o que cada opção faz:

- **1 — Aceitar uma vez**: ele faz aquela ação agora, mas vai perguntar de novo na próxima
- **2 — Aceitar sempre**: ele nunca mais pergunta para esse tipo de ação na sessão atual
- **3 — Rejeitar**: ele não faz nada e aguarda outra instrução

**Dica prática:** Para ações comuns como ler e criar arquivos, pode apertar **2** sem medo. É seguro e evita interrupções a cada passo.

## Exercício (em duas partes — vá devagar)

### Parte 1: Criar o arquivo

Peça para o usuário digitar um pedido simples. Exemplo sugerido:
> "Cria um arquivo chamado ola.txt com uma mensagem de boas-vindas criativa pra mim"

Crie o arquivo. Depois **PARE** e explique o que acabou de acontecer:
"Pronto! Acabei de criar um arquivo chamado ola.txt no seu computador. Ele está salvo aqui nessa pasta. Você não precisou abrir nenhum programa, clicar em 'salvar como', nem escolher pasta — eu fiz tudo direto pelo terminal."

Espere o usuário responder antes de continuar. Não vá para a parte 2 automaticamente.

### Parte 2: Abrir o arquivo (o momento "uau")

Depois que o usuário confirmar que entendeu, diga:
"Agora vou fazer algo que vai te surpreender: vou abrir esse arquivo na sua tela, como se você tivesse clicado duas vezes nele."

Então abra com o comando do sistema:
- No **Linux ou WSL**: `xdg-open ola.txt`
- No **macOS**: `open ola.txt`

Depois de abrir, **PARE novamente** e pergunte:
"Apareceu o arquivo na sua tela? Olha lá — a IA criou um arquivo E abriu ele pra você. Tudo isso a partir de uma conversa em português."

Se o arquivo não abriu (pode acontecer em alguns sistemas), normalize: "Isso pode acontecer dependendo da configuração do terminal. O importante é que o arquivo foi criado — você pode abrir ele manualmente na pasta."

**IMPORTANTE:** Não apresse esse momento. É a primeira impressão do usuário com o poder do Claude Code. Deixe ele absorver.

## Critérios de Validação

Você concluiu esta lição quando:
- [ ] O arquivo `ola.txt` foi criado com sucesso
- [ ] O arquivo abriu automaticamente no seu computador
- [ ] Você entendeu a diferença entre Claude Code e Claude.ai
- [ ] Você sabe o que fazer quando o Claude pede permissão
