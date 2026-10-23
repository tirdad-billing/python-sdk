# Metric

## Example Usage

```python
from tirdad_sdk.models import Metric

# Open enum: unrecognized values are captured as UnrecognizedStr
value: Metric = "usage_quantity"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"usage_quantity"`
- `"event_count"`
- `"events_volume"`
- `"invoice_total"`
- `"total_receivables"`
- `"receivables_aging"`
- `"days_to_pay"`
- `"arpu"`
- `"arpu_paid"`
- `"credit_consumption"`
- `"credit_topups"`
- `"net_billing"`
- `"invoice_total_issued"`
- `"net_billing_issued"`
- `"active_customers"`
