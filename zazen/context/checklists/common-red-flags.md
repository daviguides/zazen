# Common Code Red Flags

Critical anti-patterns that violate Zen of Python principles.

## Red Flags

- 🚨 **"This is too clever"** → Violates Simple > Complex
- 🚨 **"Only works if you know X"** → Violates Explicit > Implicit
- 🚨 **"Nesting > 3 levels of if/for"** → Violates Flat > Nested
- 🚨 **"Line beyond the language formatter's width (80 when no shodo spec)"** → Violates Sparse > Dense
- 🚨 **"Can't explain how it works"** → Violates "Hard to explain = bad idea"
- 🚨 **"Using default values with 'or'"** → Implicit behavior
- 🚨 **"Bare except:"** → Silent errors
- 🚨 **"Function > ~100 lines"** → Violates Simple > Complex

## Usage

Include this file in checklists and validation workflows to ensure consistent anti-pattern detection.
