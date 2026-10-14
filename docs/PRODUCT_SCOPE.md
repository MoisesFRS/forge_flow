# Produto — requisitos
## Problema
Centralizar demandas de desenvolvimento e permitir que agentes executem tarefas com supervisão, custo e rastreabilidade.

## Personas
Administrador define política e orçamento; gestor técnico organiza projetos/quadros; desenvolvedor descreve tarefa/aprova PR; agente executor modifica código; revisor independente valida.

## Hierarquia
`Organização → Projetos → Kanban único/projeto → Colunas personalizadas → Tarefas → Runs → Revisões/Artefatos/PRs`.

Um projeto pode ter vários repositórios; MVP limita uma execução de tarefa a um repositório. Colunas visuais: Backlog, Análise, Pronto, Desenvolvimento, Validação, Aprovação, Concluído, Bloqueado. Usuário pode renomear/reordenar, mas estado semântico não é inferido de texto de coluna.

## Funcionalidades MVP
1. Autenticação, projetos e RBAC por tenant.
2. Quadros exclusivos, colunas WIP, cards, critérios de aceite, comentários, prioridade e dependências básicas.
3. Conexão GitHub App/instalação/repo/branch, webhooks HMAC.
4. Análise Jev de tipo, complexidade, risco e confiança; fallback.
5. Roteador de modelos manual/automático usando catálogo OpenRouter, allowlist, latência e orçamento.
6. Hermes executor em sandbox e revisor separado; testes/CI obrigatórios.
7. Branch, commits, PR, aprovação humana; logs SSE e custo.
8. Dashboard de status, bloqueios, gastos e tarefas aguardando aprovação.
9. Config global/organização/projeto/tarefa e trilha de auditoria.

## Requisitos não funcionais
Segurança multi-tenant, workflows idempotentes, retry com backoff, limites de custos e recursos, eventos correlacionados, observabilidade, verificabilidade de qualidade e integração substituível.

## Fora do MVP
Cobrança SaaS, auto-deploy, auto-merge por padrão, multi-repo editado em uma execução, root/host Docker, produção e memória compartilhada de clientes.

## Métricas
PR aceito por tarefa, aprovação na primeira revisão, custo por PR válido, tempo por estado, taxa de correções e segurança.
