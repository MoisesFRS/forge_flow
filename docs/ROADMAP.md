# Roadmap
| Etapa | Escopo | Critério de aceite |
| --- | --- | --- |
| M0 | Bootstrap React/Laravel/FastAPI, Compose, PG/Redis, login, CI, contratos | sistema local, lint/testes funcionando |
| M1.1 | Projetos, board exclusivo, colunas, CRUD tasks, RBAC | projetos isolados |
| M1.2 | GitHub App, repositórios, webhooks assinados | repo conectado e eventos idempotentes |
| M1.3 | fila/outbox, run state, SSE, runtime fake | fluxo fake ponta a ponta |
| M1.4 | Jev + OpenRouter + Hermes + sandbox | execução real com orçamento e logs |
| M1.5 | testes, revisor, correções, PR e aprovação | PR validado em repo de teste |
| M1.6 | dashboard global, histórico e custos | evidências e métricas auditáveis |
| M2 | roteador adaptativo, dependências, benchmarks | ganho mensurado |
| M3 | multi-tenant SaaS/billing e escala | isolamento/billing auditados |

## Backlog inicial M0
- [ ] Fixar versões e ferramentas em ADR.
- [ ] Scaffold apps/services, lint/CI/Compose.
- [ ] Migrations e seed de board padrão.
- [ ] Contratos HTTP/eventos e auth interna.
- [ ] Políticas de RBAC e testes cross-tenant.
- [ ] Outbox + mock de provedor e SSE.
