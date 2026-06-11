# Stakeholders — Notification Hub

> Gerado em: 29/05/2026
> Versão: 1.0

---

## Stakeholders Identificados

| # | Stakeholder | Papel | Tipo |
|---|-------------|-------|------|
| S1 | Bruno Alves | Arquiteto / Responsável pelo projeto | Interno |
| S2 | Clientes dos sistemas | Solicitantes — usuários dos sistemas que originaram a demanda | Interno |
| S3 | Usuários finais | Colaboradores da empresa que receberão as notificações | Interno |
| S4 | Administradores do hub | Responsáveis pela gestão operacional do Notification Hub | Interno |
| S5 | Times de desenvolvimento | Equipes responsáveis pelos sistemas que integrarão com o hub | Interno |

---

## Matriz de Influência × Interesse

```
Alta influência │ S1 (Arquiteto)        │ S2 (Clientes sistemas)
                │ Manter satisfeito     │ Engajar ativamente ⚡
                ├───────────────────────┼──────────────────────
                │                       │ S4 (Administradores)
Baixa influência│                       │ S3 (Usuários finais)
                │                       │ S5 (Times de dev)
                │                       │ Manter informados 📢
                └───────────────────────┴──────────────────────
                    Baixo interesse          Alto interesse
```

---

## Perfil Detalhado dos Stakeholders

### S1 — Bruno Alves (Arquiteto / Responsável)
| Aspecto | Descrição |
|---------|-----------|
| **Influência** | Alta |
| **Interesse** | Alto |
| **Estratégia** | ⚡ Engajar ativamente |
| **Expectativa** | Entregar v1 até 05/06/2026 com qualidade arquitetural e alinhamento técnico |
| **Decisões** | Toma todas as decisões importantes de arquitetura e escopo |
| **Responsável pela relação** | Próprio |

---

### S2 — Clientes dos Sistemas (Solicitantes)
| Aspecto | Descrição |
|---------|-----------|
| **Influência** | Alta |
| **Interesse** | Alto |
| **Estratégia** | ⚡ Engajar ativamente |
| **Expectativa** | Receber todas as notificações em um único local — essa é a entrega mínima para satisfação |
| **Preocupações** | Nenhuma identificada |
| **Bloqueador potencial** | Não |
| **Responsável pela relação** | Bruno Alves |

---

### S3 — Usuários Finais (Colaboradores)
| Aspecto | Descrição |
|---------|-----------|
| **Influência** | Baixa |
| **Interesse** | Alto |
| **Estratégia** | 📢 Manter informados |
| **Expectativa** | Receber apenas notificações relevantes, no canal preferido, em tempo real |
| **Preocupações** | Curva de adoção — primeiro contato com um hub centralizado |
| **Responsável pela relação** | Bruno Alves |

---

### S4 — Administradores do Hub
| Aspecto | Descrição |
|---------|-----------|
| **Influência** | Média |
| **Interesse** | Alto |
| **Estratégia** | ⚡ Engajar ativamente |
| **Expectativa** | Interface administrativa funcional para gerenciar permissões e tipos de notificação |
| **Preocupações** | Nenhuma identificada |
| **Responsável pela relação** | Bruno Alves |

---

### S5 — Times de Desenvolvimento
| Aspecto | Descrição |
|---------|-----------|
| **Influência** | Média |
| **Interesse** | Médio |
| **Estratégia** | 📢 Manter informados |
| **Expectativa** | API/Broker simples de integrar, com documentação clara e sem grandes mudanças arquiteturais em seus sistemas |
| **Preocupações** | Esforço de integração não planejado nos seus roadmaps |
| **Responsável pela relação** | Bruno Alves |

---

## Plano de Comunicação

| Stakeholder | Canal | Frequência | Responsável | Conteúdo |
|-------------|-------|------------|-------------|----------|
| S2 — Clientes dos sistemas | E-mail | Semanal | Bruno Alves | Status do projeto, marcos atingidos, próximos passos |
| S3 — Usuários finais | E-mail | Semanal | Bruno Alves | Atualizações de funcionalidades, onboarding |
| S4 — Administradores | E-mail | Semanal | Bruno Alves | Novas funcionalidades administrativas, mudanças de configuração |
| S5 — Times de desenvolvimento | E-mail | Semanal | Bruno Alves | Guia de integração, mudanças na API/Broker, documentação |

---

## Riscos de Stakeholder

| Risco | Stakeholder | Probabilidade | Mitigação |
|-------|-------------|---------------|-----------|
| Times de dev não priorizarem a integração | S5 | Média | Definir se integração é obrigatória; oferecer suporte técnico e documentação clara |
| Expectativa dos clientes além do escopo da v1 | S2 | Baixa | Comunicar claramente o escopo da v1 e roadmap de evoluções |
| Baixa adoção pelos usuários finais | S3 | Média | Onboarding guiado e comunicação proativa sobre os benefícios |

---

## Pontos a Refinar

- [ ] Identificar nomes/contatos dos representantes dos clientes dos sistemas para comunicação direta
- [ ] Confirmar se a integração dos sistemas será **obrigatória ou opcional** — impacta diretamente o engajamento do S5
- [ ] Definir quem serão os administradores do hub (papel/área)

---

## Próximos Passos Sugeridos

Com os stakeholders mapeados, fica mais fácil tomar decisões com as pessoas certas. Próximos passos:
- **Métricas de sucesso** — definir como medir o sucesso do projeto para cada stakeholder
- **Escopo** — consolidar tudo em um documento de escopo para a v1
