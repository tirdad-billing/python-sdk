# IntegrationCapabilityType

## Example Usage

```python
from tirdad_sdk.models import IntegrationCapabilityType

# Open enum: unrecognized values are captured as UnrecognizedStr
value: IntegrationCapabilityType = "checkout"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"checkout"`
- `"auto_charge"`
- `"set_default_method"`
- `"payment_link"`
- `"payment_method_management"`
- `"invoice_sync"`
- `"list_payment_methods"`
- `"add_payment_method"`
- `"delete_payment_method"`
