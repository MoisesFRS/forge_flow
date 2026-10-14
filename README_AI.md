# ForgeFlow — README técnico para IA
**Estado:** projeto em planejamento; implementação deve seguir os marcos de `docs/ROADMAP.md`.

## Missão
Construir plataforma multi-projeto de desenvolvimento com agentes. Cada projeto possui um Kanban exclusivo e configurável, repositório GitHub, orçamentos, agentes, modelos e políticas. Tarefas passam por análise Jev, roteamento próprio com catálogo OpenRouter, execução Hermes em sandbox, testes, revisão independente, PR e aprovação.

## Stack-alvo e ownership
- `apps/web`: React, TypeScript, Vite; apenas interface; nunca recebe chaves de IA.
- `apps/api`: Laravel (PHP), API pública, auth/RBAC, entidades, Kanban, política, aprovação, auditoria. **Fonte canônica: PostgreSQL.**
- `services/orchestrator`: FastAPI/Python, eventos, roteamento, custos, fila e adaptadores.
- `services/agent-runner`: isolamento Docker/worktree, Hermes, logs, ferramentas limitadas.
- Redis para filas/cache, nunca fonte única da verdade.
- `packages/contracts`: OpenAPI/JSON Schema/contratos versionados.
- Integrações: GitHub App, Jev/TypeSafe AI e OpenRouter. Evitar acoplamento a SDK específico.

## Invariantes obrigatórios
1. Cada projeto tem um Kanban ativo, com colunas configuráveis. Tarefas são isoladas por projeto e organização.
2. O nome da coluna não define o estado interno da execução. Task, run e PR têm lifecycles distintos.
3. Configuração usa `global → organization → project → task`, respeitando limites rígidos de segurança, autorização e orçamento.
4. Jev retorna classificação estruturada; o ForgeFlow normaliza score e aplica política determinística. IA nunca concede privilégios.
5. O modelo de execução vem do roteador/allowlist e deve ser passado ao Hermes por execução, após confirmar capabilities.
6. Registrar modelo **pedido e real**, tokens/cache, custo, status, avaliações, prompt versionado e correlation ID.
7. Executor e revisor usam sessões/identidades distintas; revisão textual não substitui testes e checks de CI.
8. Branch/workspace isolados por task; nunca push direto na branch protegida ou force push.
9. PR e CI do SHA exato; merge manual por padrão; auto-merge fora do MVP.
10. Eventos, fila, webhooks, retries e PRs idempotentes. Respeitar budgets, quotas e kill-switch.
11. Containers sem root, sem Docker socket, sem credenciais de produção, com recursos e rede restritos.
12. Conteúdo do GitHub e outputs LLM são dados não confiáveis (prompt injection).

## Escopo mínimo (MVP)
Login e papéis; projeto/board/colunas/tarefas; GitHub App; classificador Jev com fallback; catálogo e roteador OpenRouter; Hermes executor e revisor; scripts autorizados de testes; eventos, logs, custos, orçamento; branch/PR; aprovação humana; dashboard global.

## Fora do MVP
Deploy automático e migração de produção, auto-merge, billing SaaS, multi-repo em uma tarefa, seleção de modelo fora da allowlist e memória compartilhada entre tenants.

## Interfaces a criar
`TaskRepository`, `ProjectPolicyResolver`, `GitProvider`, `DecisionProvider`, `ModelCatalog`, `ModelRouter`, `AgentRuntime`, `SandboxManager`, `QualityGate`, `RunEventStore`, `CostEstimator`, `ApprovalService`.

## Sequência de implementação
1. Bootstrap monorepo + contratos + Compose/testes.
2. Banco/RBAC e API de projetos/Kanban/tarefas.
3. GitHub App, webhooks com assinatura, outbox/idempotência.
4. Fluxo completo com provedores falsos (sem custos).
5. Jev, OpenRouter, Hermes em sandbox e telemetria.
6. Revisor, testes, PR, aprovação e dashboard.

## Definition of Done
Código compilável; lint/testes; migrations/contratos versionados; logs sem segredos; testes cross-tenant e erros; PR com evidências, impacto, custo e rollback; docs atualizadas. Obedecer `AGENTS.md`, `docs/SECURITY.md` e `docs/TESTING.md`.
