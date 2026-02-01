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
│   │   ├── python/           # Python-specific standards
│   │   ├── tdd/              # Test-driven development
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
| `/zazen:load-python-context` | Load Python standards |
| `/zazen:load-tdd-context` | Load TDD principles |

**Note**: Actions like check, refactor, review are in Kyudo plugin.


## Related Plugins

- **Kyudo**: Actions - check, refactor, review (separate plugin)
- **Arche**: Behavioral principles for Claude Code
- **Gradient**: Plugin architecture


## Size Reduction Status

See `docs/plans/` and `docs/sessions/` for reduction progress.
