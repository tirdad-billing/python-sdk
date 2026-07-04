# CheckoutStatus

## Example Usage

```python
from tirdad_sdk.models import CheckoutStatus

# Open enum: unrecognized values are captured as UnrecognizedStr
value: CheckoutStatus = "initiated"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"initiated"`
- `"pending"`
- `"completed"`
- `"failed"`
- `"expired"`
