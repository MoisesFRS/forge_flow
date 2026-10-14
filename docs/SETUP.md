# Setup — plano de ambiente (ainda não executável)
**Atualmente só existem documentação e pastas planejadas.**

## Ferramentas
Git, Docker/Compose, Node LTS, PHP/Composer compatíveis com Laravel escolhido, Python para FastAPI. WSL2 Ubuntu + VS Code Remote WSL é alternativa no Windows.

## M0
1. Criar app React+Vite TS e API Laravel, serviço FastAPI, contratos OpenAPI.
2. Docker Compose PostgreSQL/Redis/API/web/orchestrator/worker com healthchecks.
3. Preencher `.env` de desenvolvimento baseado em `.env.example`, somente credenciais de teste.
4. Migrations/seeds para organização, projetos, boards, colunas e tarefas.
5. Login/RBAC, tracing, request IDs e autenticação de serviço.
6. Scripts padronizados `dev/test/lint/migrate/seed` e CI sem provedores pagos.
7. Fluxo completo fake antes de credenciais reais.
8. Habilitar Jev, OpenRouter e Hermes sob feature flags e budget baixo.

**Não** declarar instalação pronta antes de existirem Compose, código, testes e validação local.
