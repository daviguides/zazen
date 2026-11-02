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

## Runner entries (per mode)

`/zazen:load` (interactive) keeps loading everything through
`load-universal-workflow` + `load-zen-workflow`. The runner compiles one
thin entry per mode instead, so each SDK session pays only what its
mode uses. Zazen is language-agnostic: no per-language entries. Entries
are files in `zazen/prompts/` with direct `Read:` lines only (no entry
references another entry; the compiler caps depth at 2) and carry no
card: the runner never shows it, and every system-prompt token is paid
on every API call.

| Entry | Files | Mode |
|---|---|---|
| `load-planning` | module-design-spec, module-design-examples, deepening-guide, design-it-twice-guide, zen-principles-spec, pre-code-checklist | PLANNING, PLAN_REVIEWING |
| `load-implementing` | naming-conventions-spec, code-structure-spec, error-handling-spec, zen-principles-spec, zen-implementation-guide | IMPLEMENTING |
| `load-validating` | review-checklist (pulls common-red-flags via `@`) | VALIDATING |

Classification notes:
- `zen-principles-spec` is in planning and implementing (small, and both
  modes apply it); they never share a session.
- `common-red-flags` was already loaded: `review-checklist` references it.
- `project-setup-spec` stays out of every entry (and out of `load`): it
  only matters when scaffolding a new project, not in a task's modes.

Compiled size (`compile_plugin("zazen", prompt=<entry>)`, ~chars/3.6):

| Entry | Chars | ~Tokens |
|---|---|---|
| `load` (union) | 53,269 | 14.8k |
| `load-planning` | 27,257 | 7.6k |
| `load-implementing` | 23,253 | 6.5k |
| `load-validating` | 6,551 | 1.8k |

When adding a spec file: put its `Read:` line in the interactive
workflow files AND in every runner entry whose mode uses it.

---

## Releasing — mandatory workflow

Every plugin modification MUST follow this sequence. No exceptions.

### 1. Bump version

Patch for fixes/tweaks, minor for new skills or behavioral changes:

```bash
# From gradients/zazen/
# Edit .claude-plugin/plugin.json version field
# Also update install.sh header if it shows a version
```

### 2. Commit and push

```bash
git add -A && git commit -m "bump: vX.Y.Z — <what changed>"
git tag -a vX.Y.Z -m "<what changed>"
git push && git push origin vX.Y.Z
```

### 3. Run install.sh

```bash
~/work/sources/continuum/gradients/zazen/install.sh
```

Note: install.sh clones from the GitHub remote (not local source), so
the push in step 2 must land before running it.

### 4. Verify cache is not stale

The plugin cache (`~/.claude/plugins/cache/daviguides/zazen/`) is
unstable — even after a successful install, it can preserve stale
state from previous versions. This is a known unresolved bug in the
Claude Code plugin system.

After install, always verify:

```bash
# Compare installed vs source timestamps
diff <(ls -lR ~/.claude/zazen/skills/) <(ls -lR skills/)

# Check cache version matches
ls ~/.claude/plugins/cache/daviguides/zazen/

# If stale, nuke cache and reinstall
rm -rf ~/.claude/plugins/cache/daviguides/zazen/
rm -rf ~/.claude/zazen/
./install.sh
```

Do NOT move to the next task with a stale cache — the session will
load outdated skills silently.
