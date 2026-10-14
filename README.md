# ForgeFlow

> **Da tarefa ao Pull Request.** Plataforma para orquestrar agentes de IA no desenvolvimento de software com Kanban por projeto, Jev, OpenRouter, Hermes Agent e GitHub.

**Status:** planejamento; arquitetura e documentação inicial. Aplicação ainda não implementada.

## Proposta

Cada projeto possui Kanban próprio, repositórios e parâmetros independentes. A plataforma analisa tarefas, classifica dificuldade e risco com Jev, escolhe um modelo aprovado via OpenRouter, executa em sandbox com Hermes Agent, realiza testes e revisão independente, e prepara um Pull Request para aprovação humana.

## Stack prevista

React + TypeScript + Vite; Laravel/PHP; FastAPI/Python; PostgreSQL; Redis; Docker; GitHub App; Jev/TypeSafe AI; OpenRouter; Hermes Agent.

## Leia primeiro

- [README técnico para IA](README_AI.md) e [regras para agentes](AGENTS.md)
- [Escopo](docs/PRODUCT_SCOPE.md), [arquitetura](docs/ARCHITECTURE.md), [modelo de dados](docs/DATA_MODEL.md)
- [API](docs/API_CONTRACT.md), [execução](docs/AGENT_WORKFLOW.md), [configuração](docs/CONFIGURATION.md)
- [Segurança](docs/SECURITY.md), [testes](docs/TESTING.md), [observabilidade](docs/OBSERVABILITY.md)
- [Setup](docs/SETUP.md), [roadmap](docs/ROADMAP.md), [decisões](docs/DECISIONS.md), [referências](docs/REFERENCES.md)

**A documentação descreve uma arquitetura alvo, não funcionalidades existentes.**
