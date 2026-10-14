# API v1 proposta (ainda não implementada)
Pública Laravel `/api/v1`: JSON, UUID, UTC ISO8601, RBAC e `X-Request-ID`; contratos formais em `packages/contracts`. FastAPI interno somente via identidade de serviço.

| Método | Rota | Descrição |
| --- | --- | --- |
| GET/POST | /projects | listar/criar projeto |
| GET/PATCH | /projects/{projectId} | detalhe/config |
| GET/POST | /projects/{projectId}/repositories | integrar GitHub |
| GET/PATCH | /projects/{projectId}/board | quadro/colunas |
| POST/PATCH/DELETE | /projects/{projectId}/board/columns | colunas |
| GET/POST | /projects/{projectId}/tasks | cards |
| GET/PATCH | /tasks/{taskId} | dados da tarefa |
| POST | /tasks/{taskId}/move | trocar coluna com version guard |
| POST | /tasks/{taskId}/analyze | classificar tarefa |
| POST | /tasks/{taskId}/runs | solicitar run; idempotência |
| GET | /runs/{runId} | estado, preço e artefatos |
| GET | /runs/{runId}/events | SSE com replay |
| POST | /runs/{runId}/cancel | cancelar |
| POST | /runs/{runId}/steer | intervenção auditável |
| POST | /tasks/{taskId}/approvals | aprovar/rejeitar |
| GET | /models | catálogo/allowlist |
| GET | /dashboard | métricas autorizadas |
| POST | /webhooks/github | verificar assinatura e delivery id |

Exemplo: `POST /tasks/{id}/runs` com `Idempotency-Key` e `If-Match` e corpo:
```json
{"mode":"autonomous_pr","routing":"automatic","max_cost_usd":"5.00","require_human_approval":true}
```
Retornar 202 com `run_id`; 403 acesso; 409 versão/idempotência; 422 política; 429 rate limit. SSE inclui `event_id`, `sequence`, `type`, `project_id`, `task_id`, `run_id`, `occurred_at`, payload redigido. GitHub webhook só atualiza PR/CI do SHA esperado.
