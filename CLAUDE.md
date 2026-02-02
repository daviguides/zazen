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

**Note**: TDD principles moved to **Kinhin** plugin. Actions in **Kyudo** plugin.


## Related Plugins

- **Kinhin**: TDD principles (extracted from Zazen)
- **Kyudo**: Actions - check, refactor, review
- **Arche**: Behavioral principles for Claude Code
- **Gradient**: Plugin architecture


## Size Reduction Testing

**IMPORTANT**: When doing size reduction on Zazen specs, use zazen-tester.

**Location**: `/Users/daviguides/work/sources/gradients/testers/zazen-tester/`

**Quick commands**:
```bash
cd /Users/daviguides/work/sources/gradients/testers/zazen-tester

# Run specific group (faster iteration)
uv run zazen-test run 0.1.0 -g NM      # Naming only
uv run zazen-test run 0.1.0 -g NM,ST   # Multiple groups

# Full baseline (151 tests)
uv run zazen-test baseline
```

**Groups**: NM, ST, EH, ZN, PY, PYS, PYL, PYT, RF, PS

**Note**: TDD tests (TD, TDH) moved to kinhin-tester.


## Size Reduction Status

@./docs/sessions/INDEX.md
