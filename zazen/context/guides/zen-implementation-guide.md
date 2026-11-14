# Zen of Python Implementation Guide

## Decision Matrix - Context-Based Prioritization

| Implementation Context | Primary Principles | Secondary Principles | Mandatory Check |
|------------------------|-------------------|----------------------|-----------------|
| **Writing Function** | Readability counts<br>Simple > Complex | Explicit > Implicit<br>Flat > Nested | "Can explain in one sentence?" |
| **Structuring Class** | Explicit > Implicit<br>Namespaces | Simple > Complex<br>Beautiful > Ugly | "Single responsibility?" |
| **Organizing Module** | Namespaces<br>One obvious way | Flat > Nested<br>Sparse > Dense | "Imports clear?" |
| **Error Handling** | Errors never silent<br>Unless silenced | Explicit > Implicit<br>Refuse to guess | "Failure obvious?" |
| **Refactoring** | Readability counts<br>Simple > Complex | Beautiful > Ugly<br>Flat > Nested | "Improved clarity?" |

## Conflict Resolution

### When Principles Conflict

@~/.claude/zazen/spec/principles/zen-principles-spec.md#conflict-resolution-hierarchy

### Example Conflicts

**Purity vs Practicality:**
```python
# Pure (always explicit):
config = load_config(path=Path("config.yaml"))

# Practical (when path is always same):
DEFAULT_CONFIG_PATH = Path("config.yaml")

def load_default_config() -> Config:
    """Load config from default location."""
    return load_config(path=DEFAULT_CONFIG_PATH)

# Practicality wins when:
# - Pattern is used 20+ times
# - Default is well-documented
# - Clear practical benefit
```

## Success Metrics

**Code Quality:**
- Can explain each function in one sentence?
- No nesting > 3 levels?
- All errors handled explicitly?
- Magic numbers eliminated?
- Each module under 500 lines, one responsibility?

**Readability:**
- Junior dev can understand?
- Code tells clear story?
- No cleverness for cleverness sake?

**Maintainability:**
- Easy to add features?
- Clear where changes go?
- Consistent patterns used?
