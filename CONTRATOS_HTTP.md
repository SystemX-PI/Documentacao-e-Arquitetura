# Inventário de contratos HTTP

Comparação entre chamadas da interface e o OpenAPI gerado pelo Spring Boot em execução. Inclui a sessão de servidor do widget documentada pela interface. Rotas de provedor e auxiliares sem consumidor ativo aparecem separadamente.

## Operações verificadas

A marca `*` indica parâmetro ou corpo obrigatório. Os tipos vêm do OpenAPI. O código de sucesso reflete também os retornos explícitos dos controllers. Respostas declaradas como Object são detalhadas na seção posterior.

| Método e rota | Parâmetros | Entrada JSON | Sucesso e resposta |
|---|---|---|---|
| `POST /api/assistente/acoes/{token}/confirmar` | `token*` (path) | — | 200 ComunicacaoResponse |
| `POST /api/assistente/mensagens` | — | AssistenteMensagemRequest `*` | 200 AssistenteResposta |
| `GET /api/auditoria/pagina` | `page` (query), `size` (query), `q` (query), `acao` (query), `data` (query) | — | 200 PaginaResponseEvento |
| `POST /api/auth/forgot-password` | — | ForgotPassword `*` | 200 object |
| `POST /api/auth/google` | — | GoogleCredential `*` | 200 AuthResponse |
| `POST /api/auth/google/link` | — | GoogleCredential `*` | 204 — |
| `POST /api/auth/google/photo` | — | GoogleCredential `*` | 200 object |
| `POST /api/auth/google/register` | — | GoogleRegistration `*` | 200 AuthResponse |
| `POST /api/auth/login` | — | LoginRequest `*` | 200 AuthResponse |
| `POST /api/auth/logout` | — | RefreshTokenRequest `*` | 204 — |
| `POST /api/auth/refresh` | — | RefreshTokenRequest `*` | 200 AuthResponse |
| `POST /api/auth/register` | — | RegistroRequest `*` | 201 UsuarioResponse |
| `POST /api/auth/reset-password` | — | ResetPassword `*` | 204 — |
| `GET /api/clientes/pagina` | `page` (query), `size` (query), `q` (query) | — | 200 PaginaResponseUsuarioResponse |
| `POST /api/consorcios` | — | ConsorcioRequest `*` | 201 ConsorcioResponse |
| `GET /api/consorcios/pagina` | `page` (query), `size` (query), `q` (query) | — | 200 PaginaResponseConsorcioResponse |
| `DELETE /api/consorcios/{id}` | `id*` (path) | — | 204 — |
| `GET /api/consorcios/{id}` | `id*` (path) | — | 200 ConsorcioResponse |
| `PUT /api/consorcios/{id}` | `id*` (path) | ConsorcioRequest `*` | 200 ConsorcioResponse |
| `POST /api/cotas` | — | CotaRequest `*` | 201 CotaResponse |
| `GET /api/cotas/pagina` | `page` (query), `size` (query), `q` (query) | — | 200 PaginaResponseCotaResponse |
| `DELETE /api/cotas/{id}` | `id*` (path) | — | 204 — |
| `GET /api/cotas/{id}` | `id*` (path) | — | 200 CotaResponse |
| `PUT /api/cotas/{id}` | `id*` (path) | CotaRequest `*` | 200 CotaResponse |
| `POST /api/grupos` | — | GrupoRequest `*` | 201 GrupoResponse |
| `GET /api/grupos/pagina` | `page` (query), `size` (query), `q` (query) | — | 200 PaginaResponseGrupoResponse |
| `DELETE /api/grupos/{id}` | `id*` (path) | — | 204 — |
| `GET /api/grupos/{id}` | `id*` (path) | — | 200 GrupoResponse |
| `PUT /api/grupos/{id}` | `id*` (path) | GrupoRequest `*` | 200 GrupoResponse |
| `GET /api/integracoes/comunicacoes/fila/pagina` | `page` (query), `size` (query), `q` (query), `status` (query) | — | 200 PaginaResponseFilaComunicacaoResponse |
| `GET /api/integracoes/comunicacoes/fila/resumo` | — | — | 200 ResumoFila |
| `GET /api/integracoes/comunicacoes/historico` | `inicio*` (query), `fim*` (query), `canal` (query) | — | 200 NotificationHistoryResponse |
| `GET /api/integracoes/comunicacoes/remetentes-whatsapp` | — | — | 200 lista de object |
| `GET /api/integracoes/comunicacoes/remetentes-whatsapp/status` | `senderId` (query) | — | 200 StatusRemetente |
| `GET /api/integracoes/processos/{processoId}/baixa` | `processoId*` (path) | — | 200 BaixaResponse |
| `POST /api/integracoes/processos/{processoId}/baixa` | `processoId*` (path) | BaixaRequest `*` | 200 BaixaResponse |
| `GET /api/integracoes/processos/{processoId}/comunicacao` | `processoId*` (path) | — | 200 ComunicacaoResponse |
| `POST /api/integracoes/processos/{processoId}/comunicacao/reenvio` | `processoId*` (path), `Idempotency-Key` (header) | — | 200 ComunicacaoResponse |
| `POST /api/integracoes/processos/{processoId}/comunicacao/whatsapp` | `processoId*` (path), `Idempotency-Key` (header) | WhatsAppRequest `*` | 200 ComunicacaoResponse |
| `GET /api/integracoes/processos/{processoId}/comunicacoes/historico` | `processoId*` (path), `page` (query), `size` (query) | — | 200 PaginaResponseProcessItem |
| `POST /api/integracoes/processos/{processoId}/comunicacoes/{tentativaId}/reconciliacao` | `processoId*` (path), `tentativaId*` (path) | ReconciliarComunicacaoRequest `*` | 204 — |
| `PUT /api/platform/brand` | `accountId` (query) | Brand `*` | 204 — |
| `GET /api/platform/clients` | — | — | 200 object |
| `POST /api/platform/clients` | — | Person `*` | 201 UsuarioResponse |
| `PUT /api/platform/clients/{id}/active` | `id*` (path) | Active `*` | 204 — |
| `GET /api/platform/context` | `accountId` (query) | — | 200 object |
| `POST /api/platform/instances` | `accountId` (query) | Instance `*` | 201 object |
| `DELETE /api/platform/instances/{id}` | `accountId` (query), `id*` (path) | — | 204 — |
| `POST /api/platform/instances/{id}/disconnect` | `accountId` (query), `id*` (path) | — | 204 — |
| `POST /api/platform/instances/{id}/qr` | `accountId` (query), `id*` (path) | — | 200 EvolutionStatusResponse |
| `GET /api/platform/instances/{id}/status` | `accountId` (query), `id*` (path) | — | 200 EvolutionStatusResponse |
| `POST /api/platform/mailboxes` | `accountId` (query) | Mailbox `*` | 201 object |
| `DELETE /api/platform/mailboxes/{id}` | `accountId` (query), `id*` (path) | — | 204 — |
| `GET /api/platform/operation-channels` | — | — | 200 object |
| `POST /api/platform/operation-channels/test/gmail` | — | GmailTeste `*` | 200 Resultado |
| `POST /api/platform/operation-channels/test/whatsapp` | — | WhatsAppTeste `*` | 200 Resultado |
| `PUT /api/platform/profile` | — | Profile `*` | 204 — |
| `POST /api/platform/subscription/checkout` | `accountId` (query) | Checkout `*` | 201 object |
| `POST /api/platform/subscription/checkout/{id}/confirm` | `accountId` (query), `id*` (path) | — | 200 object |
| `POST /api/platform/subscription/portal` | `accountId` (query) | — | 200 object |
| `POST /api/platform/subscription/refresh` | `accountId` (query) | — | 200 object |
| `POST /api/platform/subscription/stripe-checkout` | `accountId` (query) | Checkout | 201 object |
| `POST /api/platform/users` | `accountId` (query) | Person `*` | 201 object |
| `PUT /api/platform/users/{id}/active` | `accountId` (query), `id*` (path) | Active `*` | 204 — |
| `DELETE /api/platform/widget` | `accountId` (query) | — | 204 — |
| `GET /api/platform/widget` | `accountId` (query) | — | 200 object |
| `PUT /api/platform/widget` | `accountId` (query) | Configuracao `*` | 200 object |
| `GET /api/portal/processos` | `page` (query), `size` (query) | — | 200 PaginaResponseProcessoResponse |
| `GET /api/portal/processos/{id}` | `id*` (path) | — | 200 PortalProcessoResponse |
| `GET /api/processos-contemplacao/pagina` | `page` (query), `size` (query), `q` (query), `status` (query) | — | 200 PaginaResponseProcessoResponse |
| `GET /api/processos-contemplacao/{id}` | `id*` (path) | — | 200 ProcessoResponse |
| `PATCH /api/processos-contemplacao/{id}/status` | `id*` (path) | StatusProcessoRequest `*` | 200 ProcessoResponse |
| `POST /api/tipos-consorcio` | — | TipoConsorcioRequest `*` | 201 TipoConsorcioResponse |
| `GET /api/tipos-consorcio/pagina` | `page` (query), `size` (query), `q` (query) | — | 200 PaginaResponseTipoConsorcioResponse |
| `DELETE /api/tipos-consorcio/{id}` | `id*` (path) | — | 204 — |
| `GET /api/tipos-consorcio/{id}` | `id*` (path) | — | 200 TipoConsorcioResponse |
| `PUT /api/tipos-consorcio/{id}` | `id*` (path) | TipoConsorcioRequest `*` | 200 TipoConsorcioResponse |
| `POST /api/usuarios` | — | UsuarioRequest `*` | 201 UsuarioResponse |
| `GET /api/usuarios/pagina` | `page` (query), `size` (query), `q` (query), `tipo` (query) | — | 200 PaginaResponseUsuarioResponse |
| `DELETE /api/usuarios/{id}` | `id*` (path) | — | 204 — |
| `GET /api/usuarios/{id}` | `id*` (path) | — | 200 UsuarioResponse |
| `PUT /api/usuarios/{id}` | `id*` (path) | UsuarioAtualizacaoRequest `*` | 200 UsuarioResponse |
| `PUT /api/usuarios/{id}/senha` | `id*` (path) | SenhaRequest `*` | 204 — |
| `POST /api/widget/chat` | `X-Widget-Session*` (header) | Consulta `*` | 200 object |
| `POST /api/widget/session` | `X-Widget-Key*` (header) | Sessao `*` | 200 object |

