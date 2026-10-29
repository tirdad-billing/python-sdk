# JournalEventType

## Example Usage

```python
from tirdad_sdk.models import JournalEventType

# Open enum: unrecognized values are captured as UnrecognizedStr
value: JournalEventType = "invoice_finalized"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"invoice_finalized"`
- `"invoice_voided"`
- `"credit_note_finalized"`
- `"credit_note_voided"`
- `"payment_succeeded"`
- `"payment_reversed"`
- `"refund_succeeded"`
- `"revenue_earned"`
- `"revenue_offset"`
