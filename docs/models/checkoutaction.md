# CheckoutAction

## Example Usage

```python
from tirdad_sdk.models import CheckoutAction

# Open enum: unrecognized values are captured as UnrecognizedStr
value: CheckoutAction = "create_subscription"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"create_subscription"`
- `"modify_subscription"`
- `"wallet_topup"`
- `"add_addon"`
