# Zazen Sessions Index

Registro de sessoes do projeto de size reduction.


## Sessoes

| Data | Sessao | Fase | Status | Link |
|------|--------|------|--------|------|
| 2026-02-01 | 001 | Fase 0: Split | Concluido | [→](./2026-02-01-phase0-split.md) |
| 2026-02-01 | 002 | Fase 0.5: Site | Concluido | [→](./2026-02-01-phase05-site.md) |
| 2026-02-01 | 003 | Fase 1: Tester | Em progresso | [→](./2026-02-01-phase1-tester.md) |


## Quick Resume

**Ultima sessao**: 003 (2026-02-01)
**Fase atual**: 1 - Tester (em progresso)
**Proximo passo**: Rodar baseline

**Para continuar**:

1. Ler ultima sessao:
@./2026-02-01-phase1-tester.md

2. Instalar dependencias:
```bash
cd /Users/daviguides/work/sources/gradients/testers/zazen-tester
uv sync
```

3. Rodar baseline:
```bash
uv run zazen-test baseline
```

4. Documentar pass rate


## Metricas

| Versao | Data | Bundle KB | Pass Rate | Delta |
|--------|------|-----------|-----------|-------|
| v0.1.0 (split) | 2026-02-01 | 258 | TBD | - |


## Origem

Zazen foi criado a partir do split de Code-Zen.
Historico anterior: `/gradients/zazen/docs/sessions/`
