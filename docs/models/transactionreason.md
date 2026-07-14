# TransactionReason

## Example Usage

```python
from tirdad_sdk.models import TransactionReason

# Open enum: unrecognized values are captured as UnrecognizedStr
value: TransactionReason = "INVOICE_PAYMENT"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"INVOICE_PAYMENT"`
- `"FREE_CREDIT_GRANT"`
- `"SUBSCRIPTION_CREDIT_GRANT"`
- `"PURCHASED_CREDIT_INVOICED"`
- `"PURCHASED_CREDIT_DIRECT"`
- `"CREDIT_NOTE"`
- `"CREDIT_EXPIRED"`
- `"WALLET_TERMINATION"`
- `"MANUAL_BALANCE_DEBIT"`
- `"CREDIT_ADJUSTMENT"`
- `"INVOICE_VOID_REFUND"`
- `"PURCHASED_CREDIT_BONUS"`
