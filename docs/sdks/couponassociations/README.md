# CouponAssociations

## Overview

### Available Operations

* [list_coupon_associations](#list_coupon_associations) - List coupon associations
* [get_coupon_association](#get_coupon_association) - Get coupon association

## list_coupon_associations

List coupon associations with optional filters. Coupon associations are created and removed via the subscription modify API.

### Example Usage

<!-- UsageSnippet language="python" operationID="listCouponAssociations" method="get" path="/coupons/associations" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.coupon_associations.list_coupon_associations()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                               | Type                                                                                    | Required                                                                                | Description                                                                             |
| --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| `subscription_ids`                                                                      | List[*str*]                                                                             | :heavy_minus_sign:                                                                      | Filter by subscription IDs (max 100)                                                    |
| `coupon_ids`                                                                            | List[*str*]                                                                             | :heavy_minus_sign:                                                                      | Filter by coupon IDs (max 100)                                                          |
| `active_only`                                                                           | *Optional[bool]*                                                                        | :heavy_minus_sign:                                                                      | Return only currently active associations                                               |
| `expand`                                                                                | *Optional[str]*                                                                         | :heavy_minus_sign:                                                                      | Comma-separated fields: coupon, subscription_line_items, subscription_line_items.prices |
| `limit`                                                                                 | *Optional[int]*                                                                         | :heavy_minus_sign:                                                                      | Page size                                                                               |
| `offset`                                                                                | *Optional[int]*                                                                         | :heavy_minus_sign:                                                                      | Page offset                                                                             |
| `retries`                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                        | :heavy_minus_sign:                                                                      | Configuration to override the default retry behavior of the client.                     |

### Response

**[models.ListCouponAssociationsResponse](../../models/listcouponassociationsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_coupon_association

Get a single coupon association by ID. Coupon associations are created and removed via the subscription modify API.

### Example Usage

<!-- UsageSnippet language="python" operationID="getCouponAssociation" method="get" path="/coupons/associations/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.coupon_associations.get_coupon_association(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Coupon Association ID                                               |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.CouponAssociationResponse](../../models/couponassociationresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 404                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |