# Telemetria, custos e auditoria
Propagar `correlation_id`, `organization_id`, `project_id`, `task_id`, `run_id`, `attempt`, `hermes_run_id`, `github_delivery_id`, `pr_number`.

## Eventos
`task.created`, `analysis.started/completed`, `route.selected`, `run.queued/running/failed/completed`, `review.completed`, `pr.created`, `approval.recorded`, `budget.exceeded`.

## Métricas
Runs por minuto/projeto, tempo por estado, success/retry, latência de terceiros, custo estimado/real, tokens cache, modelo solicitado vs. usado, PRs aceitos e retrabalho. Custo USD em decimal; deduplicar registros e preservar snapshots de preço.

## Logs
JSON estruturado, redigido, retenção definida, sem credenciais/código privado cru. Dashboards respeitam RBAC. Artefatos em storage protegido com expiração.
