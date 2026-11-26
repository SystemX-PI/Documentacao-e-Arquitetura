# Otimização do Processo de Comunicação e Baixa de Clientes Contemplados em Consórcios

Projeto desenvolvido para a **F M C CENTER CAR LTDA**, em parceria com o **SENAI Cáceres - MT**.

O objetivo é desenvolver uma aplicação web capaz de tornar mais eficiente o processo de acompanhamento, comunicação e baixa de clientes contemplados em consórcios.

---

## Referências de integração

- [Instalação oficial do Back-end e da pilha completa](https://github.com/SystemX-PI/Back-end#subir-o-projeto-completo-com-docker)
- [Execução local e testes do Front-End](https://github.com/SystemX-PI/Front-End#executar-localmente)
- [Contratos HTTP do frontend e backend](CONTRATOS_HTTP.md)
- [Validação e preparação da entrega](VALIDACAO_ENTREGA.md)
- [Painéis e matriz de permissões](PAINEIS_E_PERMISSOES.md)

## Objetivo do Projeto

O projeto tem como objetivo criar um sistema que permita centralizar e organizar as informações dos clientes contemplados em consórcios.

A aplicação deverá facilitar o acompanhamento de cada cliente desde a contemplação até a finalização do processo, permitindo registrar comunicações, atualizar situações e realizar a baixa de forma mais organizada.

Com isso, espera-se:

* reduzir o tempo necessário para comunicar os clientes contemplados;
* diminuir falhas e atrasos;
* evitar retrabalho;
* melhorar o controle das informações;
* facilitar o acompanhamento dos processos;
* aumentar a eficiência operacional;
* proporcionar maior agilidade no atendimento aos clientes.

---

## Sobre o Projeto

Quando um cliente é contemplado em um consórcio, a empresa precisa realizar diferentes procedimentos internos.

Entre eles estão:

* identificar o cliente contemplado;
* realizar o contato;
* registrar o andamento;
* acompanhar possíveis pendências;
* atualizar o status do processo;
* realizar a baixa quando o processo for concluído.

Atualmente, essas etapas podem demandar tempo e esforço operacional.

O sistema será desenvolvido para centralizar essas informações em um único ambiente, facilitando o acompanhamento dos clientes contemplados e permitindo que a equipe responsável visualize com mais clareza quais processos estão pendentes, em andamento ou finalizados.

---

## Tecnologias Utilizadas

### Frontend

O frontend será desenvolvido utilizando:

* React;
* JavaScript ou TypeScript;
* HTML;
* CSS;
* Axios;
* React Router.

O React será responsável pela interface e interação do usuário com o sistema.

---

### Backend

O backend será desenvolvido utilizando:

* Java;
* Spring Boot;
* Spring Web;
* Spring Data JPA;
* Spring Security;
* API REST.

O backend será responsável pelas regras de negócio, autenticação, validações e comunicação com o banco de dados.

---

### Banco de Dados

Será utilizado:

* MySQL.

O MySQL será responsável pelo armazenamento das informações dos usuários, clientes, consórcios, contemplações, contatos e histórico dos processos.

---

## Integração das Tecnologias

A arquitetura inicial do sistema será:

```text
Frontend
React
   ↓
API REST
   ↓
Backend
Java + Spring Boot
   ↓
Banco de Dados
MySQL
```

O React não acessará diretamente o banco de dados.

Todas as operações serão enviadas para o backend através da API.

O backend será responsável por validar as informações, executar as regras do sistema e acessar o MySQL.

Fluxo simplificado:

```text
Usuário
   ↓
React
   ↓
API REST
   ↓
Spring Boot
   ↓
MySQL
```

---

## Tecnologias e Integrações que NÃO fazem parte da primeira versão

Inicialmente, o projeto não terá integração com:

* WhatsApp;
* API oficial do WhatsApp;
* SMS;
* bancos;
* sistemas de pagamento;
* administradoras de consórcio;
* inteligência artificial;
* aplicativo Android;
* aplicativo iOS;
* assinatura digital;
* serviços externos de envio automático de mensagens.

Essas funcionalidades poderão ser avaliadas futuramente.

---

# Padrão de Commits

Para manter o histórico do projeto organizado, todos os integrantes deverão seguir um padrão de commits.

Será utilizado o padrão **Conventional Commits**.

Formato:

```text
tipo: descrição da alteração
```

---

## Tipos de Commit

### feat

Utilizado quando uma nova funcionalidade for criada.

```text
feat: adiciona cadastro de clientes
```

```text
feat: cria tela de contemplados
```

---

### fix

Utilizado para correções.

```text
fix: corrige erro no login
```

```text
fix: corrige atualização de status
```

---

### docs

Utilizado para alterações na documentação.

```text
docs: adiciona documentação do projeto
```

```text
docs: atualiza requisitos do sistema
```

---

### style

Utilizado para alterações visuais ou de formatação que não modificam a lógica principal.

```text
style: ajusta layout do dashboard
```

---

### refactor

Utilizado para reorganização ou melhoria do código.

```text
refactor: reorganiza service de clientes
```

---

### test

Utilizado para criação ou alteração de testes.

```text
test: adiciona teste de login
```

---

### chore

Utilizado para configurações e tarefas de manutenção.

```text
chore: configura estrutura inicial do projeto
```

---

## Regras para os Commits

Os commits deverão ser claros e informar o que foi realizado.

### Correto

```text
feat: cria cadastro de clientes
```

```text
fix: corrige validação do telefone
```

```text
docs: atualiza visão geral do projeto
```

### Evitar

```text
alteração
```

```text
teste
```

```text
mudança
```

```text
final
```

```text
arrumei
```

```text
123
```

---

## Equipe

O projeto é desenvolvido por:

* Nicolas
* Kaique
* Julio
* Kaiki
* Swell
* Juca

### Líderes do Projeto

* Nicolas
* Kaique
* Julio

---

## Instituição

**SENAI Cáceres - MT**

---

## Empresa

**F M C CENTER CAR LTDA**

---

## Área

**Tecnologia da Informação**

---

## Status do Projeto

Em desenvolvimento.

**Vigência:** 31/08/2026 até 03/03/2027.

## Guia técnico do front-end

- [Versão em PDF](docs/frontend/GUIA_FRONTEND_SYSTEMX.pdf)
- [Arquivo HTML editável usado para gerar o PDF](docs/frontend/GUIA_FRONTEND_SYSTEMX.html)
