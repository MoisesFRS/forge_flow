# Modelo de dados PostgreSQL (lógico; migrations pendentes)
Todas PKs UUID; audit timestamps; `organization_id` e relações fortes para isolamento.

| Entidade | Campos principais |
| --- | --- |
| organizations, users, memberships | id, slug/nome, user_id, role |
| projects, project_memberships | organization_id, name, slug, settings_version |
| github_installations, repositories | installation_id, project_id, github_repository_id, base_branch |
| boards, board_columns | project_id, label, order, semantic_state, wip_limit |
| tasks, task_dependencies, task_comments | project_id, board_id, column_id, repo_id, title, criteria, status, version |
| runs, run_events | task_id, attempt, requested/actual model, state, idempotency_key, sequence |
| classifications, routing_decisions | provider, rubric_version, score, risk, confidence, selection, justification |
| agent_profiles, configuration_revisions | role, prompt_version, overrides, actor |
| quality_results, reviews, artifacts | stage, command/exit_code, verdict/findings, storage_key |
| pull_requests, approvals | repo_id, number, head_sha, checks, actor, decision |
| usage_records, budget_policies | tokens, cache, provider, USD NUMERIC, hard limits |
| webhook_deliveries, outbox_events, audit_logs | delivery_id, correlation_id, payload redacted, processed_at |

## Integridade
Um board ativo por projeto; task/board/repo devem pertencer ao mesmo projeto; sem dependências circulares; `(task_id, attempt)`, `idempotency_key`, `(run_id, sequence)`, webhook delivery únicos; índice em `(project_id,status)`. Soft-delete onde necessário. Custos em decimal e ledgers imutáveis.
