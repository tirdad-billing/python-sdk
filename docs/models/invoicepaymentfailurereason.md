# InvoicePaymentFailureReason

## Example Usage

```python
from tirdad_sdk.models import InvoicePaymentFailureReason

# Open enum: unrecognized values are captured as UnrecognizedStr
value: InvoicePaymentFailureReason = "payment_method_unavailable"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"payment_method_unavailable"`
- `"provider_error"`
- `"declined"`
