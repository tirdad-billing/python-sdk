# RevRecEntityType

## Example Usage

```python
from tirdad_sdk.models import RevRecEntityType

# Open enum: unrecognized values are captured as UnrecognizedStr
value: RevRecEntityType = "subscription"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"subscription"`
- `"subscription_line_item"`
- `"invoice"`
- `"credit_note"`
- `"payment"`
- `"refund"`
- `"pob"`
