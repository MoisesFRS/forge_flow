# Segurança e ameaça de execução de código não confiável
A plataforma executa código externo e recebe prompts não confiáveis; priorizar: isolamento entre tenants, prompt injection, supply chain, exfiltração, SSRF, fuga de sandbox, CI/PR indevidos e gastos excessivos.

## Obrigatório
- Laravel RBAC/tenant checks em toda query e ação; GitHub App com permissão mínima e token de instalação efêmero.
- Verificar HMAC + `X-GitHub-Delivery` e deduplicar webhooks.
- Sandbox por task/run: não-root, volumes allowlist, sem Docker socket, capacidades removidas, sem rede host, egress restrito, cgroup CPU/RAM/PIDs e timeout.
- Sem secrets de produção, DB de produção ou acesso entre projetos. Criptografia em repouso e TLS.
- Filtrar contexto enviado ao Jev/OpenRouter; detectar tokens, chaves e dados pessoais. README, issues, commits e saídas dos LLMs não são instruções confiáveis.
- Checks do commit SHA exato; bloquear force push, push em branch protegida, merge e deploy não aprovados.
- Preservar logs redigidos e ledger de custo; aplicar políticas de retenção e privacidade (incluindo LGPD).

## Ações que exigem humano no MVP
Merge, mudança de permissões, operações destrutivas, deploy, acesso a dados sensíveis e gastos acima do teto. Nenhum parecer de agente concede autorização sozinho.

## Testes negativos
Acesso cruzado entre tenants; webhook repetido; instrução maliciosa no README; tentativa de pegar secret via sandbox; budget insuficiente; branch errada; CI de SHA antigo; provider indisponível.
