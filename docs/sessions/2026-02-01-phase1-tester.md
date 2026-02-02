# Session: Phase 1 - Zazen Tester

**Data**: 2026-02-01
**Fase**: 1 - Baseline + zazen-tester
**Status**: Em progresso


## Objetivo

Criar zazen-tester para medir conformidade com principios Zazen.


## Acoes Executadas

### 1. Repo gradient-tester criado
- **URL**: github.com/daviguides/gradient-tester (privado)
- **Local**: `/gradients/testers/`

### 2. arche-tester movido
- **De**: `/gradients/arche/arche-tester/`
- **Para**: `/gradients/testers/arche-tester/`

### 3. zazen-tester criado
Baseado no arche-tester, adaptado para principios Zazen.

**Estrutura**:
```
zazen-tester/
├── zazen_tester/
│   ├── agents/           # BaseAgent, ZazenTestAgent, AnalyzerAgent
│   ├── cli.py            # Typer CLI
│   ├── runner.py         # fork_session + parallel
│   ├── analyzer.py       # Conformity analysis
│   ├── models.py         # Pydantic models
│   ├── config.py         # Settings
│   └── display.py        # Rich output
├── data/
│   ├── test-cases/       # functional-tests.yaml (196 casos)
│   └── mock-project/     # Projeto isolado para testes
├── CLAUDE.md
├── README.md
└── pyproject.toml
```

### 4. Casos de teste completos (v3.0.0)

**Fase 1 - Críticos:**

| Categoria | ID Prefix | Testes |
|-----------|-----------|--------|
| Naming | NM-* | 17 |
| Structure | ST-* | 15 |
| Error Handling | EH-* | 25 |
| Zen Principles | ZN-* | 15 |
| Python Language | PY-* | 15 |
| TDD (base) | TD-001 a TD-010 | 10 |

**Fase 2 - Expandido:**

| Categoria | ID Prefix | Testes |
|-----------|-----------|--------|
| Python Style | PYS-* | 19 |
| Python Libraries | PYL-* | 8 |
| Python Testing Tools | PYT-* | 15 |
| TDD (expandido) | TD-011 a TD-025 | 15 |
| Red Flags / Anti-Patterns | RF-* | 8 |

**Fase 3 - Completo:**

| Categoria | ID Prefix | Testes |
|-----------|-----------|--------|
| Project Setup | PS-* | 14 |
| TDD Hypothesis / Advanced | TDH-* | 20 |

**Total**: 196 casos de teste

### 5. Analise de cobertura

| Metrica | Valor |
|---------|-------|
| Regras identificadas no bundle | 196 |
| Regras com test cases | 196 |
| Cobertura | **100%** |

### 6. Feature --group para testes por categoria

Implementado filtro `--group` / `-g` para rodar subconjuntos de testes durante size reduction.

**Comandos atualizados**:
- `zazen-test run <version> -g <PREFIX>`
- `zazen-test baseline -g <PREFIX>`

**Suporta múltiplos grupos** (comma-separated):
```bash
zazen-test run 0.1.0 -g NM,ST,EH
```

**Grupos disponíveis**:

| Grupo | Testes | Area |
|-------|--------|------|
| NM | 17 | Naming |
| ST | 15 | Structure |
| EH | 25 | Error Handling |
| ZN | 15 | Zen Principles |
| PY | 15 | Python Language |
| TD | 25 | TDD |
| PYS | 19 | Python Style |
| PYL | 8 | Python Libraries |
| PYT | 15 | Python Testing |
| RF | 8 | Red Flags |
| PS | 14 | Project Setup |
| TDH | 20 | TDD Advanced |

**Arquivos modificados**:
- `zazen_tester/cli.py` - opcao --group
- `zazen_tester/runner.py` - filtro _filter_test_cases
- `CLAUDE.md` - documentacao completa

**Referencia adicionada** no CLAUDE.md do zazen principal.


## Arquivos Criados

