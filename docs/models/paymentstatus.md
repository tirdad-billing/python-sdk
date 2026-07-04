# PaymentStatus

## Example Usage

```python
from tirdad_sdk.models import PaymentStatus

# Open enum: unrecognized values are captured as UnrecognizedStr
value: PaymentStatus = "INITIATED"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"INITIATED"`
- `"PENDING"`
- `"PROCESSING"`
- `"SUCCEEDED"`
- `"OVERPAID"`
- `"FAILED"`
- `"REFUNDED"`
- `"PARTIALLY_REFUNDED"`
- `"VOIDED"`
