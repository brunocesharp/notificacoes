# Áreas de Domínio — Mapeamento para Documentação

Este arquivo define as áreas do domínio OPBH, os arquivos de documentação correspondentes
e os arquivos de código a analisar em cada área.

---

## Área: Sistema de Fila

**Arquivo destino:** `docs/business/fila.md`

**Código a analisar:**
- `backend/src/OPBH.Domain/Entities/Participante.cs`
- `backend/src/OPBH.Application/Services/FilaService.cs`
- `backend/src/OPBH.Application/Validators/` (arquivos relacionados a fila)
- `backend/src/OPBH.Infrastructure/Repositories/ParticipanteRepository.cs`

**Regras esperadas (do REGRAS_NEGOCIO.md existente):**
- Pontuação por presença (+2 por encontro)
- Reset após apresentação
- Mínimo de 1 presença para entrar na fila
- Desempate por última apresentação
- Saída voluntária zera pontuação

**Complexidade estimada:** 5-7 regras → 1 task (~45min)

---

## Área: Participantes

**Arquivo destino:** `docs/business/participantes.md`

**Código a analisar:**
- `backend/src/OPBH.Domain/Entities/Participante.cs`
- `backend/src/OPBH.Application/Services/ParticipanteService.cs`
- `backend/src/OPBH.Application/Validators/` (arquivos de participante)
- `backend/src/OPBH.Application/DTOs/Participante/`

**Regras esperadas:**
- Código sequencial (P + 4 dígitos)
- Unicidade de código e email
- Validação de formato de Instagram (@)
- Validação de email
- Flag `desconsiderar_fila`

**Complexidade estimada:** 4-6 regras → 1 task (~30min)

---

## Área: Projetos e Autorias

**Arquivo destino:** `docs/business/projetos.md`

**Código a analisar:**
- `backend/src/OPBH.Domain/Entities/Projeto.cs`
- `backend/src/OPBH.Domain/Entities/Autoria.cs`
- `backend/src/OPBH.Application/Services/ProjetoService.cs`
- `backend/src/OPBH.Application/Validators/` (arquivos de projeto)

**Regras esperadas:**
- Código sequencial (J + 4 dígitos)
- Máximo de 3 autores por projeto
- Autor principal (ordem = 1)
- Reset de pontuação de todos os autores ao apresentar
- Contagem de vezes apresentado

**Complexidade estimada:** 5-7 regras → 1 task (~40min)

---

## Área: Encontros e Presença

**Arquivo destino:** `docs/business/encontros.md`

**Código a analisar:**
- `backend/src/OPBH.Domain/Entities/Encontro.cs`
- `backend/src/OPBH.Domain/Entities/Presenca.cs`
- `backend/src/OPBH.Application/Services/EncontroService.cs`
- `backend/src/OPBH.Application/Validators/` (arquivos de encontro)

**Regras esperadas:**
- Código sequencial (E + 4 dígitos)
- Unicidade de presença por encontro
- Histórico imutável (encontros passados não podem ser excluídos)
- Data do encontro limitada (máx 30 dias no futuro)

**Complexidade estimada:** 4-6 regras → 1 task (~35min)

---

## Área: Apresentações

**Arquivo destino:** `docs/business/apresentacoes.md`

**Código a analisar:**
- `backend/src/OPBH.Domain/Entities/Apresentacao.cs`
- `backend/src/OPBH.Application/Services/EncontroService.cs` (método de apresentação)
- Testes relacionados a apresentações

**Regras esperadas:**
- Uma apresentação por projeto por encontro
- Atualiza estatísticas do projeto (vezes apresentado, data última apresentação)
- Dispara reset de pontuação dos autores (RN02 + RN08)

**Complexidade estimada:** 3-5 regras → 1 task (~25min)

---

## Área: Autenticação e Controle de Acesso

**Arquivo destino:** `docs/business/auth.md`

**Código a analisar:**
- `backend/src/OPBH.Domain/Entities/User.cs`
- `backend/src/OPBH.Domain/Enums/UserRole.cs`
- `backend/src/OPBH.Application/Services/AuthService.cs`
- `backend/src/OPBH.Infrastructure/Services/JwtService.cs`
- `backend/src/OPBH.API/Controllers/AuthController.cs`

**Regras esperadas:**
- Papéis: Admin e Participante
- Regras de acesso por papel (quem pode fazer o quê)
- Expiração de token JWT

**Complexidade estimada:** 3-5 regras → 1 task (~30min)

---

## Área: Códigos Sequenciais

**Arquivo destino:** `docs/business/codigos-sequenciais.md`

**Código a analisar:**
- `backend/src/OPBH.Application/Services/` (métodos de geração de código)
- `backend/src/OPBH.Domain/Entities/` (campos Codigo nas entidades)

**Regras esperadas:**
- Formato E/P/J + 4 dígitos
- Geração automática sequencial
- Imutabilidade do código após criação

**Complexidade estimada:** 2-4 regras → 1 task (~20min)

---

## Prioridade de execução

Execute nesta ordem (da mais crítica à mais periférica):

1. `fila.md` — núcleo do sistema
2. `projetos.md` — entidade central de valor
3. `encontros.md` — evento principal
4. `apresentacoes.md` — efeitos colaterais críticos
5. `participantes.md` — cadastro base
6. `codigos-sequenciais.md` — infraestrutura de identidade
7. `auth.md` — controle de acesso

---

## Como identificar novas áreas

Se durante a análise do código você encontrar lógica de negócio não coberta acima:

1. Verifique se cabe em uma área existente
2. Se não couber, crie um novo arquivo com nome kebab-case
3. Adicione a área neste arquivo para referência futura
4. Estime complexidade e decida se merece task própria ou pode ser adicionada a uma existente
