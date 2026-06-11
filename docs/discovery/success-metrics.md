# Métricas de Sucesso — Notification Hub

> Gerado em: 29/05/2026
> Versão: 1.0
> Responsável: Bruno Alves

---

## Objetivo Central

Facilitar o recebimento e gerenciamento de notificações pelos usuários, permitindo que cada um filtre apenas o que é relevante para ele — medido pelo engajamento real com as notificações recebidas.

---

## North Star Metric

> **% de notificações lidas pelos usuários**

Esta métrica captura o valor central do hub: se as notificações são relevantes e chegam no lugar certo, os usuários as leem. Quando esta métrica está alta, significa que os sistemas estão integrados, as preferências estão configuradas e a entrega está funcionando.

| Aspecto | Valor |
|---------|-------|
| **Meta** | 80% das notificações lidas |
| **Baseline** | A medir a partir do lançamento |
| **Prazo** | 3 meses após o go-live (até 05/09/2026) |
| **Responsável** | Bruno Alves |

---

## Métricas de Negócio

| Métrica | Descrição | Baseline | Meta | Prazo | Responsável |
|---------|-----------|----------|------|-------|-------------|
| % de sistemas integrados ao hub | Cobertura de sistemas da empresa publicando no hub | 0% | 100% | 3 meses pós-lançamento | Bruno Alves |
| Redução de implementações duplicadas | Novos sistemas não precisam criar seu próprio sistema de notificações | A medir | 0 implementações paralelas | Contínuo | Bruno Alves |
| Tempo médio de integração de um sistema | Mede facilidade de adoção da API/Broker pelos times de desenvolvimento | A medir na 1ª integração | A definir após 1ª integração | Contínuo | Bruno Alves |

---

## Métricas de Produto / Usuário (HEART)

| Framework | Métrica | Descrição | Baseline | Meta | Prazo | Responsável |
|-----------|---------|-----------|----------|------|-------|-------------|
| **Retention** | % de usuários que voltam ao hub na 1ª semana | Mede se o hub se torna parte da rotina do usuário | A medir | 60% | 1 mês pós-lançamento | Bruno Alves |
| **Task Success** | % de usuários que configuraram pelo menos uma preferência | Mede adoção ativa do controle de notificações | A medir | 70% | 3 meses pós-lançamento | Bruno Alves |

---

## Critérios de Aceitação do Go-Live

Critérios mínimos para considerar o lançamento da Fase 1 bem-sucedido:

- [ ] Usuário consegue visualizar todas as notificações em um único lugar
- [ ] Notificações chegam em tempo real para usuários logados no navegador
- [ ] Pelo menos 1 sistema integrado publicando notificações via API/Broker

---

## Conexão com Hipóteses Críticas

> As métricas abaixo também validam hipóteses levantadas em `assumptions.md`.

| Hipótese | Métrica que valida | Como interpretar |
|----------|--------------------|-----------------|
| H1 — Usuários vão configurar preferências ativamente | % usuários com preferência configurada (meta: 70%) | < 30% indica que o onboarding precisa ser melhorado |
| H2 — Usuários preferirão o hub aos sistemas individuais | % usuários que voltam na 1ª semana (meta: 60%) | < 30% indica resistência à adoção |
| H4 — Sistemas internos vão aderir à integração | % sistemas integrados (meta: 100%) | < 50% indica necessidade de tornar integração obrigatória |
| H8 — Broker suporta o volume de notificações | Taxa de erro de entrega de notificações | > 1% de erro indica problema de capacidade |

---

## Instrumentação Necessária

Para medir as métricas acima, os seguintes dados precisam ser capturados:

| Dado | Onde capturar | Prioridade |
|------|--------------|------------|
| Notificação lida/não lida | Banco de dados — evento de leitura | Alta |
| Usuário acessou o hub | Log de acesso / analytics | Alta |
| Usuário configurou preferência | Evento no backend ao salvar preferência | Alta |
| Sistema integrado publicou notificação | Log do broker/API com identificação do remetente | Alta |
| Tempo de entrega da notificação | Timestamp de envio vs. recebimento | Média |

---

## Pontos a Refinar

- [ ] Definir ferramenta de analytics/observabilidade para acompanhar métricas (ex: Grafana, Application Insights, Kibana)
- [ ] Definir baseline real após as primeiras 2 semanas de uso em produção
- [ ] Revisar metas com base no baseline real — ajustar se necessário
- [ ] Definir ritual de acompanhamento: frequência e formato do review de métricas

---

## Próximos Passos Sugeridos

Com as métricas definidas, o discovery está fundamentado. Próximos passos:
- **Especificação Funcional** — detalhar regras de negócio de cada funcionalidade em BDD
- **Plano de Execução** — definir sprints e entregas para a Fase 1
