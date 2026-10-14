# Regras para qualquer agente de programação
**Leia primeiro:** `README_AI.md`, `docs/PRODUCT_SCOPE.md`, `docs/ARCHITECTURE.md`, `docs/DECISIONS.md` e a documentação específica do módulo.

- Trabalhar somente dentro da tarefa e dos critérios de aceite; não fazer refatoração extra.
- Não afirmar que há software executável: este repositório começa com documentação e estrutura.
- Nunca incluir segredos, chaves, senhas nem dados pessoais em commits, logs, prompts externos e artifacts.
- Não rodar comandos destrutivos, testes contra produção, `push --force`, deploy ou merge automático sem autorização/política explícita.
- Não acessar repositórios, pastas, memória ou tokens de outras organizações.
- Frontend usa somente API Laravel; API é dono dos dados/ACL; FastAPI orquestra; Hermes opera em sandbox.
- Jev faz julgamento limitado; regras de segurança são determinísticas no backend.
- Gerar branch e worktree independentes; revisor independente; exigir testes/CI do SHA atual.
- Limitar orçamento, tempo, CPU, memória, rede, retries e permissões. Falha segura em provedor indisponível.
- Implementar ports/adapters para GitHub, Jev, OpenRouter e Hermes; usar mocks/fakes na CI.
- Corrigir problemas do revisor até limite configurado; se bloqueado, registrar motivo e pedir intervenção humana.
- Atualizar documentação e contratos; deixar PR com comandos e saídas de teste, custo observado e rollback.

## Checklist final
- [ ] Projeto/tenant correto e acesso conferido
- [ ] Mudança mínima e critérios de aceite atendidos
- [ ] Testes/lint/build pertinentes registrados
- [ ] Sem segredos ou privilégio fora da sandbox
- [ ] PR/revisão independente/CI verificados
- [ ] Nenhuma etapa sensível aprovada somente por IA
