# ChangedInvoiceAction

created (proration invoice) | wallet_credit (downgrade credit)

## Example Usage

```python
from tirdad_sdk.models import ChangedInvoiceAction

# Open enum: unrecognized values are captured as UnrecognizedStr
value: ChangedInvoiceAction = "created"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"created"`
- `"wallet_credit"`
