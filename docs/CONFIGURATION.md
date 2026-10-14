# Parametrização
Herança `global < organização < projeto < tarefa`, exceto **limites máximos de segurança/orçamento** que não podem ser relaxados por níveis inferiores. Versionar alterações e salvar snapshot da política por run.

## Grupos
Kanban (colunas/WIP/automação); GitHub (instalação/repo/branch/prefixo/PR/checks); agentes (perfil, engine, prompts/skills); modelos (allowlist, automático/manual, fallback/revisor); Jev (rubrica/confiança); qualidade (testes, lint, build, revisão, retries); custo (USD/task/mês, alertas, tokens); sandbox (CPU/RAM/tempo/egress); segurança (aprovação, logs, armazenamento).

## Exemplo
Arquivo versionado em `examples/project-policy.example.yaml`. Valores são demonstrativos: modelo real precisa ser consultado no catálogo. Padrão: `autonomous_pr` (abre PR, não faz merge), `max_fix_attempts=3`, teto/run US$ 5 e `max_parallel_runs=2`.

## Regras
- Faltou modelo compatível ou Jev confiável? Bloquear/revisão manual.
- O modelo não pode alterar política para ampliar privilégios.
- Segredos por referências de vault; jamais config text/plain ou frontend.
- Persistir modelo/prompt/config/rubrica efetivamente usados no histórico.
