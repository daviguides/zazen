# Zazen - Claude Code Project Instructions

## Project Overview

**Zazen** (座禅) provides principles for writing code with focus and clarity.

**Philosophy**: Like seated meditation, Zazen helps developers write code with mindfulness - clear structure, proper naming, and zen-like simplicity.


## Structure

```
zazen/
├── zazen/                    # Bundle (Gradient pattern)
│   ├── spec/
│   │   ├── universal/        # Language-agnostic principles
│   │   └── principles/       # Zen principles
│   ├── context/
│   │   ├── guides/           # Implementation guides
│   │   ├── examples/         # Code examples
│   │   └── checklists/       # Verification checklists
│   └── prompts/
├── commands/
├── skills/
└── docs/
```


## Commands

| Command | Purpose |
|---------|---------|
| `/zazen:load` | Load zen principles (base) |
| `/zazen:load-all-context` | Load universal + zen principles |

**Note**: TDD moved to **Kinhin**. Python moved to **Shodō**. Actions in **Kyudo**.


## Related Plugins

- **Kinhin**: TDD principles (extracted from Zazen)
- **Shodō**: Python standards (extracted from Zazen)
- **Kyudo**: Actions - check, refactor, review
- **Arche**: Behavioral principles for Claude Code
- **Gradient**: Plugin architecture


## Size Reduction Testing

**IMPORTANT**: Before any size reduction work, read the tester documentation:

```
@./../testers/zazen-tester/CLAUDE.md
```

This is **mandatory reading** - contains all commands, workflows, and iteration patterns.

**Quick start**:
```bash
cd /Users/daviguides/work/sources/gradients/testers/zazen-tester

# Single test iteration (fastest)
uv run zazen-test run 0.1.0 -i NM-007 -f
uv run zazen-test analyze 0.1.0 -i NM-007 -f

# Group iteration
uv run zazen-test run 0.1.0 -g NM

# Full baseline (94 tests)
uv run zazen-test baseline
```

**Groups**: NM (17), ST (15), EH (25), ZN (15), RF (8), PS (14)

**Related testers**:
- kinhin-tester: TDD tests (45) - `@./../testers/kinhin-tester/CLAUDE.md`
- shodo-tester: Python tests (57) - `@./../testers/shodo-tester/CLAUDE.md`


## Size Reduction Status

@./docs/sessions/INDEX.md
