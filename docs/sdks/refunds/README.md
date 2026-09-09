# Refunds

## Overview

### Available Operations

* [list_refunds](#list_refunds) - List refunds
* [get_refund](#get_refund) - Get refund
* [retry_refund](#retry_refund) - Retry refund

## list_refunds

Use to see where refunded money actually went and whether it has settled. Filter by invoice_ids to get every settlement row for one invoice.

### Example Usage

<!-- UsageSnippet language="python" operationID="listRefunds" method="get" path="/refunds" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.refunds.list_refunds()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `invoice_ids`                                                       | List[*str*]                                                         | :heavy_minus_sign:                                                  | Filter by invoice IDs                                               |
| `payment_ids`                                                       | List[*str*]                                                         | :heavy_minus_sign:                                                  | Filter by payment IDs                                               |
| `credit_note_ids`                                                   | List[*str*]                                                         | :heavy_minus_sign:                                                  | Filter by credit note IDs                                           |
| `refund_statuses`                                                   | List[*str*]                                                         | :heavy_minus_sign:                                                  | Filter by refund status                                             |
| `refund_destinations`                                               | List[*str*]                                                         | :heavy_minus_sign:                                                  | Filter by refund destination                                        |
| `gateway`                                                           | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Filter by payment gateway                                           |
| `only_settled`                                                      | *Optional[bool]*                                                    | :heavy_minus_sign:                                                  | Only refunds that have settled                                      |
| `limit`                                                             | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | Limit                                                               |
| `offset`                                                            | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | Offset                                                              |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ListRefundsResponse](../../models/listrefundsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 401                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_refund

Use to inspect a single refund: its destination, settled amount and failure reason.

### Example Usage

<!-- UsageSnippet language="python" operationID="getRefund" method="get" path="/refunds/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.refunds.get_refund(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Refund ID                                                           |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.RefundResponse](../../models/refundresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## retry_refund

Use when a refund failed or is stuck pending. A failed gateway refund is retried into the customer's wallet; an already-settled refund is rejected.

### Example Usage

<!-- UsageSnippet language="python" operationID="retryRefund" method="post" path="/refunds/{id}/retry" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.refunds.retry_refund(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Refund ID                                                           |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.RefundResponse](../../models/refundresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 401, 404                    | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |