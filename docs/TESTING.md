# Testes e qualidade
- Unitários: RBAC, versões/transições, resolução de política, normalização Jev, roteamento, orçamento.
- Integração: PostgreSQL real de teste, Redis, outbox, concorrência, webhooks HMAC/idempotência.
- Contratos: OpenAPI/JSON Schema Laravel ⇄ FastAPI, adaptadores Jev/OpenRouter/Hermes com dublês.
- E2E: projeto → Kanban → tarefa → Jev fake → Hermes fake → testes → revisor → PR fake → aprovação.
- Segurança: tenant A não lê B; retries sem duplicar PR; prompt injection não altera política; custo bloqueado; sandbox restrita.
- Qualidade por stack: React TS lint/typecheck/componentes; Laravel Pint/PHPStan/PHPUnit; Python ruff/typecheck/pytest; contracts validate.
- CI padrão **não** usa provedores reais/pagos. Smoke tests externos apenas manualmente/ambiente de teste com limite.
- Critério de MVP: PR funcional num repo de teste, custos e evidências verificáveis, aprovação humana e isolamento validado.
