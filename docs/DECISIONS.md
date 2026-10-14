# Decisões arquiteturais — iniciais
| ID | Status | Decisão |
| --- | --- | --- |
| ADR-001 | proposta | monorepo React/TS + Laravel + FastAPI + PostgreSQL + Redis |
| ADR-002 | acordada | Kanban próprio por projeto, PostgreSQL como fonte canônica |
| ADR-003 | acordada | Jev avalia; roteador ForgeFlow decide; OpenRouter fornece; Hermes executa |
| ADR-004 | acordada | executor e revisor independentes, CI e aprovação humana |
| ADR-005 | acordada | GitHub App com menor privilégio |
| ADR-006 | acordada | sandbox efêmera por run, sem segredos de produção |
| ADR-007 | aberta | versões específicas de ferramentas e bibliotecas |
| ADR-008 | aberta | storage de artefatos, eventos e política de retenção |
| ADR-009 | aberta | eventual uso interno do Kanban Hermes sem segunda fonte de verdade |
| ADR-010 | aberta | licença comercial/open source |

Registrar novas decisões em `docs/adr/NNNN-titulo.md` com contexto, alternativas, decisão e rollback.
