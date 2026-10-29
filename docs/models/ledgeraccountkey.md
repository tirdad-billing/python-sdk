# LedgerAccountKey

## Example Usage

```python
from tirdad_sdk.models import LedgerAccountKey

# Open enum: unrecognized values are captured as UnrecognizedStr
value: LedgerAccountKey = "cash"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"cash"`
- `"accounts_receivable"`
- `"unbilled_receivable"`
- `"deferred_revenue"`
- `"customer_credit"`
- `"tax_payable"`
- `"revenue"`
- `"contra_revenue"`
