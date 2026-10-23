# SelfBilling

## Overview

### Available Operations

* [start_self_billing_checkout](#start_self_billing_checkout) - Start self-billing checkout
* [poll_self_billing_checkout](#poll_self_billing_checkout) - Poll self-billing checkout
* [cancel_self_billing_checkout](#cancel_self_billing_checkout) - Cancel self-billing checkout
* [create_self_billing_portal_session](#create_self_billing_portal_session) - Create self-billing portal session
* [get_self_billing_status](#get_self_billing_status) - Get self-billing status
* [get_self_billing_summary](#get_self_billing_summary) - Get self-billing summary
* [get_tenant_billing_summary](#get_tenant_billing_summary) - Get tenant billing summary

## start_self_billing_checkout

Saves the billing details and opens the checkout that ends the caller tenant's trial.

### Example Usage

<!-- UsageSnippet language="python" operationID="startSelfBillingCheckout" method="post" path="/portal/billing/checkout" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.self_billing.start_self_billing_checkout(address_city="<value>", address_country="<value>", address_line1="856 Hammes Creek", address_postal_code="<value>", email="Pamela.Rogahn3@gmail.com", name="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `address_city`                                                      | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `address_country`                                                   | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `address_line1`                                                     | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `address_postal_code`                                               | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `email`                                                             | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `name`                                                              | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `address_line2`                                                     | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `address_state`                                                     | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `tax_id`                                                            | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.SelfBillingCheckoutResponse](../../models/selfbillingcheckoutresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404, 409                    | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## poll_self_billing_checkout

Reports the caller tenant's checkout and activates the tenant once it is paid.

### Example Usage

<!-- UsageSnippet language="python" operationID="pollSelfBillingCheckout" method="get" path="/portal/billing/checkout/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.self_billing.poll_self_billing_checkout(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Checkout session ID                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.SelfBillingCheckoutResponse](../../models/selfbillingcheckoutresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 404                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## cancel_self_billing_checkout

Cancels the caller tenant's open checkout.

### Example Usage

<!-- UsageSnippet language="python" operationID="cancelSelfBillingCheckout" method="post" path="/portal/billing/checkout/{id}/cancel" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    tirdad.self_billing.cancel_self_billing_checkout(id="<id>")

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Checkout session ID                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## create_self_billing_portal_session

Opens a short-lived customer portal session for the caller tenant.

### Example Usage

<!-- UsageSnippet language="python" operationID="createSelfBillingPortalSession" method="post" path="/portal/billing/portal-session" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.self_billing.create_self_billing_portal_session()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.SelfBillingPortalResponse](../../models/selfbillingportalresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 404                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_self_billing_status

Reports whether self-billing is enabled and the caller tenant's billing status.

### Example Usage

<!-- UsageSnippet language="python" operationID="getSelfBillingStatus" method="get" path="/portal/billing/status" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.self_billing.get_self_billing_status()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.SelfBillingStatusResponse](../../models/selfbillingstatusresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_self_billing_summary

Returns the caller tenant's billing status, subscription, recent invoices and usage.

### Example Usage

<!-- UsageSnippet language="python" operationID="getSelfBillingSummary" method="get" path="/portal/billing/summary" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.self_billing.get_self_billing_summary()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.SelfBillingSummaryResponse](../../models/selfbillingsummaryresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 404                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_tenant_billing_summary

Returns the caller tenant's billing summary; same as /portal/billing/summary.

### Example Usage

<!-- UsageSnippet language="python" operationID="getTenantBillingSummary" method="get" path="/tenants/billing" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.self_billing.get_tenant_billing_summary()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.SelfBillingSummaryResponse](../../models/selfbillingsummaryresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 404                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |