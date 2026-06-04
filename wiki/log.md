# Log de Mudanças

**Summary**: Histórico cronológico de todas as mudanças relevantes no projeto.
**Last updated**: 2026-06-04

---

## 2026-06-04

### Estrutura inicial do projeto
- Repositório criado: https://github.com/luizinhotec/orquestrador-n8n
- Wiki base criada: index, arquitetura, banco, workflows, dashboard
- Infraestrutura validada: postgres-orq, n8n-orq, metabase-orq operacionais
- Campos do projeto definidos: nome, responsavel, data_inicio, prazo, status
- Próximo passo: implementar workflow Fase 1 — Criar Projeto

### Fase 2 — Workflows de Tarefas operacionais
- Criar Tarefa, Listar Tarefas e Mover Tarefa testados e publicados
- Listar retorna nome do projeto via JOIN
- Schema tarefas ajustado: created_at e updated_at adicionados via ALTER TABLE

### Fase 1 — Workflow Criar Projeto operacional
- Workflow importado no N8N e publicado
- Credencial PostgreSQL configurada (postgres-orq)
- Schema real do banco difere do planejado — colunas adicionadas via ALTER TABLE:
  - `projetos`: responsavel, data_inicio, prazo, updated_at, created_at
  - `logs`: entidade, entidade_id, detalhe, created_at
- Teste bem-sucedido: POST /webhook/projeto/criar retornou `{"success":true}`
- Wiki banco.md atualizada com schema real
