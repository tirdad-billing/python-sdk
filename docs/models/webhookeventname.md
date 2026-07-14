# WebhookEventName

## Example Usage

```python
from tirdad_sdk.models import WebhookEventName

# Open enum: unrecognized values are captured as UnrecognizedStr
value: WebhookEventName = "subscription.created"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"subscription.created"`
- `"subscription.draft.created"`
- `"subscription.activated"`
- `"subscription.updated"`
- `"subscription.paused"`
- `"subscription.cancelled"`
- `"subscription.resumed"`
- `"subscription.phase.created"`
- `"subscription.phase.updated"`
- `"subscription.phase.deleted"`
- `"feature.created"`
- `"feature.updated"`
- `"feature.deleted"`
- `"feature.wallet_balance.alert"`
- `"entitlement.created"`
- `"entitlement.updated"`
- `"entitlement.deleted"`
- `"wallet.created"`
- `"wallet.updated"`
- `"wallet.terminated"`
- `"wallet.transaction.created"`
- `"payment.created"`
- `"payment.updated"`
- `"payment.failed"`
- `"payment.success"`
- `"payment.pending"`
- `"customer.created"`
- `"customer.updated"`
- `"customer.deleted"`
- `"invoice.update.finalized"`
- `"invoice.update.payment"`
- `"invoice.update.voided"`
- `"invoice.update"`
- `"invoice.payment.overdue"`
- `"wallet.credit_balance.dropped"`
- `"wallet.credit_balance.recovered"`
- `"wallet.ongoing_balance.dropped"`
- `"wallet.ongoing_balance.recovered"`
- `"subscription.spend.threshold_reached"`
- `"subscription.spend.threshold_recovered"`
- `"subscription.line_item_spend.threshold_reached"`
- `"subscription.line_item_spend.threshold_recovered"`
- `"subscription.group_spend.threshold_reached"`
- `"subscription.group_spend.threshold_recovered"`
- `"subscription.renewal.due"`
- `"invoice.communication.triggered"`
- `"credit_note.created"`
- `"credit_note.updated"`
- `"checkout.session.initiated"`
- `"checkout.session.completed"`
- `"checkout.session.failed"`
- `"checkout.session.expired"`
- `"event.rejected"`
