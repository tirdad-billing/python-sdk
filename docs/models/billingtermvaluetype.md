# BillingTermValueType

fixed or remainder; percentage is reserved and rejected as not supported yet

## Example Usage

```python
from tirdad_sdk.models import BillingTermValueType

# Open enum: unrecognized values are captured as UnrecognizedStr
value: BillingTermValueType = "fixed"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"fixed"`
- `"percentage"`
- `"remainder"`
