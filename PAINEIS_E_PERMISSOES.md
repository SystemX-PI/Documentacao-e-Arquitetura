# Painéis e permissões do SystemX

## Navegação

O administrador começa em **Gestão da plataforma**. O menu reúne Visão geral, Empresas clientes, Usuários e acessos, Planos e assinaturas, Auditoria, Configurações e Suporte. A consulta de suporte usa um painel de leitura com conta, titular, acessos e situação comercial. As ferramentas operacionais anteriores continuam nas rotas autorizadas. Os canais internos da operação podem ser acessados em Configurações.

O titular começa no espaço da empresa. O menu reúne Visão geral, Contemplados, Baixas pendentes, Comunicação, Disparo manual, Cadastros, Histórico, Equipe, Canais internos e Meu espaço. A identidade visual, o perfil e a assinatura continuam disponíveis. A navegação do funcionário preserva atalhos para a operação interna.

## Matriz de acesso

| Perfil | Gestão global e suporte | Processos, baixas e comunicação | Equipe e canais da empresa |
|---|---|---|---|
| ADMINISTRADOR | Empresas, usuários, auditoria, relatórios de cobrança e saúde. Suporte com roteiro de consulta. | Acesso legado autorizado preservado. Menu de gestão sem atalhos para ações operacionais. | Administração explícita existente; suporte usa consulta. |
| CLIENTE com conta | Sem acesso global. | Consulta na própria empresa. Alterações de status, baixa e solicitação de WhatsApp exigem conta ativa. Reenvio oficial e reconciliação continuam restritos à operação global. | Titular gerencia os membros e os canais da própria conta conforme os limites do plano. |
| USUARIO | Sem acesso global. | Sem acesso às rotas operacionais abertas ao titular. | Acessos de leitura existentes na própria conta; sem alteração administrativa. |
| FUNCIONARIO | Sem gestão global de empresas. Auditoria global somente quando já tinha escopo de operação global. | Operação existente. Com conta vinculada, limitado àquela empresa. | Sem administração do espaço do titular. |
| CLIENTE sem conta | Sem acesso global. | Portal do beneficiário e seus próprios processos, sem acesso à operação da empresa. | Sem administração de empresa. |

A API determina a conta pela sessão e pela relação do processo com o cliente. Um identificador de outra empresa devolve 404 em rotas operacionais. Perfis sem a permissão recebem 403. O WhatsApp manual do titular exige um número já vinculado ao processo, uma instância da própria conta e uma chave de idempotência. A outbox revalida a empresa e o remetente antes de reservar a tentativa. Resultados sem confirmação seguem bloqueados pela regra anterior.

## API e persistência

- `GET /api/platform/clients/page`, `/clients/summary`, `/clients/{id}`, `/clients/settings` e `/clients/billing-events` adicionam lista paginada, indicadores globais, detalhes, saúde e eventos de cobrança. As rotas são administrativas. Os eventos Stripe disponíveis têm tipo e horário global, sem associação confiável ao cliente gravada na tabela. Nos detalhes da empresa, os pedidos históricos listados são identificados como simulação.
- `GET /api/platform/operation/records` e `/operation/history` consultam os cadastros e a auditoria dos processos da empresa do titular. Cadastros de consórcio, grupo e cota continuam globais.
- `/api/processos-contemplacao` e as rotas específicas de baixa, fila, comunicação e histórico passam a aceitar o titular com escopo. `GET /api/integracoes/processos/{id}/comunicacao/whatsapp` retorna o contato registrado. O POST usa a outbox existente.
- `GET /api/auditoria/pagina` aceita `contaId`. A V22 acrescenta o vínculo de empresa nos novos eventos e registra a empresa de despacho nas novas tentativas dos titulares. Eventos antigos sem vínculo histórico conhecido continuam visíveis na auditoria global.

## Limites previstos

O cadastro de contemplações pelo titular e a edição de cadastros dos consórcios dependem de regras para vincular os registros atualmente compartilhados a uma empresa. A equipe pode criar acessos locais pela tela existente. Convites por e-mail dependem de fluxo próprio. Os estados Stripe são consultivos e nenhuma operação administrativa altera pagamentos. A situação de envio via Gmail e Evolution e os ciclos recorrentes do Stripe continuam dependendo de homologação externa.
