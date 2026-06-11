# Escopo — Fase 1: Entrega Inicial

> Projeto: Notification Hub
> Situação: Rascunho
> Criado em: 29/05/2026
> Responsável: Bruno Alves
> Prazo: 05/06/2026

---

## Visão Geral

Centralizar as notificações de todos os sistemas internos da empresa em um único hub, permitindo que cada usuário receba apenas o que é relevante para ele, no canal que preferir, em tempo real — independentemente de qual sistema originou o evento.

---

## Problema Endereçado

Hoje cada sistema da empresa gerencia suas próprias notificações de forma isolada. Os usuários recebem notificações fragmentadas, sem controle sobre o que recebem ou por qual canal, e precisam acessar múltiplos sistemas para acompanhar todas as comunicações.

---

## Público-Alvo

| Perfil | Descrição |
|--------|-----------|
| **Usuário Final** | Colaboradores da empresa que recebem e gerenciam notificações |
| **Administrador** | Responsável pela gestão das configurações globais do hub |
| **Sistema Integrado** | Sistemas internos que publicam notificações via API/Broker (fire and forget) |

---

## Funcionalidades da Fase 1

### F1 — Hub de Notificações (Usuário Final)
**Oportunidade:** Usuário precisa acessar múltiplos sistemas para ver todas as notificações

| Item | Descrição |
|------|-----------|
| F1.1 | Visualizar todas as notificações recebidas em um único lugar |
| F1.2 | Marcar notificações como lidas / não lidas |
| F1.3 | Badge com contagem de notificações não lidas |
| F1.4 | Link direto na notificação para o sistema/contexto de origem |
| F1.5 | Histórico de notificações recebidas |

---

### F2 — Preferências de Notificação (Usuário Final)
**Oportunidade:** Usuário recebe notificações irrelevantes de sistemas que não usa

| Item | Descrição |
|------|-----------|
| F2.1 | Configurar quais sistemas deseja receber notificações |
| F2.2 | Configurar quais tipos de notificação deseja receber |
| F2.3 | Configurar o canal preferido de recebimento (in-app, e-mail) |

---

### F3 — Entrega em Tempo Real
**Oportunidade:** Usuário perde notificações importantes por não estar no sistema correto

| Item | Descrição |
|------|-----------|
| F3.1 | Entrega de notificações em tempo real via WebSocket/SSE para usuários logados |
| F3.2 | Entrega via e-mail para usuários offline ou que optaram por e-mail |

---

### F4 — API de Integração (Sistemas Integrados)
**Oportunidade:** Times de desenvolvimento sem padrão centralizado para envio de notificações automáticas

| Item | Descrição |
|------|-----------|
| F4.1 | API REST para publicação de notificações por sistemas integrados |
| F4.2 | Message Broker para publicação assíncrona de notificações |
| F4.3 | Identificação do sistema remetente em cada notificação |
| F4.4 | Autenticação dos sistemas integrados via token/chave de API |

---

### F5 — Painel Administrativo
**Oportunidade:** Administrador sem visibilidade e controle central

| Item | Descrição |
|------|-----------|
| F5.1 | Gerenciar permissões por sistema — bloquear/liberar sistemas para envio |
| F5.2 | Gerenciar tipos de notificação disponíveis para cada sistema |
| F5.3 | Buscar notificações com filtros avançados (sistema, tipo, usuário, data, status) |

---

## O Que Está Fora do Escopo da Fase 1

| Item | Justificativa |
|------|---------------|
| Push notifications (mobile) | Sem requisito mobile na v1 |
| Notificações em lote agrupadas | A definir em fase posterior |
| Relatórios e dashboards de auditoria | A definir em fase posterior |
| SDK para sistemas integrados | Documentação da API é suficiente para v1 |
| Notificações para usuários offline via SMS | Fora do escopo atual |

---

## Restrições Técnicas

| Tipo | Restrição |
|------|-----------|
| Backend (API) | .NET Core última versão LTS |
| Frontend | Angular 20+ versão LTS |
| Broker/Mensageria | .NET Core última versão LTS |
| Entrega real-time | WebSocket ou SSE |
| Banco de dados | A definir |
| Legado | Nenhum — não há sistemas legados a integrar |

---

## Hipóteses Críticas a Validar

> Extraídas de `discovery/assumptions.md` — devem ser validadas durante o desenvolvimento da Fase 1.

| ID | Hipótese | Ação |
|----|----------|------|
| H4 | Sistemas internos vão aderir à integração | Definir se integração é obrigatória antes do início |
| H7 | WebSocket/SSE é viável na infraestrutura atual | Spike técnico de 1-2 dias no início do projeto |
| H8 | Broker suporta o volume de notificações | Estimar volume e realizar teste de carga antes do go-live |
| H9 | Sistemas integram sem grandes mudanças arquiteturais | PoC com 1-2 sistemas piloto no início do desenvolvimento |

---

## Stakeholders

| Stakeholder | Papel | Estratégia |
|-------------|-------|------------|
| Bruno Alves | Arquiteto / Decisor | Responsável por todas as decisões |
| Clientes dos sistemas | Solicitantes | Engajar ativamente — comunicação semanal por e-mail |
| Usuários finais | Usuários do hub | Manter informados — onboarding no lançamento |
| Administradores | Gestores do hub | Engajar ativamente |
| Times de desenvolvimento | Integradores | Manter informados — documentação clara da API |

---

## Critérios de Aceite da Fase 1

- [ ] Usuário consegue visualizar todas as notificações recebidas em um único lugar
- [ ] Usuário consegue configurar quais sistemas e tipos de notificação deseja receber
- [ ] Notificações chegam em tempo real para usuários logados no navegador
- [ ] Sistemas integrados conseguem publicar notificações via API REST e/ou Broker
- [ ] Administrador consegue bloquear sistemas e gerenciar tipos de notificação
- [ ] Administrador consegue buscar notificações com filtros
- [ ] Notificações possuem link direto para o sistema de origem

---

## Dependências

| Dependência | Tipo | Status |
|-------------|------|--------|
| Definição de obrigatoriedade de integração dos sistemas | Organizacional | ⚠️ Pendente |
| Validação de viabilidade do WebSocket/SSE na infra | Técnica | ⚠️ Pendente (spike) |
| Estimativa de volume de notificações por sistema | Técnica | ⚠️ Pendente |
| Definição do banco de dados | Técnica | ⚠️ Pendente |

---

## Situação do Escopo

| Estado | Descrição |
|--------|-----------|
| ✅ Rascunho | Escopo gerado a partir do discovery |
| ⬜ Em revisão | Aguardando validação dos stakeholders |
| ⬜ Aprovado | Aprovado para início do desenvolvimento |
| ⬜ Em execução | Desenvolvimento em andamento |
| ⬜ Concluído | Fase 1 entregue em produção |

---

## Próximos Passos

1. Revisar este escopo com os stakeholders e atualizar para **Em revisão**
2. Resolver as dependências pendentes (obrigatoriedade de integração, spike de WebSocket, volume de notificações)
3. Iniciar **Especificação Funcional** para detalhar as regras de negócio de cada funcionalidade
4. Definir o banco de dados e arquitetura detalhada
