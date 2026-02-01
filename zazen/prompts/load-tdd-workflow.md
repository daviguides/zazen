# Load TDD Context Workflow

## ⚠️ STOP - MANDATORY ACTION REQUIRED

**DO NOT RESPOND until you have used the Read tool on EACH file below.**

This is not a reference list. This is an execution order.

### Step 1: Read TDD Methodology
```
Read: ~/.claude/zazen/spec/tdd/tdd-spec.md
```

### Step 2: Read Python TDD Specifics
```
Read: ~/.claude/zazen/spec/python/python-tdd-spec.md
Read: ~/.claude/zazen/spec/python/python-testing-tools-spec.md
```

### Step 3: Read TDD Implementation Guides
```
Read: ~/.claude/zazen/context/guides/tdd-implementation-guide.md
Read: ~/.claude/zazen/context/guides/tdd-feature-development.md
Read: ~/.claude/zazen/context/guides/tdd-bugfix-guide.md
Read: ~/.claude/zazen/context/guides/tdd-refactoring-guide.md
```

### Step 4: Read Test Templates
```
Read: ~/.claude/zazen/context/examples/tdd-unit-tests.md
Read: ~/.claude/zazen/context/examples/tdd-integration-tests.md
Read: ~/.claude/zazen/context/examples/tdd-property-tests.md
Read: ~/.claude/zazen/context/examples/tdd-error-handling-tests.md
Read: ~/.claude/zazen/context/examples/tdd-performance-tests.md
```

### Step 5: Read Anti-Patterns and Checklist
```
Read: ~/.claude/zazen/context/examples/tdd-anti-patterns.md
Read: ~/.claude/zazen/context/checklists/tdd-checklist.md
```

---

## ⛔ HALT CONDITIONS

**If you responded without reading all 14 files above: YOU VIOLATED THIS PRINCIPLE.**

---

## Workflow Instructions

**When TDD context is loaded, ALL implementations must be test-driven:**

### Phase 1: Test Design (Always First)

1. **Identify Workflow**
   - New feature → Use Feature-Complete or Test Suite First
   - Bug fix → Use Test Suite First (reproduction test)
   - Refactoring → Ensure coverage first, then refactor
   - Complex domain → Use Scenario Matrix

2. **Create Scenario Matrix**
   - Happy path cases (3-5 minimum)
   - Edge cases (boundaries, limits)
   - Error cases (invalid inputs, failures)
   - Performance cases (if applicable)

3. **Plan Test Categories**
   - Unit tests for core logic
   - Integration tests for interactions
   - Property tests for constraints
   - Error tests for failure modes
   - Performance tests for requirements

### Phase 2: Test Generation (Batch Processing)

1. **Generate Tests in Batches**
   - Use templates from context/examples/
   - Generate entire test categories simultaneously
   - Apply consistent patterns across all tests
   - Use AAA pattern (Arrange-Act-Assert)
   - Include type hints and docstrings

2. **Use Property-Based Tests**
   - All business constraints → property tests
   - All invariants → property tests
   - Anti-hallucination barriers → property tests

3. **Validate Test Quality**
   - Check against tdd-checklist.md
   - Verify no anti-patterns from tdd-anti-patterns.md
   - Ensure comprehensive scenario coverage

### Phase 3: Implementation (Tests to Green)

1. **Implement in Dependency Order**
   - Data models first
   - Core utilities second
   - Business logic third
   - Integration layers fourth
   - Error handling last

2. **Batch Implementation**
   - Implement logical groups together
   - Not one function at a time
   - Use LLM parallel thinking

3. **Keep Tests Passing**
   - All tests should pass when complete
   - No skipped tests
   - No ignored test failures

### Phase 4: Validation (Quality Assurance)

1. **Run Complete Checklist**
   - Use tdd-checklist.md for validation
   - Verify coverage ≥ 90%
   - Validate no anti-patterns
   - Ensure performance requirements met

2. **Anti-Hallucination Validation**
   - All constraints tested with property tests
   - Cross-function consistency validated
   - Type safety confirmed
   - No implicit conversions

3. **Documentation**
   - All tests have docstrings
   - Complex setups documented
   - Test purpose clear

## LLM Optimization Strategies

**Apply these throughout TDD process:**

### Batch Processing
- Generate multiple tests simultaneously
- Implement functions in logical groups
- Refactor modules for consistency

### Template-Driven Consistency
- Use templates from context/examples/
- Maintain consistent patterns
- Leverage LLM pattern-following

### Property-Based Validation
- Focus on invariants
- Use as anti-hallucination barriers
- Validate constraints systematically

### Context Preservation
- Keep related tests together
- Don't fragment across prompts
- Use comprehensive scenario matrices

## Workflow Selection

| Task Type | Recommended Workflow | Guide |
|-----------|---------------------|-------|
| New feature | Feature-Complete TDD | tdd-feature-development.md |
| Bug fix | Test Suite First | tdd-bugfix-guide.md |
| Refactoring | Test-First Refactoring | tdd-refactoring-guide.md |
| Complex domain | Scenario Matrix | tdd-implementation-guide.md |

## Quality Gates

**Do NOT proceed to next phase until:**

- [ ] Phase 1: Scenario matrix complete, workflow selected
- [ ] Phase 2: All tests generated, checklist validated
- [ ] Phase 3: All tests passing, implementation complete
- [ ] Phase 4: Checklist complete, no anti-patterns

## Prompt Engineering Guidelines

**When requesting test generation:**

```
Generate complete test suite for [COMPONENT]:

Scenario Matrix:
[PASTE OR DESCRIBE MATRIX]

Generate:
1. All unit tests (use tdd-unit-tests.md templates)
2. All integration tests (use tdd-integration-tests.md templates)
3. All property tests (use tdd-property-tests.md templates)
4. All error tests (use tdd-error-handling-tests.md templates)

Requirements:
- Batch generation (all tests simultaneously)
- Consistent AAA pattern
- Type hints on all parameters
- Descriptive docstrings
- Clear assertion messages
- Anti-hallucination focus (property tests for constraints)

Validate against tdd-checklist.md before completion.
```

**When requesting implementation:**

```
Implement [COMPONENT] to satisfy test suite:

Tests: tests/test_[component].py
Requirements: [LIST REQUIREMENTS]

Implementation order:
1. [Dependency level 1]
2. [Dependency level 2]
3. [Main component]

Constraints:
- All tests must pass
- Follow Python standards
- Type hints required
- Error handling required
- Coverage ≥ 90%

Validate:
- No anti-patterns from tdd-anti-patterns.md
- Passes tdd-checklist.md validation
```

## Integration with Code Standards

**TDD works alongside other Code Zen standards:**

### Always Apply
- Zen of Python principles
- Python language standards
- Python style standards
- Error handling standards

### References
- Zen Principles: `@~/.claude/zazen/spec/principles/zen-principles-spec.md`
- Python Language: `@~/.claude/zazen/spec/python/python-language-spec.md`
- Python Style: `@~/.claude/zazen/spec/python/python-style-spec.md`

## Success Criteria

**TDD context successfully applied when:**

- ✅ All implementations preceded by tests
- ✅ Scenario matrix coverage 100%
- ✅ Code coverage ≥ 90%
- ✅ All constraints have property tests
- ✅ No anti-patterns detected
- ✅ TDD checklist validated
- ✅ Tests serve as documentation
- ✅ High confidence in code correctness

Apply TDD methodology to ALL code generated in this session.
