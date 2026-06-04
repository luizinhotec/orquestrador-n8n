# Banco de Dados

**Summary**: Schema PostgreSQL do orquestrador, tabelas, colunas e queries padrão.
**Sources**: banco `orquestrador` no container `postgres-orq`
**Last updated**: 2026-06-04

## Conexão

```
Host: postgres-orq (interno Docker) | 185.135.137.113:5433 (externo)
Banco: orquestrador
Usuário: orq
```

## Tabelas

### usuarios
| Coluna | Tipo | Descrição |
|--------|------|-----------|
| id | SERIAL PK | |
| nome | VARCHAR | Nome do membro |
| email | VARCHAR UNIQUE | |
| cargo | VARCHAR | Função na equipe |
| created_at | TIMESTAMP | |

### projetos
| Coluna | Tipo | Descrição |
|--------|------|-----------|
| id | SERIAL PK | |
| nome | VARCHAR | Nome do projeto |
| responsavel | VARCHAR | Responsável |
| data_inicio | DATE | |
| prazo | DATE | Data limite |
| status | VARCHAR | Estado no funil (default: BACKLOG) |
| created_at | TIMESTAMP | |
| updated_at | TIMESTAMP | |

### tarefas
| Coluna | Tipo | Descrição |
|--------|------|-----------|
| id | SERIAL PK | |
| projeto_id | INT FK → projetos.id | |
| titulo | VARCHAR | |
| responsavel | VARCHAR | |
| status | VARCHAR | Estado no funil |
| created_at | TIMESTAMP | |
| updated_at | TIMESTAMP | |

### logs
| Coluna | Tipo | Descrição |
|--------|------|-----------|
| id | SERIAL PK | |
| usuario | VARCHAR | Quem executou |
| acao | VARCHAR | Ex: CRIOU_PROJETO, MOVEU_TAREFA |
| entidade | VARCHAR | Ex: projeto, tarefa |
| entidade_id | INT | ID do registro afetado |
| detalhe | TEXT | JSON com dados antes/depois |
| created_at | TIMESTAMP | |

## Estados do Funil

```
BACKLOG → ANÁLISE → DESENVOLVIMENTO → TESTES → HOMOLOGAÇÃO → PRODUÇÃO → CONCLUÍDO
```

## Links

- [[arquitetura]] — containers e conexão
- [[workflows]] — workflows que escrevem no banco
