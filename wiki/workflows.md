# Workflows N8N

**Summary**: Todos os workflows ativos no N8N, seus webhooks e status de implementação.
**Sources**: N8N em http://185.135.137.113:5678, pasta workflows/ no repo
**Last updated**: 2026-06-04

## Convenção de Nomenclatura

- Arquivo JSON: `workflows/<fase>-<nome>.json`
- Webhook path: `/webhook/<entidade>/<acao>`

## Fase 1 — Gestão de Projetos

| Workflow | Webhook | Arquivo | Status |
|----------|---------|---------|--------|
| Criar Projeto | POST /webhook/projeto/criar | workflows/fase1-criar-projeto.json | ✅ Ativo |
| Listar Projetos | GET /webhook/projeto/listar | workflows/fase1-listar-projetos.json | ✅ Ativo |
| Atualizar Status | POST /webhook/projeto/status | workflows/fase1-atualizar-status.json | ✅ Ativo |

## Fase 2 — Gestão de Tarefas

| Workflow | Webhook | Arquivo | Status |
|----------|---------|---------|--------|
| Criar Tarefa | POST /webhook/tarefa/criar | workflows/fase2-criar-tarefa.json | 🔄 Em desenvolvimento |
| Listar Tarefas | GET /webhook/tarefa/listar | — | ⏳ Pendente |
| Mover Tarefa no Funil | POST /webhook/tarefa/mover | — | ⏳ Pendente |

## Fase 3 — Funil Operacional

⏳ Pendente — depende da Fase 2

## Fluxo Padrão de Todo Workflow

```
Webhook Trigger
    ↓
Validar campos obrigatórios
    ↓
Executar ação no PostgreSQL
    ↓
Registrar em logs
    ↓
(Opcional) Notificar responsável
    ↓
Retornar JSON { success, data }
```

## Links

- [[banco]] — tabelas que os workflows escrevem
- [[dashboard]] — como o dashboard chama os webhooks
