# AlertType

## Example Usage

```python
from tirdad_sdk.models import AlertType

# Open enum: unrecognized values are captured as UnrecognizedStr
value: AlertType = "low_ongoing_balance"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"low_ongoing_balance"`
- `"low_credit_balance"`
- `"feature_wallet_balance"`
- `"subscription_spend"`
- `"subscription_line_item_spend"`
- `"subscription_group_spend"`