## Rotas fora do tráfego direto do frontend

As operações abaixo existem no OpenAPI, porém não fazem parte da navegação direta desta versão. O recebimento de contemplações tem um consumidor auxiliar sem rota de navegação. O webhook é exclusivo do Stripe. Configuração de e-mail e QR/status da integração legada só são referenciados pelas antigas telas auxiliares.

- `GET /`
- `GET /api/consorcios`
- `GET /api/cotas`
- `GET /api/grupos`
- `GET /api/integracoes/comunicacoes/fila`
- `POST /api/integracoes/contemplacoes`
- `GET /api/platform/notification-history`
- `PUT /api/platform/profile/password`
- `POST /api/platform/webhooks/stripe`
- `GET /api/tipos-consorcio`
- `GET /api/usuarios`

- `GET /api/integracoes/whatsapp/status`
- `POST /api/integracoes/whatsapp/qr`
- `PUT /api/configuracoes/email`

## Autorização, campos e estados

- Autenticação por e-mail recebe `email` e `senha`. Login, Google e renovação retornam `token`, `refreshToken`, `tipo` e `expiresIn`. Renovação e logout recebem o token de renovação. Vincular Google e importar foto exigem JWT. Recuperação recebe e-mail e retorna `message` e `expiresIn`. A redefinição recebe e-mail, código e nova senha.
- Plataforma exige JWT de administrador, titular ou equipe. `context` devolve papel, conta, integrantes, integrações e plano. `accountId` delimita a conta quando aplicável. Titular e equipe só podem acessar a própria conta. Administração global lista e altera clientes. Equipe é `USUARIO`, com leitura autorizada e sem escrita de marca, equipe, canais ou widget.
- Os formulários da plataforma enviam `name` e os campos da operação. Equipe e remetente de e-mail usam `email` e `password`. Marca usa `logo` opcional, `primary` e `accent`. Estado de membro/conta usa `active`. Perfil usa `name` e `photo`. Widget identifica `origin` e recebe credencial própria apenas na rota de sessão. Respostas de teste de canal usam `accepted` e `message`.
- Contratação recebe `paymentMethod` com `PIX` ou `CARD`. Stripe começa com `checkoutUrl`, `status`, `amountCents`, `currency`, `interval` e `simulation`. Simulação retorna o identificador do pedido e seus próprios estados. Consulta de assinatura retorna `active`, `status` e `paidUntil`. Valores de cobrança são inteiros em centavos BRL. Crédito e valores cadastrais são decimais em reais. O retorno do navegador não ativa o plano.
- Operação requer administrador ou funcionário. Auditoria e remetentes de operação exigem acesso global. Histórico e busca de processos respeitam a conta do operador. Portal aceita clientes e filtra os processos vinculados ao usuário. Cadastros de usuário e alterações de cadastros de consórcio exigem administrador global. O recebimento de contemplações autentica por chave de integração.
- Páginas usam `items`, `total`, `page` iniciando em zero e `size`. Filtros `q`, `status`, `acao` e datas só são enviados nas rotas que os aceitam. A API retorna lista vazia no resultado paginado sem registros.
- A transição usa `status` e `observacao` e o backend fornece `transicoesPermitidas`. A baixa usa `observacao` e obtém o operador da sessão. Repetir a baixa retorna o comprovante original. O histórico e as comunicações mantêm o estado de negócio separado do aceite do provedor. Reenvio aceita `Idempotency-Key` e o despacho usa `NA_FILA`, `EM_ENVIO`, `INCERTO`, `INCERTO_EXECUCAO` e `CONCLUIDO`. Reconciliação de execução ainda incerta é recusada.
- A API usa 400 para entrada inválida, 401 para falta de sessão, 403 para falta de permissão, 404 para recurso ausente ou fora do escopo e 409 para conflito. Alguns limites do plano retornam 402. HTTP 204 tem corpo vazio. Comprovante ausente é distinto de resposta indisponível.
- Datas de calendário usam ISO sem horário. Os horários operacionais novos são gravados em UTC pelo backend e chegam como `LocalDateTime` sem offset. O frontend interpreta esses valores como UTC e formata no fuso do navegador. O offset explícito de outros timestamps é preservado. O fuso de registros importados legados precisa de conferência antes de qualquer correção em massa.
