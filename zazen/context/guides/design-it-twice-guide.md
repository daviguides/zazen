# Design It Twice Guide

Explore alternative interfaces for a module before committing to one. Based on the principle that the first idea is unlikely to be the best.

**For vocabulary**: @~/.claude/zazen/spec/universal/module-design-spec.md

---

## When to Use

- Designing a new deep module where the interface shape is not obvious
- Deepening a cluster of shallow modules and multiple seam placements are plausible
- The module will have many callers (high leverage), making the interface costly to change later

---

## Process

### 1. Frame the problem space

Before exploring alternatives, write down:

- The constraints any interface MUST satisfy
- The dependencies and their categories (see deepening-guide.md)
- A rough sketch to ground the constraints — not a proposal, just something concrete to think against

### 2. Generate radically different designs

Produce 3+ interface designs. Each MUST differ in shape, not just naming. Use different design constraints:

- **Minimize the interface**: 1-3 entry points maximum. Maximize leverage per entry point.
- **Maximize flexibility**: support many use cases and extension points.
- **Optimize for the common caller**: make the default case trivial, accept complexity for rare cases.
- **Design around ports**: if cross-seam dependencies dominate, let the adapter pattern shape the interface.

Each design specifies:

1. Interface (methods, parameters, invariants, error modes)
2. Usage from a caller's perspective
3. What the implementation hides behind the seam
4. Dependency strategy and adapters
5. Where leverage is high and where it is thin

### 3. Compare

Contrast designs on three axes:

- **Depth**: which interface hides the most behaviour per unit of surface?
- **Locality**: which concentrates change in fewer places?
- **Seam placement**: which puts seams where behaviour actually varies?

### 4. Decide

Recommend one design. If elements from different designs combine well, propose a hybrid. State the reason in terms of depth, locality, and seam placement — not preference.

---

## Anti-patterns

- **Generating variations that differ only in naming**: not design-it-twice. The interfaces MUST differ in shape (number of methods, parameter structure, seam placement).
- **Comparing without criteria**: always compare on depth, locality, and seam placement. Subjective preference is not a criterion.
- **Skipping the problem-space frame**: without written constraints, designs drift and comparison loses ground truth.

---

## Validation

- [ ] At least 3 designs generated with different constraints
- [ ] Designs differ in interface shape, not just names
- [ ] Comparison uses depth, locality, and seam placement as criteria
- [ ] One design recommended with stated reason
- [ ] Problem-space constraints documented before design exploration
