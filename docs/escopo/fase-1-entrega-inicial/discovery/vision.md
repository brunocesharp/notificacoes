# Visão do Projeto — Notification Hub

> Gerado em: 29/05/2026
> Versão: 1.0

---

## O Problema

Hoje cada sistema da empresa controla suas próprias notificações de forma independente, sem centralização. Os usuários precisam acessar múltiplos sistemas para acompanhar notificações distintas, sem nenhum controle sobre o que recebem ou por qual canal. Não há rastreabilidade de origem nem possibilidade de filtrar por tipo ou sistema.

| Aspecto | Descrição |
|---------|-----------|
| **Quem sente essa dor** | Usuários finais (colaboradores), administradores dos sistemas e equipes responsáveis pelos sistemas internos |
| **Frequência/Impacto** | Diário — toda vez que um sistema dispara uma notificação (ex: jobs agendados executados) o usuário pode não ser alcançado ou recebe notificações indesejadas |
| **Situação atual** | Cada sistema gerencia suas próprias notificações de forma isolada, sem integração entre eles |

---

## Público-Alvo

Três perfis distintos interagem com o Notification Hub.

| Perfil | Descrição | Principal Necessidade | Contexto de Uso |
|--------|-----------|----------------------|-----------------|
| **Usuário Final** | Colaborador da empresa que usa os sistemas internos | Receber apenas as notificações desejadas, no canal preferido, em qualquer sistema que estiver logado | Rotina de trabalho — acesso a múltiplos sistemas internos |
| **Administrador** | Responsável pela gestão das configurações globais do hub | Configurar tipos de notificações, gerenciar integrações e ter visibilidade centralizada | Gestão e manutenção do sistema |
| **Sistema Integrado** | Sistema interno (ex: scheduler de jobs) que publica notificações via API/broker | Enviar notificações identificadas por remetente para todos os usuários elegíveis | Execução automática — jobs agendados, eventos de sistema |

---

## Proposta de Valor

Um hub central que unifica a comunicação instantânea de todos os sistemas internos, dando ao usuário controle total sobre o que recebe e como recebe.

| Aspecto | Descrição |
|---------|-----------|
| **Transformação esperada** | Usuário recebe apenas as notificações que deseja, no canal preferido (ex: somente e-mail), estando logado em qualquer sistema da empresa |
| **Diferencial** | Centralização com rastreabilidade de origem — sabe-se qual sistema enviou cada notificação; configuração por tipo e canal por usuário |
| **Frase de elevador** | "Um único lugar para receber, filtrar e gerenciar todas as notificações dos sistemas da empresa" |

---

## Motivação e Contexto

O projeto surge da necessidade de modernizar e unificar a comunicação entre sistemas durante a reformulação geral da plataforma interna da empresa.

**Gatilhos identificados:**
- Reformulação de todos os sistemas internos da empresa exige uma camada de notificação padronizada
- Crescimento do número de sistemas gera fragmentação crescente das notificações
- Prazo definido: primeira versão em produção até **05/06/2026**

---

## Restrições Conhecidas

| Tipo | Restrição | Impacto |
|------|-----------|---------|
| Tecnologia — Backend | .NET Core última versão LTS | Stack obrigatória para a API de notificações |
| Tecnologia — Frontend | Angular 20+ versão LTS | Stack obrigatória para a interface web |
| Tecnologia — Broker | .NET Core última versão LTS | Stack obrigatória para o serviço de mensageria |
| Prazo | Primeira versão em produção até 05/06/2026 | Janela de desenvolvimento muito curta — priorização de escopo essencial |
| Legado | Nenhum sistema legado | Sem débito técnico de integrações antigas |
| Equipe/Orçamento | Sem limitações identificadas | Flexibilidade para definir estrutura de equipe |

---

## Declaração de Visão

> "O Notification Hub unifica todas as notificações dos sistemas internos da empresa em um único canal centralizado, permitindo que cada usuário receba apenas o que é relevante para ele, no momento certo e pelo canal que preferir — independentemente de qual sistema originou o evento."

---

## Pontos a Refinar

- [ ] Quais são os tipos de notificação iniciais a serem suportados?
- [ ] Quais canais serão entregues na v1 (in-app, e-mail, push, WebSocket)?
- [ ] Como será a autenticação dos sistemas integrados (chave de API, token, etc.)?
- [ ] Qual o volume estimado de notificações por dia?
- [ ] Como será a política de retenção/histórico de notificações?

---

## Próximos Passos Sugeridos

Com base nesta visão, as próximas etapas recomendadas de discovery são:
- **Oportunidades** — mapear dores e jobs to be done em profundidade
- **Hipóteses** — identificar premissas que precisam ser validadas antes de investir
- **Stakeholders** — mapear os envolvidos e suas expectativas
- **Métricas** — definir como medir o sucesso do hub
