# Lição 09 — Construa e Publique: do Zero à Internet

## Objetivos
- Criar um projeto real do zero com o Claude Code
- Aprender o básico de Git e GitHub na prática
- Publicar o projeto na internet usando GitHub Pages
- Ter um link pra mostrar pra amigos e família

## Pré-requisito
- Ter completado pelo menos as lições 1 e 2

---

## Parte 1: Git — Salvando seu trabalho

### O que é o Git?

O Git é como um "histórico de versões" do seu projeto. Sabe quando você salva um documento como "trabalho_final_v2_corrigido_ESSE_SIM.docx"? O Git resolve isso — ele guarda cada versão automaticamente, e você pode voltar a qualquer uma delas.

### Conceitos essenciais (só 3)

- **Repositório (repo)** — é a pasta do seu projeto, mas com superpoderes. O Git guarda o histórico dentro dela
- **Commit** — é como tirar uma "foto" do projeto naquele momento. Cada foto tem uma descrição do que mudou
- **Push** — é enviar essas "fotos" pro GitHub (a nuvem), pra ficar salvo online

### Exercício: Primeiros comandos Git

Ensine o usuário a:
1. `git init` — "Isso transforma sua pasta num repositório Git. É como ativar o modo 'histórico' na pasta"
2. `git add .` — "Isso seleciona todos os arquivos pra próxima foto. É como escolher quais documentos guardar"
3. `git commit -m "primeiro commit"` — "Isso tira a foto e coloca uma legenda. Agora seu trabalho está salvo"

**Importante:** antes de rodar cada comando, explique o que ele faz e peça permissão. Mostre o resultado e explique o que aconteceu.

---

## Parte 2: GitHub — Sua vitrine na internet

### O que é o GitHub?

O GitHub é como um Google Drive pra código. Você guarda seus projetos lá, e outras pessoas podem ver. Muitos programadores usam o GitHub como portfólio — é o "LinkedIn dos desenvolvedores".

### Criar conta no GitHub

Guie o usuário passo a passo:
1. Acesse https://github.com
2. Clique em "Sign up"
3. Crie com e-mail e senha
4. Escolha um username (esse vai aparecer no link do site!)
5. Confirme o e-mail

**Dica pro usuário:** "Escolha um username profissional — ele vai aparecer no endereço do seu site: seunome.github.io"

### Configurar Git no computador

Configure o Git automaticamente usando o nome do state file:
```
git config --global user.name "NOME_DO_STATE"
```
Depois pergunte APENAS o e-mail: "Qual o e-mail que você quer usar no GitHub? (pode ser qualquer um)"

```
git config --global user.email "EMAIL_DO_USUARIO"
```

**Explique:** "Configurei o Git com seu nome e e-mail. Toda vez que você salvar uma versão do projeto, ele marca com sua assinatura — como um carimbo."

### Criar conta no GitHub (se ainda não tiver)

Pergunte: "Você já tem conta no GitHub?" Se não:
1. Abra o navegador pro usuário: `xdg-open https://github.com/signup` (Linux) ou `open https://github.com/signup` (macOS)
2. Guie passo a passo: "Na tela que abriu, coloque seu e-mail, crie uma senha, e escolha um nome de usuário"
3. **Dica importante:** "O nome de usuário vai aparecer no endereço do seu site — escolha algo profissional como seunome ou seunome-dev"
4. Diga: "Quando terminar de criar a conta, me avisa aqui que eu continuo"
5. Depois: "Agora abre seu e-mail e clica no link de confirmação do GitHub"

### Autenticar com GitHub (o Mentor faz quase tudo)

1. Instale o `gh` CLI automaticamente (explique: "Vou instalar uma ferramenta que conecta seu terminal ao GitHub")
2. Rode `gh auth login -h github.com -p https -w`
3. **Explique cada passo do fluxo interativo para o usuário:**
   - "Ele vai mostrar um código na tela. Copia esse código"
   - "Vai abrir uma página no navegador. Cola o código lá e clica em 'Authorize'"
   - "Quando aparecer 'Authentication complete', pode voltar aqui"
