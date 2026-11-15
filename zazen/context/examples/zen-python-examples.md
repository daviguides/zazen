# Zen Applied in Python: Examples

Python illustrations of the zen principles per implementation context.
The decision matrix that picks which principles lead in each context
lives in `zen-implementation-guide.md`; Python syntax, docstring format
and idioms are owned by shodo.

## Writing Functions

**Apply:**
- Single responsibility
- Clear, descriptive name
- Type hints on all parameters
- Docstring (Args/Returns/Raises when applicable, shodo format)
- Validation at function start
- Guard clauses for flat structure
- No hidden side effects

**Example:**
```python
def calculate_user_discount(
    user: User,
    purchase_amount: Decimal,
) -> Decimal:
    """Calculate discount for user purchase."""
    # Validate first
    if not user.is_active:
        raise ValueError("User not active")
    if purchase_amount <= 0:
        raise ValueError("Amount must be positive")

    # Main logic
    base_discount = _get_loyalty_discount(user)
    volume_discount = _get_volume_discount(purchase_amount)

    return min(base_discount + volume_discount, Decimal("0.25"))
```

## Structuring Classes

**Apply:**
- Single clear responsibility
- Explicit public interface
- Private methods as helpers
- Constructor validates state
- Type hints on all methods
- Docstrings on class and public methods

**Example:**
```python
class DiscountCalculator:
    """Calculate discounts based on user and purchase criteria."""

    def __init__(self, max_discount: Decimal = Decimal("0.25")) -> None:
        self.max_discount = max_discount

    def calculate(self, user: User, amount: Decimal) -> Decimal:
        """Calculate final discount."""
        self._validate_inputs(user=user, amount=amount)

        loyalty = self._calculate_loyalty(user)
        volume = self._calculate_volume(amount)

        return min(loyalty + volume, self.max_discount)

    def _validate_inputs(self, user: User, amount: Decimal) -> None:
        """Validate calculation inputs."""
        if not user.is_active:
            raise ValueError("User not active")
        if amount <= 0:
            raise ValueError("Amount must be positive")
```

## Organizing Modules

**Apply:**
- One clear responsibility per module
- Module docstring explains purpose
- Imports in 3 groups (stdlib, third-party, local)
- Main function at top
- Helpers ordered by usage
- Module < 500 lines

**Example:**
```python
"""User discount calculation module.

Provides functionality to calculate discounts based on
loyalty and purchase volume.
"""

from decimal import Decimal

from pydantic import BaseModel

from core.models import User


def calculate_discount(user: User, amount: Decimal) -> Decimal:
    """Main function to calculate discount."""
    _validate_inputs(user, amount)
    return _apply_discount_rules(user, amount)


def _validate_inputs(user: User, amount: Decimal) -> None:
    """Helper to validate inputs."""
    ...


def _apply_discount_rules(user: User, amount: Decimal) -> Decimal:
    """Helper to apply discount rules."""
    ...
```

## Error Handling

**Apply:**
- Validate inputs explicitly
- Use specific exception types
- No bare `except:` and no catch-all `except Exception`
- Include context in messages
- Exception chaining with `from e`
- Log errors appropriately

**Example:**
```python
def process_payment(data: PaymentData) -> PaymentResult:
    """Process payment with explicit error handling."""
    try:
        if not data.amount > 0:
            raise ValueError("Amount must be positive")

        result = charge_card(data)

        if not result.success:
            raise PaymentError(f"Charge failed: {result.error}")

        return result

    except NetworkError as e:
        logger.error(f"Network error: {e}")
        raise PaymentError("Service unavailable") from e

    except GatewayTimeoutError as e:
        logger.error(f"Gateway timeout for {data.order_id}: {e}")
        raise PaymentError("Processing timed out") from e
```

Unexpected exceptions are not caught: they propagate with their traceback.

## Refactoring

**Process:**

1. **Identify Problems**
   - Deep nesting?
   - Unclear names?
   - Magic numbers?
   - Implicit behavior?

2. **Apply Zen Fixes**
   - Flatten with guard clauses
   - Rename for clarity
   - Extract constants
   - Make explicit

3. **Verify Improvements**
   - Is code clearer?
   - Complexity reduced?
   - Functionality maintained?

**Before:**
```python
def calc(u, amt):
    if u["type"] == "premium":
        if amt > 100:
            return amt * 0.9
        else:
            return amt * 0.95
    else:
        return amt
```

**After:**
```python
PREMIUM_DISCOUNT = Decimal("0.10")
PREMIUM_SMALL_DISCOUNT = Decimal("0.05")

def calculate_discounted_price(
    user: User,
    amount: Decimal,
) -> Decimal:
    """Calculate price with user-specific discount."""
    if amount <= 0:
        raise ValueError("Amount must be positive")

    if user.subscription_type == "premium":
        return _apply_premium_discount(amount)

    return amount


def _apply_premium_discount(amount: Decimal) -> Decimal:
    """Apply discount for premium users."""
    if amount > 100:
        return amount * (1 - PREMIUM_DISCOUNT)
    return amount * (1 - PREMIUM_SMALL_DISCOUNT)
```

