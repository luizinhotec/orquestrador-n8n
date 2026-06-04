# CLAUDE.md

Wiki interna do projeto para uso por agentes Claude (Code, Agent SDK ou API).
Esta wiki é a fonte canônica para navegar e entender o código. **Leia primeiro `wiki/index.md`** antes de abrir arquivos avulsos.

## Estrutura do Projeto

```
CLAUDE.md            ← você está aqui (entrypoint)
wiki/
  index.md           ← índice geral, sempre comece aqui
  log.md             ← histórico de mudanças relevantes
  arquitetura.md     ← stack, infraestrutura, containers
  banco.md           ← schema PostgreSQL e queries padrão
  workflows.md       ← workflows N8N e seus webhooks
  dashboard.md       ← frontend e rotas do dashboard
workflows/           ← JSONs exportados do N8N (importáveis)
raw/                 ← dumps, referências externas
```

## Como navegar

1. Abra `wiki/index.md` para mapa completo das páginas
2. Cada página segue o formato:
   - **Summary** — o que a página cobre em 2-3 frases
   - **Sources** — caminhos de arquivo reais que a página descreve
   - **Last updated** — data ISO da última revisão
3. Wiki-links usam sintaxe `[[nome-da-pagina]]`

## Como manter (OBRIGATÓRIO)

- Ao alterar qualquer coisa, **atualize a página wiki correspondente E o `wiki/log.md`** no mesmo commit
- Páginas devem permanecer curtas (≤ 200 linhas)
- Nunca duplique conteúdo entre páginas — linke
- Workflows exportados do N8N ficam em `workflows/` com nome descritivo

## Infraestrutura

- **VPS**: Contabo — 185.135.137.113
- **N8N**: http://185.135.137.113:5678
- **Metabase**: http://185.135.137.113:3000
- **Banco**: postgres-orq → banco `orquestrador`, usuário `orq`

## Convenções

- **Idioma**: pt-BR para wiki e mensagens; inglês para nomes de variável/função
- **Agent model**: Claude Haiku (barato) para tarefas rotineiras; Sonnet para decisões complexas
- **Padrão de aprovação**: agente sugere → responsável aprova → sistema executa
- **Commits**: mensagem em pt-BR, prefixo `feat:` / `fix:` / `docs:` / `workflow:`

Comece em `wiki/index.md`.