4. Verifique se deu certo com `gh auth status`
5. Se falhar, resolva o problema sem mostrar erros técnicos

---

## Parte 3: Criar o projeto (o Mentor constrói, o usuário decide)

### Pergunte o que construir

"Agora a parte mais legal: vamos criar o seu projeto! O que você prefere?"
- **Portfólio pessoal** — "Página com seu nome, sobre você, seus trabalhos e um jeito de te contatar"
- **Link na bio** — "Tipo Linktree — uma página bonita com todos os seus links organizados"
- **Landing page** — "Página de um produto ou serviço que você quer promover"
- **Currículo online** — "Versão web do seu currículo, acessível por qualquer celular"

### O Mentor constrói TUDO

Depois que o usuário escolher, pergunte as informações pessoais necessárias:
- Nome completo, bio curta, links de redes sociais
- Cores preferidas (ou sugira um esquema bonito)
- Foto (pode ser um link de uma foto online)

**Então CONSTRUA o projeto inteiro:**
1. Crie TODOS os arquivos (HTML, CSS, imagens) — o usuário NÃO precisa escrever código
2. Use HTML + CSS puro (sem frameworks, sem npm, sem build) — isso funciona direto no GitHub Pages
3. Faça um design bonito e moderno com CSS (gradientes, fontes do Google Fonts, responsivo)
4. **A cada arquivo criado**, explique em uma frase: "Criei o index.html — é a página principal do seu site"
5. Faça commits automaticamente — o usuário não precisa saber os comandos
6. Personalize com as informações que o usuário deu

**IMPORTANTE:** use APENAS HTML + CSS puro. Nada de Node.js, npm, React, frameworks. Motivo:
- Funciona direto no GitHub Pages sem build
- Zero instalações extras no computador do usuário
- Não complica com ferramentas que o leigo não precisa
- O resultado é o mesmo: um site bonito e funcional

---

## Parte 4: Publicar na internet (Deploy)

### O que é GitHub Pages?

"O GitHub Pages é um serviço gratuito que transforma seu repositório num site de verdade. Você sobe o código, e o GitHub cria um endereço pra qualquer pessoa acessar. Seu site fica em: seunome.github.io/nome-do-projeto."

### Passo a passo (o Mentor faz tudo, o usuário só assiste e aprende)

Diga: "Agora vou publicar seu site na internet. Vou fazer tudo — só preciso que você aceite as permissões quando aparecerem."

1. Crie o repositório no GitHub automaticamente:
   ```
   gh repo create nome-do-projeto --public --source . --push
   ```
   **Explique depois de fazer:** "Pronto! Criei um espaço no GitHub pro seu projeto e enviei todos os arquivos. Qualquer pessoa pode ver o código agora."

2. Ative o GitHub Pages automaticamente:
   ```
   gh api repos/USUARIO/REPO/pages -X POST -f source.branch=main -f source.path=/
   ```
   Ou guie pelo navegador: Settings → Pages → Source → main → Save

3. Aguardar 1-2 minutos e acessar o link

### O momento mágico

Quando o site estiver no ar, diga algo como:
"Pronto! Seu site está ao vivo em https://seunome.github.io/nome-do-projeto. Qualquer pessoa no mundo pode acessar esse link agora — manda pra um amigo e vê a reação!"

---

## Parte 5: Próximos passos

Depois do deploy, sugira:
- "Quer personalizar mais? Podemos mudar cores, adicionar fotos, melhorar o layout"
- "Quer um domínio próprio? (seunome.com) — posso te explicar como configurar"
- "Quer adicionar mais páginas ou funcionalidades?"

---

## Critérios de Validação

Você concluiu esta lição quando:
- [ ] Entendeu o que é Git, commit e push
- [ ] Tem uma conta no GitHub
- [ ] Criou um projeto e fez pelo menos 1 commit
- [ ] O projeto está publicado e acessível por um link
- [ ] Mandou o link pra alguém e a pessoa conseguiu abrir
