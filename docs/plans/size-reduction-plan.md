# Zazen Size Reduction Plan

**Data**: 2026-02-01
**Baseline**: 251 KB
**Target**: ~50-60 KB (~75% reducao)


## Fases

### Fase 1: Baseline + zazen-tester
**Sessao**: 2

**Acoes**:
1. Instalar Zazen como plugin
2. Criar zazen-tester (baseado em arche-tester)
3. Definir casos de teste funcionais
4. Rodar baseline
5. Documentar pass rate

**Entregaveis**:
- [ ] zazen-tester criado
- [ ] Casos de teste definidos
- [ ] Baseline de pass rate


### Fase 2: Framework Comum
**Sessao**: 3
**Economia estimada**: 15-20 KB

**Acoes**:
1. Criar `spec/_spec-framework.md`
2. Unificar checklists duplicados
3. Aplicar referencias @


### Fase 3: Consolidacao TDD
**Sessao**: 4
**Economia estimada**: 50-60 KB

**Acoes**:
1. Consolidar 6 examples TDD → 2
2. Consolidar 4 guides TDD → 1
3. Mover detalhes para skill

**Arquivos afetados**:
- tdd-unit-tests.md (14 KB)
- tdd-integration-tests.md (12 KB)
- tdd-anti-patterns.md (13 KB)
- tdd-performance-tests.md (9 KB)
- tdd-property-tests.md (10 KB)
- tdd-error-handling-tests.md (10 KB)
- tdd-implementation-guide.md (17 KB)
- tdd-bugfix-guide.md (10 KB)
- tdd-refactoring-guide.md (12 KB)
- tdd-feature-development.md (8 KB)


### Fase 4: Compressao de Specs
**Sessao**: 5
**Economia estimada**: 10-15 KB

**Acoes**:
1. Remover filler words
2. Passivo → ativo
3. Remover `---` excessivos


### Fase 5: Reducao Exemplos Python
**Sessao**: 6
**Economia estimada**: 10-15 KB

**Acoes**:
1. Consolidar python-patterns + python-templates
2. Reduzir python-anti-patterns


### Fase 6: Demand Loading (Skills)
**Sessao**: 7

**Acoes**:
1. `load-all-context` → base: universal + zen
2. Skills para python, tdd


### Fase 7: Limpeza Final
**Sessao**: 8
**Economia estimada**: 5 KB


## Metricas de Sucesso

| Metrica | Baseline | Target |
|---------|----------|--------|
| Bundle | 251 KB | ~50-60 KB |
| Reducao | - | ~75% |
| Pass rate | TBD | >= 95% |
| Carga tipica | 258 KB | ~25 KB |


## Criterios de Rollback

- Degradacao < 5%: Continuar
- Degradacao 5-10%: Revisar
- Degradacao > 10%: Reverter


## Referencias

- Principios: /Users/daviguides/work/sources/gradients/size-redux/
- Arche tester: /Users/daviguides/work/sources/gradients/arche/arche-tester/
