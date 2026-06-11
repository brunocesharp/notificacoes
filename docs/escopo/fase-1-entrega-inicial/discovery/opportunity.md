# Mapeamento de Oportunidades — Notification Hub

> Gerado em: 29/05/2026
> Versão: 1.0

---

## Jobs to Be Done

| Perfil | Situação | Motivação | Resultado Esperado |
|--------|----------|-----------|-------------------|
| **Usuário Final** | Quando acessa o hub | Quer visualizar todas as notificações recebidas | Ver tudo em um único lugar, sem precisar acessar cada sistema |
| **Usuário Final** | Quando configura suas preferências | Quer escolher quais notificações receber e por qual canal | Receber apenas o que é relevante para ele |
| **Administrador** | Quando gerencia o hub | Quer controlar permissões e tipos de notificação disponíveis | Garantir que usuários recebam apenas notificações adequadas ao seu perfil |
| **Sistema Integrado** | Quando um job é executado ou evento ocorre | Quer disparar uma notificação para os usuários elegíveis | Notificação enviada com sucesso (fire and forget — sem confirmação de leitura) |

---

## Dores e Fricções

### Críticas

| Perfil | Dor | Impacto |
|--------|-----|---------|
| **Usuário Final** | Recebe notificações irrelevantes de sistemas que não usa | Ruído e perda de foco |
| **Usuário Final** | Perde notificações importantes por não estar no sistema correto | Falhas de comunicação e retrabalho |
| **Usuário Final** | Precisa acessar vários sistemas para ver todas as notificações | Perda de tempo e experiência fragmentada |
| **Administrador** | Não possui central para gerenciar notificações de todos os sistemas | Falta de controle e visibilidade |
| **Times de Desenvolvimento** | Não existe serviço centralizado para envio de notificações automáticas | Cada sistema precisa implementar sua própria solução, gerando retrabalho |

### Secundárias

| Perfil | Dor | Impacto |
|--------|-----|---------|
| **Administrador** | Sem rastreabilidade de qual sistema enviou cada notificação | Dificuldade para auditar e depurar problemas |
| **Times de Desenvolvimento** | Sem padrão de integração entre sistemas para notificações | Inconsistência e custo de manutenção elevado |

---

## Desejos e Ganhos

| Perfil | Desejo | Valor Esperado |
|--------|--------|---------------|
| **Usuário Final** | Notificações com **link direto** para o sistema/contexto que originou o evento | Acesso rápido sem precisar navegar manualmente |
| **Usuário Final** | Badge de contagem de notificações não lidas | Consciência situacional sem precisar abrir o hub |
| **Usuário Final** | Marcar notificações como lidas / histórico de notificações | Controle e rastreabilidade pessoal |
| **Administrador** | Tela de busca de notificações com **múltiplos filtros** (sistema, tipo, usuário, data, status) | Auditoria, suporte e visibilidade operacional |

---

## Contexto de Uso

| Aspecto | Descrição |
|---------|-----------|
| **Frequência** | Uso rotineiro — diário, durante a jornada de trabalho |
| **Tempo real** | Sim — notificações devem aparecer enquanto o usuário está logado (WebSocket/SSE) |
| **Ambiente** | Navegador desktop — sem requisito de mobile na v1 |
| **Urgência** | Média a alta — notificações de jobs e eventos de sistema podem exigir ação imediata |

---

## Tentativas Anteriores

Nenhuma tentativa anterior identificada. Este é o primeiro esforço para centralizar notificações na empresa.

**Implicação:** Não há histórico de fracassos para aprender, mas também não há resistência a mudanças ou vícios de uso a quebrar. A adoção dependerá da qualidade da integração e da experiência do usuário.

---

## Árvore de Oportunidades (Opportunity Solution Tree)

```
Objetivo: Unificar notificações dos sistemas internos com controle por usuário
│
├── Oportunidade 1: Usuário recebe notificações irrelevantes
│   └── Permitir configuração de preferências por sistema e tipo
│
├── Oportunidade 2: Usuário perde notificações importantes
│   └── Entrega em tempo real (WebSocket) + badge de não lidas
│
├── Oportunidade 3: Usuário precisa acessar múltiplos sistemas
│   └── Hub centralizado com todas as notificações em um único lugar
│
├── Oportunidade 4: Notificações sem contexto de ação
│   └── Links diretos para o sistema/contexto de origem
│
├── Oportunidade 5: Administrador sem visibilidade central
│   └── Painel administrativo com busca e filtros avançados
│
└── Oportunidade 6: Times de dev sem padrão de integração
    └── API/Broker padronizado com documentação clara
```

---

## Pontos a Investigar

- [ ] Quais filtros são mais importantes para o administrador? (sistema, tipo, usuário, período, status de leitura)
- [ ] O link de redirecionamento das notificações deve ser configurado pelo sistema integrado ou pelo administrador?
- [ ] Qual o comportamento esperado quando o usuário clica em uma notificação com link — abre na mesma aba ou nova aba?
- [ ] Há necessidade de notificações em lote (ex: "5 jobs finalizaram") ou sempre individuais?
- [ ] Como tratar notificações para usuários que estão offline no momento do envio?

---

## Próximos Passos Sugeridos

Com as oportunidades mapeadas, as próximas etapas recomendadas são:
- **Hipóteses** — transformar oportunidades em premissas a validar antes de construir
- **Stakeholders** — identificar os times responsáveis pelos sistemas que vão integrar
- **Métricas** — definir como medir se estamos endereçando as oportunidades certas
