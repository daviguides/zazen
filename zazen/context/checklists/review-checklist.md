# Code Review Checklist

## Post-Implementation Verification

### ✅ Group 1: Foundations (CRITICAL)

**Beautiful (Conventions):**
- [ ] Code follows the language's conventions (Python: PEP 8); lines within the language formatter's width
- [ ] Names are consistent with project patterns
- [ ] Structure is clean and organized

**Explicit (Clear Intentions):**
- [ ] All code intentions are clear
- [ ] No "magic" or implicit behaviors
- [ ] Can be understood without special knowledge

**Readability (Human-First):**
- [ ] A junior developer could understand this code
- [ ] Code tells a clear story
- [ ] Avoided unnecessary cleverness

### ✅ Group 2: Structure (CRITICAL)

**Simple vs Complex:**
- [ ] Used the simplest solution for this problem
- [ ] If complex, problem is inherently complex
- [ ] Avoided over-engineering

**Flat (No Deep Nesting):**
- [ ] No unnecessary nesting levels
- [ ] Used guard clauses or early returns where appropriate
- [ ] Control flow is linear and clear

**Sparse (Proper Spacing):**
- [ ] Code has adequate spacing
- [ ] No dense or compressed lines
- [ ] Complex expressions broken into multiple lines

### ✅ Group 3: Decisions (WHEN APPLICABLE)

**Special Cases:**
- [ ] Maintained consistency even in edge cases
- [ ] No unique solutions for "special" cases
- [ ] Followed established patterns

**Practicality vs Purity:**
- [ ] If broke convention, clear practical benefit exists
- [ ] Documented reason for exception
- [ ] Benefit justifies the deviation

**Ambiguity:**
- [ ] No assumptions about inputs or behavior
- [ ] Forced clarity where ambiguity existed
- [ ] Documented necessary assumptions

**One Obvious Way:**
- [ ] Used the idiomatic approach (Python: Pythonic)
- [ ] Followed established language conventions
- [ ] Did not reinvent the wheel

### ✅ Group 4: Implementation Details

**Type Hints:**
- [ ] All function parameters have type hints
- [ ] All return types are annotated
- [ ] Python: 3.13+ syntax (`list[str]` not `List[str]`), unions with `|` not `Union`

**Function Structure:**
- [ ] Functions have single responsibility
- [ ] Function names are descriptive
- [ ] Parameters use keyword arguments when multiple
- [ ] Input validation at function start
- [ ] No hidden side effects

**Class Structure:**
- [ ] Single clear responsibility
- [ ] Public interface is intuitive
- [ ] Constructor validates initial state
- [ ] Private methods are clear helpers

**Error Handling:**
- [ ] No bare `except:` clauses
- [ ] Specific exception types used
- [ ] Error messages include context
- [ ] Exception chaining (Python: `from e`)
- [ ] Errors never pass silently (unless explicitly intended)

**Documentation:**
- [ ] Module docstring exists
- [ ] Class docstrings exist
- [ ] Public function docstrings exist
- [ ] Docstrings within the language formatter's width
- [ ] Args, Returns, Raises documented where applicable

**Imports:**
- [ ] Organized in 3 groups (stdlib, third-party, local)
- [ ] Blank lines between groups
- [ ] No unused imports
- [ ] Python: pathlib over os.path

**Style:**
- [ ] Python: f-strings (not % or .format())
- [ ] No magic numbers (named constants used)
- [ ] Trailing commas in multi-line constructs
- [ ] Lines within the language formatter's width

## Context-Specific Checks

### For New Features
- [ ] Feature can be explained in one sentence
- [ ] Interface is intuitive
- [ ] Follows project patterns
- [ ] Tests included

### For Refactoring
- [ ] Code is clearer than before
- [ ] Reduced unnecessary complexity
- [ ] Maintained original functionality
- [ ] Improved test coverage

### For Bug Fixes
- [ ] Root cause is clear
- [ ] Added validation to prevent recurrence
- [ ] Fix is targeted (not over-engineered)
- [ ] Added regression test

## Red Flags - Reject If Found

See `common-red-flags.md` (every zazen entry that loads this checklist loads it too).
