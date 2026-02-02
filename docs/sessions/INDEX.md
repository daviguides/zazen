# Zazen Sessions Index

Registro de sessoes do projeto de size reduction.


## Sessoes

| Data | Sessao | Fase | Status | Link |
|------|--------|------|--------|------|
| 2026-02-01 | 001 | Fase 0: Split | Concluido | [→](./2026-02-01-phase0-split.md) |
| 2026-02-01 | 002 | Fase 0.5: Site | Concluido | [→](./2026-02-01-phase05-site.md) |
| 2026-02-01 | 003 | Fase 1: Tester | Concluido | [→](./2026-02-01-phase1-tester.md) |
| 2026-02-01 | 004 | Fase 2: Kinhin | Concluido | [→](./2026-02-01-phase2-kinhin.md) |
| 2026-02-02 | 005 | Fase 3: Shodo | Concluido | [→](./2026-02-02-phase3-shodo.md) |


## Quick Resume

**Ultima sessao**: 005 (2026-02-02)
**Fase atual**: 3 - Shodo Split + Incremental Saving (concluido)
**Proximo passo**: Rodar baselines Zazen + Kinhin + Shodo

**Novidade**: Incremental response saving implementado em todos os testers
- Respostas salvas em `responses/` (1 YAML por test)
- Recovery automatico de falhas (pula testes ja completos)
- Flag `--force` para re-rodar todos os testes

**Para continuar**:

1. Rodar baseline Zazen (94 tests):
```bash
cd /Users/daviguides/work/sources/gradients/testers/zazen-tester
uv run zazen-test baseline
```

2. Rodar baseline Kinhin (45 tests):
```bash
cd /Users/daviguides/work/sources/gradients/testers/kinhin-tester
uv run kinhin-test baseline
```

3. Rodar baseline Shodo (57 tests):
```bash
cd /Users/daviguides/work/sources/gradients/testers/shodo-tester
uv run shodo-test baseline
```

4. Documentar pass rates

**Dica**: Se falhar no meio, basta rodar novamente (pula os ja completos).
Use `--force` para forcar re-execucao de todos.


## Metricas

| Versao | Data | Bundle KB | Pass Rate | Delta |
|--------|------|-----------|-----------|-------|
| v0.1.0 (split) | 2026-02-01 | 258 | TBD | - |


## Test Cases Coverage

### Zazen (core zen principles)

| Versao | Test Cases | Cobertura |
|--------|------------|-----------|
| v3.0.0 | 196 | 100% (pre-split) |
| v3.1.0 | 151 | 100% (post-kinhin) |
| v3.2.0 | 94 | 100% (post-shodo) |

**Grupos**: NM, ST, EH, ZN, RF, PS


### Kinhin (TDD)

| Versao | Test Cases | Cobertura |
|--------|------------|-----------|
| v1.0.0 | 45 | 100% |

**Grupos**: TD, TDH


### Shodo (Python)

| Versao | Test Cases | Cobertura |
|--------|------------|-----------|
| v1.0.0 | 57 | 100% |

**Grupos**: PY, PYS, PYL, PYT


## Projetos Split

| Projeto | Foco | Test Cases | Tester |
|---------|------|------------|--------|
| **Zazen** | Core zen principles (naming, structure, errors) | 94 | zazen-tester |
| **Kinhin** | TDD practices (red-green-refactor) | 45 | kinhin-tester |
| **Shodo** | Python standards (style, libs, testing) | 57 | shodo-tester |
| **Total** | | 196 | |


## Origem

Zazen foi criado a partir do split de Code-Zen.
Kinhin foi extraido do Zazen para separar TDD.
Shodo foi extraido do Zazen para separar Python.
