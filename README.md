# Zazen

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> Principles for writing code with focus and clarity, designed as a Claude Code plugin.

## What is Zazen?

**Zazen** (座禅) means "seated meditation" in Japanese. Like the practice of sitting in focused awareness, Zazen helps developers write code with mindfulness - clear structure, proper naming, and zen-like simplicity.

Zazen provides **universal principles** that apply to any programming language - the foundational practices for clean, maintainable code.

## Installation

```bash
bash -c "$(curl -fsSL https://raw.githubusercontent.com/daviguides/zazen/main/install.sh)"
```

## Philosophy

### The Way of Mindful Code (座禅)

Just as Zen practitioners seek clarity through seated meditation, this plugin defines the principles of mindful coding: structure, naming, and simplicity that bring peace to any codebase.

> *"In the beginner's mind there are many possibilities, but in the expert's there are few."*
> — Shunryu Suzuki

### Core Principles

| Principle | Zen Virtue | Purpose |
|-----------|------------|---------|
| **Clear Structure** | Form (形) | Logical organization; every piece in its place |
| **Proper Naming** | Truth (真) | Names reveal intent; self-documenting code |
| **Zen Simplicity** | Emptiness (空) | Remove the unnecessary; embrace minimalism |
| **Error Clarity** | Awareness (覚) | Handle errors with grace; fail meaningfully |

## Relationship with Other Plugins

Zazen is the meditation from which specialized practices emerge:

| Plugin | Philosophy | Focus |
|--------|------------|-------|
| **zazen** | Zen (座禅) | Universal principles (any language) |
| **shodo** | Calligraphy (書道) | Python standards |
| **kinhin** | Walking meditation (経行) | TDD practices |
| **arche** | Greek (ἀρχή) | LLM behavioral principles |

```
        ┌────────┐
        │ zazen  │  ← Universal principles
        └───┬────┘
            │
    ┌───────┼───────┐
    ▼       ▼       ▼
┌───────┐ ┌───────┐ ┌────────┐
│ shodo │ │kinhin │ │ kyudo  │
└───────┘ └───────┘ └────────┘
 Python     TDD      Actions
```

## Project Structure

```
zazen/
├── spec/                    # Normative specifications
│   ├── universal/           # Language-agnostic principles
│   └── principles/          # Zen principles
├── context/                 # Applied examples
│   ├── guides/              # Implementation guides
│   └── checklists/          # Verification checklists
├── prompts/                 # Workflow orchestrators
├── commands/                # User-facing commands
└── skills/                  # Skill definitions
```

## Usage

```bash
/zazen:load                  # Load zen principles
```

## License

MIT License

---

> *"Before enlightenment, chop wood, carry water. After enlightenment, chop wood, carry water."*
> — Zen proverb
