---
description: Discovery de visão de produto — coleta objetivos, stakeholders, escopo e decisões de arquitetura para iniciar ou evoluir o projeto
---

# Discovery de Visão

Use este comando no início de um projeto, ou de uma nova fase, para estruturar a visão antes de codar.

## Objetivo

Conduzir uma conversa de discovery com o usuário para preencher (ou atualizar) o `CLAUDE.md` com:

1. **Visão e motivação**: qual problema este projeto resolve e por quê agora
2. **Usuários e stakeholders**: quem usa o sistema, quem são os sistemas integrados/consumidores
3. **Escopo (MVP vs. futuro)**: o que entra na primeira versão e o que fica para depois
4. **Conceitos de domínio**: principais entidades e seus relacionamentos
5. **Decisões de arquitetura**: stack, persistência, integração, entrega/canais
6. **Critérios de sucesso**: como saber que o projeto está funcionando

## Como conduzir

1. Leia o `CLAUDE.md` atual (se existir) para não repetir perguntas já respondidas.
2. Faça perguntas objetivas, agrupadas por tema, usando `AskUserQuestion` quando houver decisões a tomar (ex.: stack, banco, canais).
3. Para perguntas abertas (motivação, usuários, critérios de sucesso), peça respostas livres em texto.
4. Não avance para implementação enquanto a visão não estiver minimamente definida (escopo do MVP + stack).
5. Ao final, atualize o `CLAUDE.md` com as respostas, organizando em seções claras (Visão, Escopo, Domínio, Arquitetura, Próximos Passos).
6. Não invente respostas: se o usuário não souber ou adiar uma decisão, registre como "a definir" e siga em frente.

## Saída esperada

- `CLAUDE.md` atualizado refletindo a visão acordada
- Lista curta de próximos passos acionáveis (scaffolding, definição de schema, etc.)
