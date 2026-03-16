# Lição 07 — MCP: estendendo os sentidos da IA

## Objetivos
- Entender o que é MCP e para que serve
- Conhecer os servidores MCP mais úteis no dia a dia
- Explorar uma configuração MCP real

## Conceito Principal

MCP (Model Context Protocol) é um protocolo que permite conectar o Claude a sistemas externos — navegadores, bancos de dados, APIs, sistemas de arquivos remotos. Sem MCP, o Claude só acessa o que está no seu terminal. Com MCP, ele pode interagir com o mundo.

**Analogia:** MCP é como dar braços extras para a IA — ela pode acessar o navegador, banco de dados, APIs, fazer buscas na internet, ler PDFs, controlar o sistema operacional. Cada servidor MCP é um braço novo.

## Como Funciona

Um servidor MCP é um processo que roda localmente e expõe ferramentas para o Claude usar. O Claude se comunica com ele via protocolo padronizado — você não precisa saber os detalhes técnicos, só configurar.

```json
// .claude/settings.json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/home/usuario"]
    },
    "browser": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-puppeteer"]
    }
  }
}
```

## Servidores MCP Comuns

| Servidor | O que faz |
|----------|-----------|
| `filesystem` | Acesso expandido a arquivos e diretórios |
| `puppeteer` | Controla um navegador (scraping, testes E2E) |
| `postgres` | Consulta direta ao banco de dados |
| `github` | Lê issues, PRs, código do GitHub |
| `fetch` | Busca conteúdo de URLs |
| `memory` | Memória persistente entre sessões |

## Casos de Uso Reais

- Pedir ao Claude para pesquisar documentação online e resumir
- Fazer Claude consultar o banco de dados e gerar um relatório
- Claude abre o navegador, faz login, captura screenshot de um bug
- Integração com Notion, Linear, Slack via MCP

## Exercício

Examine a configuração MCP do seu ambiente atual. Peça ao Claude Code para listar quais servidores MCP estão configurados e o que cada um oferece.

**Sugestão de prompt:**
> "Quais servidores MCP estão configurados no meu ambiente? O que cada um me permite fazer?"

Se não houver nenhum, planeje juntos qual seria mais útil para o seu projeto e como configurá-lo.

## Critérios de Validação

Você concluiu esta lição quando:
- [ ] Entende o que MCP faz e como difere das ferramentas nativas do Claude
- [ ] Sabe onde fica a configuração de servidores MCP
- [ ] Identificou pelo menos um servidor MCP que seria útil para seu trabalho
