# Module Design Specification

**Purpose**: Define the vocabulary and principles for designing deep modules with simple interfaces, clean seams, and testability through interface design.

---

## Glossary

Use these terms exactly. Do not substitute "component," "service," "API," or "boundary."

**Module**: anything with an interface and an implementation. Scale-agnostic: a function, class, package, or tier-spanning slice.

**Interface**: everything a caller MUST know to use the module correctly. Includes: type signature, invariants, ordering constraints, error modes, required configuration, performance characteristics. NOT just the type-level surface.

**Implementation**: what is inside a module. Distinct from **Adapter**: a module can be a small adapter with a large implementation (a database repository) or a large adapter with a small implementation (an in-memory fake).

**Depth**: leverage at the interface. The amount of behaviour a caller can exercise per unit of interface they must learn. A module is **deep** when a large amount of behaviour sits behind a small interface, **shallow** when the interface is nearly as complex as the implementation.

**Seam** _(Michael Feathers)_: a place where behaviour can be altered without editing in that place. The location at which a module's interface lives. Where to put the seam is its own design decision, distinct from what goes behind it.

**Adapter**: a concrete thing that satisfies an interface at a seam. Describes role (what slot it fills), not substance (what is inside).

**Leverage**: what callers get from depth. More capability per unit of interface learned. One implementation pays back across N call sites and M tests.

**Locality**: what maintainers get from depth. Change, bugs, knowledge, and verification concentrate in one place rather than spreading across callers.

---

## Deep vs Shallow

**Deep module** = small interface + large implementation:

```
┌─────────────────────┐
│   Small Interface   │  Few methods, simple params
├─────────────────────┤
│                     │
│  Deep Implementation│  Complex logic hidden
│                     │
└─────────────────────┘
```

**Shallow module** = large interface + thin implementation (anti-pattern):

```
┌─────────────────────────────────┐
│       Large Interface           │  Many methods, complex params
├─────────────────────────────────┤
│  Thin Implementation            │  Just passes through
└─────────────────────────────────┘
```

When designing an interface, answer:

1. Can the number of methods be reduced?
2. Can the parameters be simplified?
3. Can more complexity be hidden inside?

---

## Principles

### 1. Depth is a property of the interface, not the implementation

A deep module can be internally composed of small, swappable parts. Those parts are not part of the interface. A module can have **internal seams** (private, used by its own tests) as well as the **external seam** at its interface.

### 2. The deletion test

Imagine deleting the module. If complexity vanishes, it was a pass-through. If complexity reappears across N callers, the module was earning its keep.

### 3. The interface is the test surface

Callers and tests cross the same seam. If tests must reach past the interface to verify behaviour, the module is the wrong shape.

### 4. One adapter means a hypothetical seam. Two adapters means a real one.

Do not introduce a seam unless something actually varies across it. A single-adapter seam is indirection without value.

---

## Testability Through Design

Testability is a consequence of good interface design, not a separate concern.

### Accept dependencies, do not create them

The module receives what it needs through its interface. It does not instantiate concrete dependencies internally.

### Return results, do not produce side effects

A module that returns a value is testable by assertion. A module that mutates external state requires setup, observation, and teardown.

### Small surface area

Fewer methods = fewer tests needed. Fewer parameters = simpler test setup.

---

## Rejected Framings

These framings MUST NOT be used:

- **Depth as ratio of implementation-lines to interface-lines**: rewards padding the implementation. Depth is leverage, not line count.
- **"Interface" as a language keyword or a class's public methods**: too narrow. Interface here includes every fact a caller must know.
- **"Boundary"**: overloaded with DDD's bounded context. Use **seam** or **interface**.
- **"Component" / "service"**: overloaded with framework-specific meaning. Use **module**.

---

## Validation Rules

A module design is valid when:

- [ ] The glossary terms are used consistently (no substitutions)
- [ ] Depth is measured by leverage, not line count
- [ ] Every seam has at least two adapters (production + test), or is marked as hypothetical
- [ ] The deletion test has been applied: removing the module would redistribute complexity to callers
- [ ] Tests operate through the interface, not past it
- [ ] Dependencies are accepted through the interface, not created internally
