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
8. [x] Criar plugin.json para cada
9. [x] Criar CLAUDE.md para cada
10. [x] Criar commands/load.md para cada


## Resultado

| Plugin | Bundle KB | Conteudo |
|--------|-----------|----------|
| **Zazen** | 251 | specs, examples, checklists, load prompts (principios) |
| **Kyudo** | 188 | reviewers, zen-check, zen-refactor (acoes) |
| **Total** | 439 | (vs 422 original - overhead de duplicacao minima) |

**Ajuste**: zen-check e zen-refactor movidos para Kyudo (são ações, não princípios).


## Estrutura Criada

### Zazen
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

### Kyudo
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


## Pendencias

### Para testar (proxima sessao)
- [ ] Instalar plugins: `claude plugins add /path/to/zazen`
- [ ] Testar `/zazen:load`
- [ ] Testar `/kyudo:load`

### Referencias @ (futuro)
- Atualizar referencias `@zazen/` para `@zazen/` ou `@kyudo/`
- Verificar se prompts carregam corretamente


## Proximos Passos

**Fase 1**: Baseline + zazen-tester
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
