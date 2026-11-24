# Validação técnica e preparação da entrega

Este guia registra os ensaios da versão candidata. A instalação da versão publicada está nos READMEs dos repositórios de código. Os caminhos e recursos de homologação abaixo passam a fazer parte da versão oficial quando os respectivos Pull Requests são integrados.

## Operação local e Compose

Os checkouts de Back-end e Front-End ficam em pastas irmãs. Siga o guia `Back-end/LOCAL.md` para iniciar o Compose padrão ou o projeto descartável `compose.verify.yml`. O ensaio descartável sobe Nginx, Spring Boot e MySQL com volumes por projeto. A única porta publicada é 5177 em loopback. O Nginx resolve o serviço `backend` pela rede Compose. As verificações de saúde mostram prontidão do MySQL, inicialização do Spring e resposta do Nginx. A validação por Chromium complementa esses health checks com login, permissões, paginação, baixa idempotente, histórico e comunicação sem disparo externo.

Em banco MySQL vazio, Flyway aplica V1–V21. Uma atualização representativa parte de V19, com histórico fictício, comunicações antigas e assinatura existente. Pare workers da versão antiga antes de habilitar V20. Separe credenciais e volumes do ensaio. Um reinício do Compose preserva dados quando o volume do projeto é mantido.

## Sequência de persistência

| Versão | Alteração |
|---|---|
| V1 | Estrutura original de consórcios, usuários, processos, baixas, comunicação e auditoria. |
| V2–V3 | Registros legados de demonstração. Confirmar política de seed antes da entrega. |
| V4–V6 | Renovação de sessão, dados de comunicação e telefone. |
| V7 | Revogação de sessão, vínculo do cliente ao processo e índices. |
| V8–V10 | Contas e integrações da plataforma, checkout simulado e indicador de plano confirmado. |
| V11–V13 | Perfil, recuperação de senha, assinatura Stripe e identidade Google. |
| V14–V16 | Widget, Pix, canais internos, auditoria e vínculo de reenvio. |
| V17–V18 | Limite compartilhado de recuperação e unicidade da chave de operação de comunicação. |
| V19–V20 | Outbox persistente e recuperação de despachos comprovadamente não iniciados. Registros ambíguos continuam bloqueados. |
| V21 | Reserva de checkout e marca temporal de assinatura. |

## CI e proteção de branches

O backend executa Maven em H2 e um job separado com MySQL, concorrência e Flyway. O frontend executa lint, build e Playwright com API controlada. Os workflows são configurados para push e pull request em `main` e `develop`. A suíte real com os dois repositórios permanece reproduzível no Compose isolado. O pacote de revisão local exclui logs brutos, segredos e traces com sessões reais.

Para GitHub, configurar em **Settings → Rules → Rulesets** (ou **Branches**, conforme a interface da organização) um ruleset ativo para `main` e `develop` nos repositórios que têm essas branches:

1. Exigir pull request e pelo menos uma revisão aprovada. Invalidar aprovações antigas quando houver novo commit e exigir que conversas sejam resolvidas.
2. Exigir branches atualizadas antes de integrar. No backend, selecionar `backend-ci` e `mysql-integration`. No frontend, selecionar `Verificação (Lint, Build e Testes)`. Escolher os nomes depois de os jobs aparecerem com execução remota. Para o repositório de documentação, proteger `main` por PR e revisão, sem exigir jobs inexistentes.
3. Bloquear force push e exclusão da branch. Limitar permissões de bypass à política definida pela organização.

Consulte as opções de cada regra no [manual do GitHub](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/available-rules-for-rulesets).

A auditoria somente leu as configurações remotas. Os workflows atualizados precisam ser publicados e executados com autorização antes de se exigir seus checks no GitHub.

## Limitações

A cobertura de acessibilidade verificou teclado, foco, Escape, rótulos, erros, ações desativadas e reflow de fluxos selecionados. A avaliação completa com leitor de tela continua pendente.

## Homologações e entrega

- A candidata do lote 9 passou em banco limpo e na atualização de backup fictício restaurado da V19 para a V21. Na atualização que inclui V20, pare os workers antigos antes de migrar.
- Na candidata do lote 9, o Stripe Sandbox confirmou cartão, Pix, webhooks, recusa, cancelamento, expiração e persistência. Renovação automática e inadimplência por ciclo ainda exigem um sandbox autorizado com Test Clocks. A referência do provedor é o [guia da Stripe CLI](https://docs.stripe.com/cli/sandbox).
- Use o Client ID OAuth público em `GOOGLE_CLIENT_ID` no backend e em `VITE_GOOGLE_CLIENT_ID` no frontend. Cadastre no Google Cloud a origem exata usada pelo navegador.
- A Evolution usa PostgreSQL, Redis e persistência de instâncias. O backend acessa o serviço pela rede Docker. Habilite o canal só depois de preparar a instância de teste. A homologação externa de WhatsApp e Gmail continua pendente.
- Abra revisões da versão oficial contra a `main`. Confira os checks, a compatibilidade entre os repositórios e a revisão independente das mudanças sensíveis. Valide novamente a partir de um clone limpo após o merge. Deploy exige uma etapa separada.
