---
name: business-docs
description: Analisa código implementado e gera documentação de regras de negócio em docs/business/. Use quando o usuário mencionar "documentar regras de negócio", "gerar docs de negócio", "business docs", "documentar domínio", "docs/business", "atualizar documentação de negócio", "documentar lógica de negócio" ou pedir para documentar uma área do sistema. Cria tasks atômicas por área de domínio consultando arquivos existentes antes de escrever.
metadata:
  author: brunocesharp
  version: 1.0.0
---

# Business Documentation Generator

Analisa o código-fonte implementado e documenta regras de negócio em `docs/business/`, uma área por vez, usando tasks atômicas (menos de 1 hora cada).

## Referências obrigatórias

Antes de executar qualquer passo, leia:
- `references/template-business-rule.md` — estrutura padrão de cada arquivo gerado
- `references/areas.md` — mapeamento de áreas para arquivos destino e código-fonte

## Passo 1: Inventário

Liste todos os arquivos em `docs/business/` (Glob: `docs/business/**/*.md`).

Para cada arquivo encontrado, leia e extraia:
- Quais regras (RN-XXX) já estão documentadas
- Qual área está coberta
- Data da última atualização no frontmatter

Se a pasta não existir, ela será criada no Passo 3 ao escrever o primeiro arquivo.

## Passo 2: Análise de código

Para cada área sem cobertura ou desatualizada (conforme `references/areas.md`), analise os arquivos de código correspondentes:

| Camada | Local | O que procurar |
|--------|-------|----------------|
| Domain | `backend/src/OPBH.Domain/Entities/` | Invariantes, construtores com validação, métodos de domínio |
| Application | `backend/src/OPBH.Application/Services/` | Regras orquestradas, validações cross-entity |
| Application | `backend/src/OPBH.Application/Validators/` | Validações de entrada com FluentValidation |
| Infrastructure | `backend/src/OPBH.Infrastructure/Repositories/` | Constraints de dados, queries com filtros de negócio |

Para cada regra encontrada, extraia: trigger, condição, ação e localização no código (arquivo:linha).

## Passo 3: Criar tasks

Use `TaskCreate` para criar uma task por arquivo de documentação a gerar ou atualizar.

**Formato do título:** `[business-docs] Documentar {área}: docs/business/{arquivo}.md`

A descrição de cada task deve incluir:
- Arquivo destino
- Caminhos dos arquivos de código a analisar
- Regras já existentes (se for atualização)
- Regras novas identificadas no Passo 2

IMPORTANT: Se uma área tiver mais de 8 regras, divida em duas tasks com sufixos distintos (ex: `fila-pontuacao.md` e `fila-entrada-saida.md`).

## Passo 4: Executar tasks

Execute na ordem de prioridade definida em `references/areas.md`. Para cada task:

1. Marque como `in_progress`
2. Releia o arquivo existente em `docs/business/` (se houver) para não duplicar regras
3. Analise os arquivos de código listados na task
4. Escreva o arquivo seguindo o template de `references/template-business-rule.md`
5. Marque como `completed`

**Regras de escrita:**
- Não duplicar regras já documentadas — apenas referencie a RN-XXX existente
- Manter numeração sequencial global (próximo = maior existente + 1)
- Documentar apenas o que está implementado no código
- Citar arquivo e linha de cada regra

## Passo 5: Relatório final

Ao concluir todas as tasks, exiba:

```
## Documentação gerada

| Arquivo | Status | Regras documentadas |
|---------|--------|---------------------|
| docs/business/fila.md | criado | RN-001 a RN-005 |

Total: X arquivos, Y regras documentadas
```

## Exemplos

**Exemplo 1: Documentação inicial completa**
Usuário diz: "gera a documentação de regras de negócio do projeto"
Ações:
1. Inventário encontra `docs/business/` vazia
2. Análise identifica 7 áreas com regras no código
3. 7 tasks criadas, uma por área
4. Tasks executadas em ordem de prioridade definida em `references/areas.md`
Resultado: 7 arquivos criados em `docs/business/`

**Exemplo 2: Atualização incremental**
Usuário diz: "atualiza a documentação de negócio da fila"
Ações:
1. Inventário encontra `docs/business/fila.md` com RN-001 a RN-005
2. Análise encontra nova regra implementada em `FilaService.cs`
3. 1 task de atualização criada
4. `fila.md` atualizado com RN-006 adicionada
Resultado: arquivo atualizado sem sobrescrever regras existentes

**Exemplo 3: Área específica**
Usuário diz: "documenta as regras de apresentação de projetos"
Ações:
1. Inventário verifica `docs/business/apresentacoes.md`
2. Analisa `Apresentacao.cs` e método de registro em `EncontroService.cs`
3. 1 task criada e executada
Resultado: `docs/business/apresentacoes.md` criado

## Troubleshooting

**Regra já existe com numeração diferente**
Mantenha a numeração mais antiga. Adicione `(também conhecida como RN-XX)` no cabeçalho da regra.

**Código não encontrado para uma regra**
Documente com `status: pendente-implementacao` e anote que foi identificada apenas em testes ou comentários.

**Área muito grande para uma task**
Divida pelo critério natural do domínio: operações de escrita vs leitura, ou por sub-entidade relacionada.

**Arquivo existente incompleto**
Faça merge: preserve seções existentes, adicione apenas o que falta. Nunca sobrescreva conteúdo já validado.
