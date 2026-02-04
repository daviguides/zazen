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
| 2026-02-03 | 010 | Test Case Fixes | Em andamento | [→](./2026-02-03-session-010.md) |


## Quick Resume

**Ultima sessao**: 010 (2026-02-03)
**Fase atual**: Test Case Fixes
**Proximo passo**: Investigar RF-004 e ST-010

**Status**: EM ANDAMENTO
- EH-020: Prompt corrigido (PASS)
- EH-023: Removido (duplicacao desnecessaria)
- EH-001, EH-003, ZN-003: Test cases corrigidos (PASS)
- RF-004, ST-010: Fix aplicado mas ainda PARTIAL

**Para continuar**:

1. Ler sessao atual:
```bash
@./2026-02-03-session-010.md
```

2. Investigar RF-004 e ST-010:
```bash
cd /Users/daviguides/work/sources/gradients/testers/zazen-tester
cat data/versions/1.1.1/analyses/RF-004.yaml
cat data/versions/1.1.1/analyses/ST-010.yaml
```

**Commits recentes**:
- `74cb69e` (zazen) - docs: add session 010 - test case fixes
- `9777ec2` (zazen) - fix: remove Document Error Conditions from spec
- `cbee1a6` (gradient-tester) - fix: relax 5 overly strict test cases


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
| v3.3.0 | 93 | 100% (EH-023 removed) |

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
| **Zazen** | Core zen principles (naming, structure, errors) | 93 | zazen-tester |
| **Kinhin** | TDD practices (red-green-refactor) | 45 | kinhin-tester |
| **Shodo** | Python standards (style, libs, testing) | 57 | shodo-tester |
| **Total** | | 195 | |


## Origem

Zazen foi criado a partir do split de Code-Zen.
Kinhin foi extraido do Zazen para separar TDD.
Shodo foi extraido do Zazen para separar Python.
