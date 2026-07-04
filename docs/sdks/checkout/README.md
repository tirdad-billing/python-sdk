# Checkout

## Overview

### Available Operations

* [create_checkout_session](#create_checkout_session) - Create checkout session
* [get_checkout_session](#get_checkout_session) - Get checkout session
* [delete_checkout_session](#delete_checkout_session) - Delete checkout session

## create_checkout_session

Create checkout session

### Example Usage

<!-- UsageSnippet language="python" operationID="createCheckoutSession" method="post" path="/checkout/sessions" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.checkout.create_checkout_session(action="create_subscription", customer_external_id="<id>", payment_provider="razorpay")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                       | Type                                                                            | Required                                                                        | Description                                                                     |
| ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| `action`                                                                        | [models.CheckoutAction](../../models/checkoutaction.md)                         | :heavy_check_mark:                                                              | N/A                                                                             |
| `customer_external_id`                                                          | *str*                                                                           | :heavy_check_mark:                                                              | N/A                                                                             |
| `payment_provider`                                                              | [models.CheckoutPaymentProvider](../../models/checkoutpaymentprovider.md)       | :heavy_check_mark:                                                              | N/A                                                                             |
| `cancel_url`                                                                    | *Optional[str]*                                                                 | :heavy_minus_sign:                                                              | N/A                                                                             |
| `configuration`                                                                 | [Optional[models.CheckoutConfiguration]](../../models/checkoutconfiguration.md) | :heavy_minus_sign:                                                              | N/A                                                                             |
| `failure_url`                                                                   | *Optional[str]*                                                                 | :heavy_minus_sign:                                                              | N/A                                                                             |
| `idempotency_key`                                                               | *Optional[str]*                                                                 | :heavy_minus_sign:                                                              | N/A                                                                             |
| `metadata`                                                                      | Dict[str, *str*]                                                                | :heavy_minus_sign:                                                              | N/A                                                                             |
| `success_url`                                                                   | *Optional[str]*                                                                 | :heavy_minus_sign:                                                              | N/A                                                                             |
| `retries`                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                | :heavy_minus_sign:                                                              | Configuration to override the default retry behavior of the client.             |

### Response

**[models.CheckoutSessionResponse](../../models/checkoutsessionresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 409                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_checkout_session

Get checkout session

### Example Usage

<!-- UsageSnippet language="python" operationID="getCheckoutSession" method="get" path="/checkout/sessions/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.checkout.get_checkout_session(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Checkout session ID                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.CheckoutSessionResponse](../../models/checkoutsessionresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 404                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## delete_checkout_session

Delete checkout session

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteCheckoutSession" method="delete" path="/checkout/sessions/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    tirdad.checkout.delete_checkout_session(id="<id>")

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
| models.errors.ErrorResponse      | 404                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |