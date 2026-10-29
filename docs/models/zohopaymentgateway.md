# ZohoPaymentGateway

## Example Usage

```python
from tirdad_sdk.models import ZohoPaymentGateway

# Open enum: unrecognized values are captured as UnrecognizedStr
value: ZohoPaymentGateway = "paypal"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"paypal"`
- `"stripe"`
- `"authorize_net"`
- `"payflow_pro"`
- `"2checkout"`
- `"braintree"`
- `"razorpay"`
