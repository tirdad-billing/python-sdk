# RefundReason

## Example Usage

```python
from tirdad_sdk.models import RefundReason

# Open enum: unrecognized values are captured as UnrecognizedStr
value: RefundReason = "DUPLICATE"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"DUPLICATE"`
- `"FRAUDULENT"`
- `"REQUESTED_BY_CUSTOMER"`
- `"ORDER_CHANGE"`
- `"SERVICE_ISSUE"`
- `"OTHER"`
