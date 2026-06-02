# BillingModel

## Example Usage

```python
from tirdad_sdk.models import BillingModel

# Open enum: unrecognized values are captured as UnrecognizedStr
value: BillingModel = "FLAT_FEE"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"FLAT_FEE"`
- `"PACKAGE"`
- `"TIERED"`