**Repo testers/**:
- `.gitignore`
- `README.md`

**zazen-tester/**:
- `pyproject.toml`
- `CLAUDE.md`
- `README.md`
- `.gitignore`
- `zazen_tester/__init__.py`
- `zazen_tester/config.py`
- `zazen_tester/models.py`
- `zazen_tester/utils.py`
- `zazen_tester/display.py`
- `zazen_tester/runner.py`
- `zazen_tester/analyzer.py`
- `zazen_tester/comparator.py`
- `zazen_tester/cli.py`
- `zazen_tester/agents/__init__.py`
- `zazen_tester/agents/base_agent.py`
- `zazen_tester/agents/zazen_test_agent.py`
- `zazen_tester/agents/analyzer_agent.py`
- `data/test-cases/functional-tests.yaml` (v3.0.0 - 196 casos)
- `data/mock-project/src/*.py`
- `data/mock-project/tests/*.py`


## Proximos Passos

1. [x] `uv sync` no zazen-tester
2. [ ] Rodar `uv run zazen-test baseline`
3. [ ] Documentar pass rate inicial
4. [ ] Atualizar metricas no INDEX


## Comandos

```bash
cd /Users/daviguides/work/sources/gradients/testers/zazen-tester
uv sync
uv run zazen-test baseline
```


## Decisoes

### D1: Monorepo gradient-tester
Testers em repo separado para manter plugins limpos.

### D2: Principios Zazen como enum
Criado enum `Principle` com: naming, structure, simplicity, clarity, pythonic, type-safety, docstrings, test-first, red-green-refactor.

### D3: Carrega /zazen:load-all-context
ZazenTestAgent carrega principios via skill `/zazen:load-all-context`.

### D4: Expansao de test cases para 196 (100% cobertura)
Analise profunda do bundle Zazen identificou 196 regras testaveis.
Implementados 196 test cases (100% cobertura) em três fases:
- Fase 1: Críticos (97 testes)
- Fase 2: Expandido (+65 testes)
- Fase 3: Completo (+34 testes)

### D5: Filtro --group para iteracao rapida
196 testes levam ~30min. Durante size reduction, rodar apenas grupos relevantes:
- Modificou naming? `--group NM`
- Modificou TDD? `--group TD,TDH`
- Modificou Python? `--group PY,PYS,PYL,PYT`

### D6: Haiku como modelo default
Haiku é ~3-4x mais rápido e mais barato. Lógica: se Haiku segue os princípios, modelos maiores certamente seguirão.

### D7: Multiprocessing mode
Implementado modo multiprocessing (`--multiprocess` / `-p`) como alternativa ao asyncio para comparar performance.


## Historico de Versoes (functional-tests.yaml)

| Versao | Test Cases | Cobertura | Data |
|--------|------------|-----------|------|
| v1.0.0 | 14 | 7% | 2026-02-01 |
| v2.0.0 | 97 | 50% | 2026-02-01 |
| v2.1.0 | 162 | 83% | 2026-02-01 |
| v3.0.0 | 196 | **100%** | 2026-02-01 |


---

## Quick Resume

**Workflow**: size-reduction / tester-development
**Current Phase**: IMPLEMENTING (baseline em execução)
**Next Phase**: VALIDATING (analisar resultados)
**Required Context**: `/zazen:load`

## Current State

**Last Action**: Implementado modo multiprocessing para comparar performance com asyncio.
**Baseline rodando**: `uv run zazen-test baseline -c 15` (asyncio mode)

**Next Steps**:
1. Aguardar baseline completar
2. Comparar asyncio vs multiprocessing (`-p` flag)
3. Documentar pass rate inicial
4. Atualizar métricas no INDEX

**Blockers**: Nenhum

## Commit History (zazen-tester)

| Data | Commit | Descrição |
|------|--------|-----------|
| 2026-02-01 | 3b1029e | feat: add multiprocessing mode |
| 2026-02-01 | 22b72f9 | fix: use haiku as default |
| 2026-02-01 | a49912a | feat: add --model option |
| 2026-02-01 | aa8723b | fix: fair comparison with --group |
| 2026-02-01 | 224c4ee | fix: load all 3 zazen contexts |

## Session Notes

### 2026-02-01 (Session 4 - Checkpoint)
- Baseline rodando com Haiku, -c 15
- Implementado multiprocessing como alternativa
- Estimativa ~40min para 196 testes com asyncio
- Próxima sessão: extrair TDD para Kinhin

---

## Próxima Sessão: Fase 2 - Kinhin Split

### Objetivo

Extrair tudo relacionado a TDD do Zazen para um novo projeto **Kinhin** (禅歩 - meditação caminhando).

**Filosofia**: Kinhin é a prática da meditação caminhando no Zen Budismo, servindo como transição ativa entre períodos de zazen. Analogamente, TDD é desenvolvimento em passos - red, green, refactor.

### Escopo da Extração

**Do Zazen, mover para Kinhin:**

| Tipo | Arquivos Zazen | Destino Kinhin |
|------|----------------|----------------|
| Spec | `zazen/spec/tdd/` | `kinhin/spec/tdd/` |
| Context | `zazen/context/guides/tdd-*.md` | `kinhin/context/guides/` |
| Prompts | `zazen/prompts/load-tdd-*.md` | `kinhin/prompts/` |
| Commands | `commands/load-tdd-context.md` | `commands/load.md` |

**Do zazen-tester, mover para kinhin-tester:**

| Grupo | Test Cases | IDs |
|-------|------------|-----|
| TD | 25 | TD-001 a TD-025 |
| TDH | 20 | TDH-001 a TDH-020 |
| **Total** | **45** | |

### Tarefas

1. **Criar projeto Kinhin**
   - [ ] Criar repo `kinhin/` em `/gradients/`
   - [ ] Estrutura Gradient padrão (spec/, context/, prompts/, commands/)
   - [ ] Copiar specs TDD do Zazen
   - [ ] Criar skill `/kinhin:load`

2. **Criar kinhin-tester**
   - [ ] Criar em `/gradients/testers/kinhin-tester/`
   - [ ] Extrair test cases TD-* e TDH-* do functional-tests.yaml
   - [ ] Adaptar para carregar `/kinhin:load`
   - [ ] Rodar baseline Kinhin

3. **Limpar Zazen**
   - [ ] Remover specs TDD
   - [ ] Remover test cases TD-* e TDH-* do zazen-tester
   - [ ] Atualizar `/zazen:load` (remover referência TDD)
   - [ ] Rodar baseline Zazen (agora 151 testes)

4. **Validar ambos**
   - [ ] Baseline Kinhin (45 testes)
   - [ ] Baseline Zazen (151 testes)
   - [ ] Documentar pass rates

### Resultado Esperado

| Projeto | Foco | Test Cases |
|---------|------|------------|
| Zazen | Code quality (naming, structure, zen, python) | 151 |
| Kinhin | TDD practices | 45 |
| **Total** | | 196 |

### Comandos para Próxima Sessão

```bash
# 1. Verificar baseline Zazen atual
cd /Users/daviguides/work/sources/gradients/testers/zazen-tester
ls -la data/versions/0.1.0/

# 2. Criar Kinhin
cd /Users/daviguides/work/sources/gradients
mkdir -p kinhin/{spec,context,prompts,commands,skills}

# 3. Criar kinhin-tester
cd /Users/daviguides/work/sources/gradients/testers
cp -r zazen-tester kinhin-tester
# ... adaptar
```
