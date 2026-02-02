# Zazen Sessions Index

Registro de sessoes do projeto de size reduction.


## Sessoes

| Data | Sessao | Fase | Status | Link |
|------|--------|------|--------|------|
| 2026-02-01 | 001 | Fase 0: Split | Concluido | [→](./2026-02-01-phase0-split.md) |
| 2026-02-01 | 002 | Fase 0.5: Site | Concluido | [→](./2026-02-01-phase05-site.md) |
| 2026-02-01 | 003 | Fase 1: Tester | Concluido | [→](./2026-02-01-phase1-tester.md) |
| 2026-02-01 | 004 | Fase 2: Kinhin | Concluido | [→](./2026-02-01-phase2-kinhin.md) |


## Quick Resume

**Ultima sessao**: 004 (2026-02-01)
**Fase atual**: 2 - Kinhin Split (concluido)
**Proximo passo**: Rodar baselines Zazen + Kinhin

**Para continuar**:

1. Rodar baseline Zazen (151 tests):
```bash
cd /Users/daviguides/work/sources/gradients/testers/zazen-tester
uv run zazen-test baseline
```

2. Rodar baseline Kinhin (45 tests):
```bash
cd /Users/daviguides/work/sources/gradients/testers/kinhin-tester
uv run kinhin-test baseline
```

3. Documentar pass rates


## Metricas

| Versao | Data | Bundle KB | Pass Rate | Delta |
|--------|------|-----------|-----------|-------|
| v0.1.0 (split) | 2026-02-01 | 258 | TBD | - |


## Test Cases Coverage

### Zazen (code quality)

| Versao | Test Cases | Cobertura |
|--------|------------|-----------|
| v3.0.0 | 196 | 100% (pre-split) |
| v3.1.0 | 151 | 100% (post-split) |

**Grupos**: NM, ST, EH, ZN, PY, PYS, PYL, PYT, RF, PS


### Kinhin (TDD)

| Versao | Test Cases | Cobertura |
|--------|------------|-----------|
| v1.0.0 | 45 | 100% |

**Grupos**: TD, TDH


## Projetos Split

| Projeto | Foco | Test Cases | Tester |
|---------|------|------------|--------|
| **Zazen** | Code quality | 151 | zazen-tester |
| **Kinhin** | TDD practices | 45 | kinhin-tester |
| **Total** | | 196 | |


## Origem

Zazen foi criado a partir do split de Code-Zen.
Kinhin foi extraido do Zazen para separar TDD.
