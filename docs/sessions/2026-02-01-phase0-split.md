# Session: Phase 0 - Split Execution

**Data**: 2026-02-01
**Fase**: 0 - Split
**Status**: Concluido


## Objetivo

Executar split de Code-Zen em Zazen + Kyudo.


## Acoes Executadas

1. [x] Criar estrutura `/gradients/zazen/`
2. [x] Criar estrutura `/gradients/kyudo/`
3. [x] Copiar specs para Zazen (universal, python, tdd, principles)
4. [x] Copiar context para Zazen (guides, examples, checklists)
5. [x] Copiar prompts/load-* para Zazen
6. [x] Copiar reviewers para Kyudo
7. [x] Copiar code-review workflow para Kyudo
8. [x] Mover zen-check e zen-refactor para Kyudo
9. [x] Criar plugin.json para cada
10. [x] Criar CLAUDE.md para cada
11. [x] Criar commands/load.md para cada
12. [x] Atualizar referencias @code-zen/ → @zazen/ em Zazen
13. [x] Atualizar referencias @code-zen/ → @kyudo/ em Kyudo
14. [x] Criar repo GitHub zazen (publico)
15. [x] Criar repo GitHub kyudo (privado)


## Resultado

| Plugin | Bundle KB | Conteudo | Repo |
|--------|-----------|----------|------|
| **Zazen** | 251 | specs, examples, checklists, load prompts | https://github.com/daviguides/zazen |
| **Kyudo** | 188 | reviewers, zen-check, zen-refactor | https://github.com/daviguides/kyudo (privado) |
| **Total** | 439 | (vs 422 original) | |

**Ajuste**: zen-check e zen-refactor movidos para Kyudo (sao acoes, nao principios).


## Estrutura Criada

### Zazen (座禅) - Principios
```
zazen/
├── .claude-plugin/plugin.json
├── CLAUDE.md
├── zazen/
│   ├── spec/{universal,python,tdd,principles}/
│   ├── context/{guides,examples,checklists}/
│   └── prompts/
├── commands/
└── docs/{plans,sessions}/
```

### Kyudo (弓道) - Acoes
```
kyudo/
├── .claude-plugin/plugin.json
├── CLAUDE.md
├── kyudo/
│   ├── context/guides/
│   └── prompts/agents/reviewers/
├── commands/
├── agents/
└── docs/
```


## Proximos Passos (Proxima Sessao)

### Fase 0.5: Split da Wiki (pendente)
- [ ] Split wiki do repo code-zen original
- [ ] Criar wiki para zazen (publico)
- [ ] Criar wiki para kyudo (privado)
- [ ] Mover conteudo relevante para cada wiki

### Fase 1: Baseline + zazen-tester
1. Instalar Zazen como plugin
2. Criar zazen-tester (baseado em arche-tester)
3. Definir casos de teste
4. Rodar baseline
5. Documentar pass rate


## Decisoes

### D1: Overhead aceitavel
Split resultou em 439 KB vs 422 KB original (+4%).
Overhead minimo, beneficio de separacao vale.

### D2: Kyudo pode esperar
Kyudo nao precisa de reducao imediata.
Foco em Zazen primeiro.

### D3: Zazen publico, Kyudo privado
- Zazen: principios universais, valor em ser publico
- Kyudo: workflows de review, pode ser privado

### D4: zen-check/zen-refactor sao acoes
Movidos para Kyudo pois sao acoes que aplicam principios, nao os principios em si.


## Arquivos Criados

**Zazen**:
- `.claude-plugin/plugin.json`
- `CLAUDE.md`
- `commands/load.md`
- `docs/sessions/INDEX.md`
- `docs/sessions/2026-02-01-phase0-split.md`

**Kyudo**:
- `.claude-plugin/plugin.json`
- `CLAUDE.md`
- `commands/load.md`

**GitHub**:
- https://github.com/daviguides/zazen (publico)
- https://github.com/daviguides/kyudo (privado)
