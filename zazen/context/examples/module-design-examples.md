# Module Design Examples

**For vocabulary and principles**: @~/.claude/zazen/spec/universal/module-design-spec.md

---

## Example 1: Deep vs Shallow — Order Processing

**Purpose**: Show the difference between a shallow pass-through and a deep module that earns its keep.

### Shallow (anti-pattern)

```
module OrderProcessor:
    method validate(order) -> ValidationResult
    method calculate_totals(order) -> Totals
    method apply_discounts(order, rules) -> Order
    method check_inventory(order, inventory) -> AvailabilityResult
    method reserve_stock(order, inventory) -> ReservationResult
    method charge_payment(order, gateway) -> PaymentResult
    method send_confirmation(order, notifier) -> void
    method process(order, rules, inventory, gateway, notifier) -> Result
```

The interface has 8 methods. Callers must learn the ordering, handle intermediate results, and know which steps to call. The `process` method just calls the other seven in sequence — a pass-through.

**Deletion test**: deleting this module moves 7 method calls to every caller. But each method is trivial — the complexity was never hidden; it was just relocated.

### Deep (correct)

```
module OrderProcessor:
    constructor(inventory, payment_gateway, notifier)
    method process(order) -> OrderResult
```

One method. One parameter. The caller learns: "give it an order, get a result." Validation, discounts, inventory, payment, notification — all hidden. The interface is small; the implementation is rich.

**Deletion test**: deleting this module distributes discount logic, inventory reservation, payment charging, and notification across every caller. The module earns its keep.

---

## Example 2: Seam Placement

**Purpose**: Show when a seam is real (two adapters) vs hypothetical (one adapter).

### Hypothetical seam (premature)

```
interface Logger:
    method log(level, message) -> void

module ConsoleLogger implements Logger:
    method log(level, message) -> void:
        print("[{level}] {message}")
```

One adapter. No second implementation exists or is planned. The seam is indirection without value. Use the concrete module directly until a second adapter is justified.

### Real seam (justified)

```
interface PaymentGateway:
    method charge(amount, currency, token) -> ChargeResult
    method refund(charge_id) -> RefundResult

module StripeGateway implements PaymentGateway:
    // production: real HTTP calls to Stripe

module InMemoryGateway implements PaymentGateway:
    // test: records calls, returns configured responses
```

Two adapters: production and test. The seam is real — behaviour varies across it. Tests run without network; production hits the real service.

---

## Example 3: Testability Through Interface Design

**Purpose**: Contrast testable vs hard-to-test module shapes.

### Hard to test (creates dependencies internally)

```
module ReportGenerator:
    method generate(report_id) -> Report:
        db = DatabaseConnection("production_url")
        data = db.query("SELECT ...")
        template = FileSystem.read("templates/report.html")
        return render(template, data)
```

Tests must mock global state (database URL, filesystem). The module creates its dependencies — the test cannot substitute them through the interface.

### Testable (accepts dependencies through interface)

```
module ReportGenerator:
    constructor(data_source, template_loader)
    method generate(report_id) -> Report:
        data = data_source.fetch(report_id)
        template = template_loader.load("report")
        return render(template, data)
```

Tests provide in-memory data source and template loader. No global mocking. The interface declares what the module needs; the test supplies test-appropriate versions.

---

## Example 4: The Deletion Test in Practice

**Purpose**: Apply the deletion test to evaluate a module's value.

### Module under evaluation

```
module StringUtils:
    method capitalize(s) -> string
    method trim(s) -> string
    method pad_left(s, width, char) -> string
    method is_empty(s) -> boolean
```

**Deletion test**: delete `StringUtils`. Each caller writes `capitalize`, `trim`, `pad_left`, `is_empty` inline. These are one-liners. No complexity redistributes — it was already trivial at each call site.

**Verdict**: shallow. The module does not hide complexity. It collects functions that do not need collecting.

### Contrast with a deep utility

```
module MarkdownParser:
    method parse(text) -> Document
```

**Deletion test**: delete `MarkdownParser`. Every caller must implement heading detection, list parsing, code block extraction, link resolution, escaping rules. Significant complexity redistributes.

**Verdict**: deep. One method, massive hidden behaviour. Earns its keep.

---

## Example 5: Internal vs External Seams

**Purpose**: Show that a deep module can have internal seams without exposing them.

```
module SearchEngine:
    // External seam (the interface)
    constructor(index_adapter)
    method search(query) -> Results

    // Internal seams (private, used by tests of SearchEngine's internals)
    private tokenizer: Tokenizer
    private ranker: Ranker
    private filter: Filter
```

Callers see: `search(query) -> Results`. One method.

The implementation composes tokenizer, ranker, and filter — but these are internal. Tests of `SearchEngine` go through `search()`. Tests of `Tokenizer` are separate unit tests, not part of `SearchEngine`'s interface contract.

The external seam (`index_adapter`) exists because two adapters are justified: a production index and a test index.
