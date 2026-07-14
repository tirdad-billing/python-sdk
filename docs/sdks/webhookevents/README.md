# WebhookEvents

## Overview

### Available Operations

* [post_webhook_events_credit_note_created](#post_webhook_events_credit_note_created) - credit_note.created
* [post_webhook_events_credit_note_updated](#post_webhook_events_credit_note_updated) - credit_note.updated
* [post_webhook_events_customer_created](#post_webhook_events_customer_created) - customer.created
* [post_webhook_events_customer_deleted](#post_webhook_events_customer_deleted) - customer.deleted
* [post_webhook_events_customer_updated](#post_webhook_events_customer_updated) - customer.updated
* [post_webhook_events_entitlement_created](#post_webhook_events_entitlement_created) - entitlement.created
* [post_webhook_events_entitlement_deleted](#post_webhook_events_entitlement_deleted) - entitlement.deleted
* [post_webhook_events_entitlement_updated](#post_webhook_events_entitlement_updated) - entitlement.updated
* [post_webhook_events_event_rejected](#post_webhook_events_event_rejected) - event.rejected
* [post_webhook_events_feature_created](#post_webhook_events_feature_created) - feature.created
* [post_webhook_events_feature_deleted](#post_webhook_events_feature_deleted) - feature.deleted
* [post_webhook_events_feature_updated](#post_webhook_events_feature_updated) - feature.updated
* [post_webhook_events_feature_wallet_balance_alert](#post_webhook_events_feature_wallet_balance_alert) - feature.wallet_balance.alert
* [post_webhook_events_invoice_communication_triggered](#post_webhook_events_invoice_communication_triggered) - invoice.communication.triggered
* [post_webhook_events_invoice_payment_overdue](#post_webhook_events_invoice_payment_overdue) - invoice.payment.overdue
* [post_webhook_events_invoice_update](#post_webhook_events_invoice_update) - invoice.update
* [post_webhook_events_invoice_update_finalized](#post_webhook_events_invoice_update_finalized) - invoice.update.finalized
* [post_webhook_events_invoice_update_payment](#post_webhook_events_invoice_update_payment) - invoice.update.payment
* [post_webhook_events_invoice_update_voided](#post_webhook_events_invoice_update_voided) - invoice.update.voided
* [post_webhook_events_payment_created](#post_webhook_events_payment_created) - payment.created
* [post_webhook_events_payment_failed](#post_webhook_events_payment_failed) - payment.failed
* [post_webhook_events_payment_pending](#post_webhook_events_payment_pending) - payment.pending
* [post_webhook_events_payment_success](#post_webhook_events_payment_success) - payment.success
* [post_webhook_events_payment_updated](#post_webhook_events_payment_updated) - payment.updated
* [post_webhook_events_subscription_activated](#post_webhook_events_subscription_activated) - subscription.activated
* [post_webhook_events_subscription_cancelled](#post_webhook_events_subscription_cancelled) - subscription.cancelled
* [post_webhook_events_subscription_created](#post_webhook_events_subscription_created) - subscription.created
* [post_webhook_events_subscription_draft_created](#post_webhook_events_subscription_draft_created) - subscription.draft.created
* [post_webhook_events_subscription_paused](#post_webhook_events_subscription_paused) - subscription.paused
* [post_webhook_events_subscription_phase_created](#post_webhook_events_subscription_phase_created) - subscription.phase.created
* [post_webhook_events_subscription_phase_deleted](#post_webhook_events_subscription_phase_deleted) - subscription.phase.deleted
* [post_webhook_events_subscription_phase_updated](#post_webhook_events_subscription_phase_updated) - subscription.phase.updated
* [post_webhook_events_subscription_renewal_due](#post_webhook_events_subscription_renewal_due) - subscription.renewal.due
* [post_webhook_events_subscription_resumed](#post_webhook_events_subscription_resumed) - subscription.resumed
* [post_webhook_events_subscription_updated](#post_webhook_events_subscription_updated) - subscription.updated
* [post_webhook_events_wallet_created](#post_webhook_events_wallet_created) - wallet.created
* [post_webhook_events_wallet_credit_balance_dropped](#post_webhook_events_wallet_credit_balance_dropped) - wallet.credit_balance.dropped
* [post_webhook_events_wallet_credit_balance_recovered](#post_webhook_events_wallet_credit_balance_recovered) - wallet.credit_balance.recovered
* [post_webhook_events_wallet_ongoing_balance_dropped](#post_webhook_events_wallet_ongoing_balance_dropped) - wallet.ongoing_balance.dropped
* [post_webhook_events_wallet_ongoing_balance_recovered](#post_webhook_events_wallet_ongoing_balance_recovered) - wallet.ongoing_balance.recovered
* [post_webhook_events_wallet_terminated](#post_webhook_events_wallet_terminated) - wallet.terminated
* [post_webhook_events_wallet_transaction_created](#post_webhook_events_wallet_transaction_created) - wallet.transaction.created
* [post_webhook_events_wallet_updated](#post_webhook_events_wallet_updated) - wallet.updated

## post_webhook_events_credit_note_created

Fired when a new credit note is created. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/credit_note.created" method="post" path="/webhook-events/credit_note.created" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_credit_note_created()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoCreditNoteWebhookPayload](../../models/webhookdtocreditnotewebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_credit_note_updated

Fired when a credit note is updated. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/credit_note.updated" method="post" path="/webhook-events/credit_note.updated" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_credit_note_updated()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoCreditNoteWebhookPayload](../../models/webhookdtocreditnotewebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_customer_created

Fired when a new customer is created. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/customer.created" method="post" path="/webhook-events/customer.created" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_customer_created()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoCustomerWebhookPayload](../../models/webhookdtocustomerwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_customer_deleted

Fired when a customer is deleted. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/customer.deleted" method="post" path="/webhook-events/customer.deleted" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_customer_deleted()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoCustomerWebhookPayload](../../models/webhookdtocustomerwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_customer_updated

Fired when a customer is updated. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/customer.updated" method="post" path="/webhook-events/customer.updated" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_customer_updated()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoCustomerWebhookPayload](../../models/webhookdtocustomerwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_entitlement_created

Fired when a new entitlement is created. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/entitlement.created" method="post" path="/webhook-events/entitlement.created" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_entitlement_created()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoEntitlementWebhookPayload](../../models/webhookdtoentitlementwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_entitlement_deleted

Fired when an entitlement is deleted. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/entitlement.deleted" method="post" path="/webhook-events/entitlement.deleted" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_entitlement_deleted()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoEntitlementWebhookPayload](../../models/webhookdtoentitlementwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_entitlement_updated

Fired when an entitlement is updated. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/entitlement.updated" method="post" path="/webhook-events/entitlement.updated" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_entitlement_updated()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoEntitlementWebhookPayload](../../models/webhookdtoentitlementwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_event_rejected

Fired when an ingested usage event produces no meter usage — either no meter is registered for its event name, or meters exist for the name but the event matched none of their filters. Throttled to at most once per configured window per event name. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/event.rejected" method="post" path="/webhook-events/event.rejected" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_event_rejected()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoRejectedEventWebhookPayload](../../models/webhookdtorejectedeventwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_feature_created

Fired when a new feature is created. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/feature.created" method="post" path="/webhook-events/feature.created" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_feature_created()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoFeatureWebhookPayload](../../models/webhookdtofeaturewebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_feature_deleted

Fired when a feature is deleted. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/feature.deleted" method="post" path="/webhook-events/feature.deleted" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_feature_deleted()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoFeatureWebhookPayload](../../models/webhookdtofeaturewebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_feature_updated

Fired when a feature is updated. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/feature.updated" method="post" path="/webhook-events/feature.updated" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_feature_updated()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoFeatureWebhookPayload](../../models/webhookdtofeaturewebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_feature_wallet_balance_alert

Fired when a feature's associated wallet balance crosses an alert threshold. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/feature.wallet_balance.alert" method="post" path="/webhook-events/feature.wallet_balance.alert" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_feature_wallet_balance_alert()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoAlertWebhookPayload](../../models/webhookdtoalertwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_invoice_communication_triggered

Fired when an invoice communication (e.g. email notification) is triggered. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/invoice.communication.triggered" method="post" path="/webhook-events/invoice.communication.triggered" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_invoice_communication_triggered()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoCommunicationWebhookPayload](../../models/webhookdtocommunicationwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_invoice_payment_overdue

Fired when an invoice payment is overdue past the due date. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/invoice.payment.overdue" method="post" path="/webhook-events/invoice.payment.overdue" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_invoice_payment_overdue()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoInvoiceWebhookPayload](../../models/webhookdtoinvoicewebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_invoice_update

Fired when an invoice is updated. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/invoice.update" method="post" path="/webhook-events/invoice.update" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_invoice_update()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoInvoiceWebhookPayload](../../models/webhookdtoinvoicewebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_invoice_update_finalized

Fired when an invoice is finalized and locked for payment. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/invoice.update.finalized" method="post" path="/webhook-events/invoice.update.finalized" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_invoice_update_finalized()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoInvoiceWebhookPayload](../../models/webhookdtoinvoicewebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_invoice_update_payment

Fired when an invoice payment status changes. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/invoice.update.payment" method="post" path="/webhook-events/invoice.update.payment" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_invoice_update_payment()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoInvoiceWebhookPayload](../../models/webhookdtoinvoicewebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_invoice_update_voided

Fired when an invoice is voided (e.g. order cancelled or duplicate). Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/invoice.update.voided" method="post" path="/webhook-events/invoice.update.voided" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_invoice_update_voided()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoInvoiceWebhookPayload](../../models/webhookdtoinvoicewebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_payment_created

Fired when a new payment is created. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/payment.created" method="post" path="/webhook-events/payment.created" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_payment_created()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoPaymentWebhookPayload](../../models/webhookdtopaymentwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_payment_failed

Fired when a payment fails. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/payment.failed" method="post" path="/webhook-events/payment.failed" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_payment_failed()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoPaymentWebhookPayload](../../models/webhookdtopaymentwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_payment_pending

Fired when a payment is pending processing. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/payment.pending" method="post" path="/webhook-events/payment.pending" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_payment_pending()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoPaymentWebhookPayload](../../models/webhookdtopaymentwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_payment_success

Fired when a payment succeeds. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/payment.success" method="post" path="/webhook-events/payment.success" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_payment_success()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoPaymentWebhookPayload](../../models/webhookdtopaymentwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_payment_updated

Fired when a payment is updated. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/payment.updated" method="post" path="/webhook-events/payment.updated" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_payment_updated()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoPaymentWebhookPayload](../../models/webhookdtopaymentwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_subscription_activated

Fired when a draft subscription is activated. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/subscription.activated" method="post" path="/webhook-events/subscription.activated" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_subscription_activated()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoSubscriptionWebhookPayload](../../models/webhookdtosubscriptionwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_subscription_cancelled

Fired when a subscription is cancelled (immediately or end-of-period). Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/subscription.cancelled" method="post" path="/webhook-events/subscription.cancelled" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_subscription_cancelled()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoSubscriptionWebhookPayload](../../models/webhookdtosubscriptionwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_subscription_created

Fired when a new subscription is created. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/subscription.created" method="post" path="/webhook-events/subscription.created" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_subscription_created()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoSubscriptionWebhookPayload](../../models/webhookdtosubscriptionwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_subscription_draft_created

Fired when a new draft subscription is created (not yet activated). Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/subscription.draft.created" method="post" path="/webhook-events/subscription.draft.created" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_subscription_draft_created()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoSubscriptionWebhookPayload](../../models/webhookdtosubscriptionwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_subscription_paused

Fired when a subscription is paused. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/subscription.paused" method="post" path="/webhook-events/subscription.paused" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_subscription_paused()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoSubscriptionWebhookPayload](../../models/webhookdtosubscriptionwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_subscription_phase_created

Fired when a new subscription phase is created. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/subscription.phase.created" method="post" path="/webhook-events/subscription.phase.created" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_subscription_phase_created()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoSubscriptionPhaseWebhookPayload](../../models/webhookdtosubscriptionphasewebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_subscription_phase_deleted

Fired when a subscription phase is deleted. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/subscription.phase.deleted" method="post" path="/webhook-events/subscription.phase.deleted" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_subscription_phase_deleted()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoSubscriptionPhaseWebhookPayload](../../models/webhookdtosubscriptionphasewebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_subscription_phase_updated

Fired when a subscription phase is updated. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/subscription.phase.updated" method="post" path="/webhook-events/subscription.phase.updated" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_subscription_phase_updated()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoSubscriptionPhaseWebhookPayload](../../models/webhookdtosubscriptionphasewebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_subscription_renewal_due

Fired when a subscription renewal is upcoming (cron-driven). Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/subscription.renewal.due" method="post" path="/webhook-events/subscription.renewal.due" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_subscription_renewal_due()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoSubscriptionWebhookPayload](../../models/webhookdtosubscriptionwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_subscription_resumed

Fired when a paused subscription is resumed. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/subscription.resumed" method="post" path="/webhook-events/subscription.resumed" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_subscription_resumed()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoSubscriptionWebhookPayload](../../models/webhookdtosubscriptionwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_subscription_updated

Fired when a subscription is updated (e.g. quantity, billing anchor, or metadata changes). Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/subscription.updated" method="post" path="/webhook-events/subscription.updated" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_subscription_updated()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoSubscriptionWebhookPayload](../../models/webhookdtosubscriptionwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_wallet_created

Fired when a new wallet is created. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/wallet.created" method="post" path="/webhook-events/wallet.created" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_wallet_created()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoWalletWebhookPayload](../../models/webhookdtowalletwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_wallet_credit_balance_dropped

Fired when a wallet's credit balance drops below an alert threshold. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/wallet.credit_balance.dropped" method="post" path="/webhook-events/wallet.credit_balance.dropped" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_wallet_credit_balance_dropped()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoWalletWebhookPayload](../../models/webhookdtowalletwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_wallet_credit_balance_recovered

Fired when a wallet's credit balance recovers above an alert threshold. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/wallet.credit_balance.recovered" method="post" path="/webhook-events/wallet.credit_balance.recovered" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_wallet_credit_balance_recovered()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoWalletWebhookPayload](../../models/webhookdtowalletwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_wallet_ongoing_balance_dropped

Fired when a wallet's ongoing balance drops below an alert threshold. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/wallet.ongoing_balance.dropped" method="post" path="/webhook-events/wallet.ongoing_balance.dropped" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_wallet_ongoing_balance_dropped()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoWalletWebhookPayload](../../models/webhookdtowalletwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_wallet_ongoing_balance_recovered

Fired when a wallet's ongoing balance recovers above an alert threshold. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/wallet.ongoing_balance.recovered" method="post" path="/webhook-events/wallet.ongoing_balance.recovered" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_wallet_ongoing_balance_recovered()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoWalletWebhookPayload](../../models/webhookdtowalletwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_wallet_terminated

Fired when a wallet is terminated. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/wallet.terminated" method="post" path="/webhook-events/wallet.terminated" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_wallet_terminated()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoWalletWebhookPayload](../../models/webhookdtowalletwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_wallet_transaction_created

Fired when a new wallet transaction is created (top-up, deduction, etc.). Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/wallet.transaction.created" method="post" path="/webhook-events/wallet.transaction.created" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_wallet_transaction_created()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoTransactionWebhookPayload](../../models/webhookdtotransactionwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## post_webhook_events_wallet_updated

Fired when a wallet is updated. Doc-only for parsing.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/webhook-events/wallet.updated" method="post" path="/webhook-events/wallet.updated" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.webhook_events.post_webhook_events_wallet_updated()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.WebhookDtoWalletWebhookPayload](../../models/webhookdtowalletwebhookpayload.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |