# Hipóteses e Premissas — Notification Hub

> Gerado em: 29/05/2026
> Versão: 1.0

---

## Conceito

Toda decisão de produto carrega suposições embutidas — sobre o que os usuários querem, sobre o que é tecnicamente possível, sobre o que o negócio espera. O objetivo deste documento é tornar essas suposições explícitas para validá-las antes de construir a coisa errada.

---

## Hipóteses sobre Usuários

| ID | Hipótese | Evidência Atual |
|----|----------|-----------------|
| H1 | Os usuários vão adotar e configurar suas preferências de notificação ativamente | Nenhuma — primeira solução do tipo na empresa |
| H2 | Os usuários vão preferir receber notificações pelo hub em vez de continuar nos sistemas individuais | Nenhuma — comportamento ainda não testado |
| H3 | Notificações com link direto para o sistema de origem são suficientes para o usuário tomar ação | Alta — padrão amplamente adotado em outros produtos |

---

## Hipóteses sobre o Negócio

| ID | Hipótese | Evidência Atual |
|----|----------|-----------------|
| H4 | Os sistemas internos vão aderir à integração com o hub | Média — depende de decisão organizacional/obrigatoriedade |
| H5 | A v1 entregue até 05/06/2026 é suficiente para gerar valor e atender as dores críticas | Alta — escopo mínimo foi definido com base nas dores identificadas |
| H6 | O hub vai reduzir ruído e retrabalho de forma mensurável após o lançamento | Média — depende da adoção e configuração pelos usuários |

---

## Hipóteses Técnicas

| ID | Hipótese | Evidência Atual |
|----|----------|-----------------|
| H7 | WebSocket/SSE é viável para entrega em tempo real na infraestrutura atual da empresa | Média — infraestrutura ainda não validada para esse protocolo |
| H8 | O message broker consegue suportar o volume de notificações gerado pelos sistemas internos | Média — volume estimado ainda não definido |
| H9 | Os sistemas integrados conseguem publicar notificações via API/Broker sem grandes mudanças arquiteturais | Média — depende da arquitetura de cada sistema |
| H10 | A equipe tem familiaridade com Angular 20+ LTS e .NET Core LTS | Alta — stack padrão da empresa |

---

## Matriz de Priorização

> Classificação por **impacto se a hipótese estiver errada** × **certeza que temos hoje**

| ID | Hipótese | Impacto se errada | Certeza atual | Prioridade |
|----|----------|-------------------|---------------|------------|
| H1 | Usuários vão adotar e configurar preferências ativamente | Alto — hub subutilizado | Média | ⚠️ Validar primeiro |
| H2 | Usuários preferirão o hub aos sistemas individuais | Alto — baixa adoção | Média | ⚠️ Validar primeiro |
| H3 | Links diretos são suficientes para o usuário tomar ação | Médio — UX comprometida | Alta | ✅ Confirmar e seguir |
| H4 | Sistemas internos vão aderir à integração | Alto — hub sem dados | Média | ⚠️ Validar primeiro |
| H5 | V1 até 05/06/2026 é suficiente para gerar valor | Alto — prazo e escopo comprometidos | Alta | ✅ Confirmar e seguir |
| H6 | Hub vai reduzir ruído e retrabalho mensurável | Médio — dificuldade de medir sucesso | Média | 👀 Monitorar |
| H7 | WebSocket/SSE é viável na infraestrutura atual | Alto — entrega em tempo real inviável | Média | ⚠️ Validar primeiro |
| H8 | Broker suporta o volume de notificações | Alto — falha em produção | Média | ⚠️ Validar primeiro |
| H9 | Sistemas integram sem grandes mudanças arquiteturais | Alto — custo de adoção alto | Média | ⚠️ Validar primeiro |
| H10 | Equipe tem familiaridade com Angular 20+ e .NET Core | Médio — curva de aprendizado | Alta | ✅ Confirmar e seguir |

---

## Hipóteses Críticas — Plano de Validação

As hipóteses marcadas como **⚠️ Validar primeiro** devem ser endereçadas antes ou no início do desenvolvimento.

| ID | Hipótese | Como Validar | Quando |
|----|----------|-------------|--------|
| H1 | Adoção ativa pelos usuários | Lançar com onboarding guiado; medir % de usuários que configuram preferências na primeira semana | Após lançamento da v1 |
| H2 | Preferência pelo hub | Entrevistas com usuários-piloto; medir acesso ao hub vs. sistemas individuais | Pré-lançamento (piloto) |
| H4 | Adesão dos sistemas internos | Definir se a integração será mandatória ou opcional; alinhar com gestores dos sistemas | Antes do desenvolvimento |
| H7 | Viabilidade do WebSocket/SSE | Spike técnico de 1-2 dias na infraestrutura atual | Início do desenvolvimento |
| H8 | Capacidade do broker | Estimar volume de notificações por sistema; realizar teste de carga | Antes de ir para produção |
| H9 | Integração sem grandes mudanças | Realizar prova de conceito (PoC) com 1-2 sistemas piloto | Início do desenvolvimento |

---

## Pontos a Refinar

- [ ] Definir se a integração dos sistemas com o hub será **obrigatória ou opcional** (impacta H4 diretamente)
- [ ] Estimar o **volume médio de notificações por dia** para validar H8
- [ ] Realizar **spike técnico de WebSocket/SSE** para confirmar H7
- [ ] Definir sistemas piloto para a **PoC de integração** (H9)

---

## Próximos Passos Sugeridos

Com as hipóteses mapeadas e priorizadas, os próximos passos podem ser:
- **Stakeholders** — mapear quem pode ajudar a validar as hipóteses críticas (ex: quem decide se integração é obrigatória)
- **Métricas** — definir como medir se as hipóteses foram confirmadas após o lançamento
- **Plano de execução** — incorporar as validações críticas no início do desenvolvimento
