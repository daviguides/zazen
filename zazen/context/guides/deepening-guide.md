# Deepening Guide

How to deepen a cluster of shallow modules safely, given its dependencies.

**For vocabulary**: @~/.claude/zazen/spec/universal/module-design-spec.md

---

## Dependency Categories

When assessing a candidate for deepening, classify its dependencies. The category determines how the deepened module is tested across its seam.

### 1. In-process

Pure computation, in-memory state, no I/O. Always deepenable: merge the modules and test through the new interface directly. No adapter needed.

### 2. Local-substitutable

Dependencies that have local test stand-ins (in-memory database, in-memory filesystem). Deepenable when the stand-in exists. The deepened module is tested with the stand-in running in the test suite. The seam is internal; no port at the external interface.

### 3. Remote but owned (Ports and Adapters)

Your own services across a network boundary. Define a **port** (interface) at the seam. The deep module owns the logic; the transport is injected as an **adapter**. Tests use an in-memory adapter. Production uses a network adapter.

### 4. True external (Mock)

Third-party services you do not control. The deepened module takes the external dependency as an injected port; tests provide a mock adapter.

---

## Seam Discipline

- **One adapter means a hypothetical seam. Two adapters means a real one.** Do not introduce a port unless at least two adapters are justified (typically production + test). A single-adapter seam is indirection.
- **Internal seams vs external seams.** A deep module can have internal seams (private, used by its own tests) as well as the external seam at its interface. Do not expose internal seams through the interface because tests use them.

---

## Testing Strategy: Replace, Do Not Layer

When deepening a cluster of shallow modules into one deep module:

1. Write new tests at the deepened module's interface. The **interface is the test surface**.
2. Old unit tests on the formerly shallow modules become waste once tests at the new interface exist. Delete them.
3. Tests assert on observable outcomes through the interface, not internal state.
4. Tests MUST survive internal refactors. A test that breaks when the implementation changes (but behaviour does not) is testing past the interface.

---

## Process

1. **Identify the cluster**: a group of shallow modules that callers use together in a fixed sequence.
2. **Classify dependencies**: assign each dependency to one of the 4 categories.
3. **Design the deep interface**: apply module-design-spec principles (reduce methods, simplify params, hide complexity).
4. **Build adapters for each seam**: one production, one test (minimum).
5. **Write tests at the new interface**: before deleting the old tests.
6. **Delete the shallow modules and their tests**: the deep module replaces them.

---

## Validation

- [ ] Each dependency classified into one of the 4 categories
- [ ] No seam introduced without at least 2 adapters (or marked hypothetical)
- [ ] Tests operate through the deepened module's interface
- [ ] Old shallow-module tests deleted after replacement tests pass
- [ ] Internal refactors do not break tests
