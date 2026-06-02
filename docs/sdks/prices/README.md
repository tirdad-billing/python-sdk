# Prices

## Overview

### Available Operations

* [create_price](#create_price) - Create price
* [create_prices_bulk](#create_prices_bulk) - Create prices in bulk
* [get_price_by_lookup_key](#get_price_by_lookup_key) - Get price by lookup key
* [query_price](#query_price) - Query prices
* [get_price](#get_price) - Get price
* [update_price](#update_price) - Update price
* [delete_price](#delete_price) - Delete price

## create_price

Use when adding a new price to a plan or catalog (e.g. per-seat, flat, or metered). Ideal for both simple and usage-based pricing.

### Example Usage

<!-- UsageSnippet language="python" operationID="createPrice" method="post" path="/prices" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.prices.create_price(billing_model="PACKAGE", billing_period="HALF_YEARLY", currency="Serbian Dinar", entity_id="<id>", entity_type="PRICE", invoice_cadence="ARREAR", price_unit_type="CUSTOM", type_="USAGE")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                         | Type                                                                              | Required                                                                          | Description                                                                       |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `billing_model`                                                                   | [models.BillingModel](../../models/billingmodel.md)                               | :heavy_check_mark:                                                                | N/A                                                                               |
| `billing_period`                                                                  | [models.BillingPeriod](../../models/billingperiod.md)                             | :heavy_check_mark:                                                                | N/A                                                                               |
| `currency`                                                                        | *str*                                                                             | :heavy_check_mark:                                                                | N/A                                                                               |
| `entity_id`                                                                       | *str*                                                                             | :heavy_check_mark:                                                                | N/A                                                                               |
| `entity_type`                                                                     | [models.PriceEntityType](../../models/priceentitytype.md)                         | :heavy_check_mark:                                                                | N/A                                                                               |
| `invoice_cadence`                                                                 | [models.InvoiceCadence](../../models/invoicecadence.md)                           | :heavy_check_mark:                                                                | N/A                                                                               |
| `price_unit_type`                                                                 | [models.PriceUnitType](../../models/priceunittype.md)                             | :heavy_check_mark:                                                                | N/A                                                                               |
| `type`                                                                            | [models.PriceType](../../models/pricetype.md)                                     | :heavy_check_mark:                                                                | N/A                                                                               |
| `amount`                                                                          | *Optional[str]*                                                                   | :heavy_minus_sign:                                                                | N/A                                                                               |
| `billing_period_count`                                                            | *Optional[int]*                                                                   | :heavy_minus_sign:                                                                | N/A                                                                               |
| `description`                                                                     | *Optional[str]*                                                                   | :heavy_minus_sign:                                                                | N/A                                                                               |
| `display_name`                                                                    | *Optional[str]*                                                                   | :heavy_minus_sign:                                                                | N/A                                                                               |
| `end_date`                                                                        | [date](https://docs.python.org/3/library/datetime.html#date-objects)              | :heavy_minus_sign:                                                                | N/A                                                                               |
| `filter_values`                                                                   | Dict[str, List[*str*]]                                                            | :heavy_minus_sign:                                                                | N/A                                                                               |
| `group_id`                                                                        | *Optional[str]*                                                                   | :heavy_minus_sign:                                                                | GroupID is the id of the group to add the price to                                |
| `lookup_key`                                                                      | *Optional[str]*                                                                   | :heavy_minus_sign:                                                                | N/A                                                                               |
| `metadata`                                                                        | Dict[str, *str*]                                                                  | :heavy_minus_sign:                                                                | N/A                                                                               |
| `meter_id`                                                                        | *Optional[str]*                                                                   | :heavy_minus_sign:                                                                | N/A                                                                               |
| `min_quantity`                                                                    | *Optional[int]*                                                                   | :heavy_minus_sign:                                                                | MinQuantity is the minimum quantity of the price                                  |
| `price_unit_config`                                                               | [Optional[models.PriceUnitConfig]](../../models/priceunitconfig.md)               | :heavy_minus_sign:                                                                | N/A                                                                               |
| `start_date`                                                                      | [date](https://docs.python.org/3/library/datetime.html#date-objects)              | :heavy_minus_sign:                                                                | N/A                                                                               |
| `tier_mode`                                                                       | [Optional[models.BillingTier]](../../models/billingtier.md)                       | :heavy_minus_sign:                                                                | N/A                                                                               |
| `tiers`                                                                           | List[[models.CreatePriceTier](../../models/createpricetier.md)]                   | :heavy_minus_sign:                                                                | N/A                                                                               |
| `transform_quantity`                                                              | [Optional[models.PriceTransformQuantity]](../../models/pricetransformquantity.md) | :heavy_minus_sign:                                                                | N/A                                                                               |
| `trial_period_days`                                                               | *Optional[int]*                                                                   | :heavy_minus_sign:                                                                | N/A                                                                               |
| `retries`                                                                         | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                  | :heavy_minus_sign:                                                                | Configuration to override the default retry behavior of the client.               |

### Response

**[models.PriceResponse](../../models/priceresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## create_prices_bulk

Use when creating many prices at once (e.g. importing a catalog or setting up a plan with multiple tiers).

### Example Usage

<!-- UsageSnippet language="python" operationID="createPricesBulk" method="post" path="/prices/bulk" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.prices.create_prices_bulk(items=[])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                             | Type                                                                  | Required                                                              | Description                                                           |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| `items`                                                               | List[[models.CreatePriceRequest](../../models/createpricerequest.md)] | :heavy_check_mark:                                                    | N/A                                                                   |
| `retries`                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)      | :heavy_minus_sign:                                                    | Configuration to override the default retry behavior of the client.   |

### Response

**[models.CreateBulkPriceResponse](../../models/createbulkpriceresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_price_by_lookup_key

Use when resolving a price by external id (e.g. from your catalog or CMS). Ideal for integrations.

### Example Usage

<!-- UsageSnippet language="python" operationID="getPriceByLookupKey" method="get" path="/prices/lookup/{lookup_key}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.prices.get_price_by_lookup_key(lookup_key="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `lookup_key`                                                        | *str*                                                               | :heavy_check_mark:                                                  | Lookup key                                                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.PriceResponse](../../models/priceresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## query_price

Use when listing or searching prices (e.g. plan builder or catalog). Returns a paginated list; supports filtering and sorting.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryPrice" method="post" path="/prices/search" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.prices.query_price(allow_expired_prices=False)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                             | Type                                                                  | Required                                                              | Description                                                           |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| `allow_expired_prices`                                                | *Optional[bool]*                                                      | :heavy_minus_sign:                                                    | N/A                                                                   |
| `end_time`                                                            | [date](https://docs.python.org/3/library/datetime.html#date-objects)  | :heavy_minus_sign:                                                    | N/A                                                                   |
| `entity_ids`                                                          | List[*str*]                                                           | :heavy_minus_sign:                                                    | N/A                                                                   |
| `entity_type`                                                         | [Optional[models.PriceEntityType]](../../models/priceentitytype.md)   | :heavy_minus_sign:                                                    | N/A                                                                   |
| `expand`                                                              | *Optional[str]*                                                       | :heavy_minus_sign:                                                    | N/A                                                                   |
| `filters`                                                             | List[[models.FilterCondition](../../models/filtercondition.md)]       | :heavy_minus_sign:                                                    | DSL filters                                                           |
| `limit`                                                               | *Optional[int]*                                                       | :heavy_minus_sign:                                                    | N/A                                                                   |
| `meter_ids`                                                           | List[*str*]                                                           | :heavy_minus_sign:                                                    | N/A                                                                   |
| `offset`                                                              | *Optional[int]*                                                       | :heavy_minus_sign:                                                    | N/A                                                                   |
| `order`                                                               | [Optional[models.PriceFilterOrder]](../../models/pricefilterorder.md) | :heavy_minus_sign:                                                    | N/A                                                                   |
| `parent_price_id`                                                     | *Optional[str]*                                                       | :heavy_minus_sign:                                                    | N/A                                                                   |
| `plan_ids`                                                            | List[*str*]                                                           | :heavy_minus_sign:                                                    | Price override filtering fields                                       |
| `price_ids`                                                           | List[*str*]                                                           | :heavy_minus_sign:                                                    | N/A                                                                   |
| `sort`                                                                | *Optional[str]*                                                       | :heavy_minus_sign:                                                    | N/A                                                                   |
| `start_date_lt`                                                       | *Optional[str]*                                                       | :heavy_minus_sign:                                                    | N/A                                                                   |
| `start_time`                                                          | [date](https://docs.python.org/3/library/datetime.html#date-objects)  | :heavy_minus_sign:                                                    | N/A                                                                   |
| `status`                                                              | [Optional[models.Status]](../../models/status.md)                     | :heavy_minus_sign:                                                    | N/A                                                                   |
| `subscription_id`                                                     | *Optional[str]*                                                       | :heavy_minus_sign:                                                    | N/A                                                                   |
| `retries`                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)      | :heavy_minus_sign:                                                    | Configuration to override the default retry behavior of the client.   |

### Response

**[models.ListPricesResponse](../../models/listpricesresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_price

Use when you need to load a single price (e.g. for display or editing). Response includes expanded meter and price unit when applicable.

### Example Usage

<!-- UsageSnippet language="python" operationID="getPrice" method="get" path="/prices/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.prices.get_price(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Price ID                                                            |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.PriceResponse](../../models/priceresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## update_price

Use when changing price configuration (e.g. amount, billing scheme, or metadata).

### Example Usage

<!-- UsageSnippet language="python" operationID="updatePrice" method="put" path="/prices/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.prices.update_price(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                           | Type                                                                                                                                                                                                                                                                                                | Required                                                                                                                                                                                                                                                                                            | Description                                                                                                                                                                                                                                                                                         |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                                                                                                                                                                                                                | *str*                                                                                                                                                                                                                                                                                               | :heavy_check_mark:                                                                                                                                                                                                                                                                                  | Price ID                                                                                                                                                                                                                                                                                            |
| `amount`                                                                                                                                                                                                                                                                                            | *Optional[str]*                                                                                                                                                                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                                                                                                  | Amount is the new price amount that overrides the original price (optional)                                                                                                                                                                                                                         |
| `billing_model`                                                                                                                                                                                                                                                                                     | [Optional[models.BillingModel]](../../models/billingmodel.md)                                                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                                                                                                  | N/A                                                                                                                                                                                                                                                                                                 |
| `description`                                                                                                                                                                                                                                                                                       | *Optional[str]*                                                                                                                                                                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                                                                                                  | N/A                                                                                                                                                                                                                                                                                                 |
| `display_name`                                                                                                                                                                                                                                                                                      | *Optional[str]*                                                                                                                                                                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                                                                                                  | N/A                                                                                                                                                                                                                                                                                                 |
| `effective_from`                                                                                                                                                                                                                                                                                    | *Optional[str]*                                                                                                                                                                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                                                                                                  | N/A                                                                                                                                                                                                                                                                                                 |
| `group_id`                                                                                                                                                                                                                                                                                          | *Optional[str]*                                                                                                                                                                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                                                                                                  | GroupID is the id of the group to update the price in.<br/>If not provided (nil), the group will not be changed<br/>If provided as empty string (""), the group will be removed (price will be ungrouped)<br/>If provided as a group ID, the price will be assigned to that group (must exist and be published) |
| `lookup_key`                                                                                                                                                                                                                                                                                        | *Optional[str]*                                                                                                                                                                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                                                                                                  | All price fields that can be updated<br/>Non-critical fields (can be updated directly)                                                                                                                                                                                                              |
| `metadata`                                                                                                                                                                                                                                                                                          | Dict[str, *str*]                                                                                                                                                                                                                                                                                    | :heavy_minus_sign:                                                                                                                                                                                                                                                                                  | N/A                                                                                                                                                                                                                                                                                                 |
| `price_unit_amount`                                                                                                                                                                                                                                                                                 | *Optional[str]*                                                                                                                                                                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                                                                                                  | PriceUnitAmount is the price unit amount (for CUSTOM price unit type, FLAT_FEE/PACKAGE billing models)                                                                                                                                                                                              |
| `price_unit_tiers`                                                                                                                                                                                                                                                                                  | List[[models.CreatePriceTier](../../models/createpricetier.md)]                                                                                                                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                                                                                                  | PriceUnitTiers are the price unit tiers (for CUSTOM price unit type, TIERED billing model)                                                                                                                                                                                                          |
| `tier_mode`                                                                                                                                                                                                                                                                                         | [Optional[models.BillingTier]](../../models/billingtier.md)                                                                                                                                                                                                                                         | :heavy_minus_sign:                                                                                                                                                                                                                                                                                  | N/A                                                                                                                                                                                                                                                                                                 |
| `tiers`                                                                                                                                                                                                                                                                                             | List[[models.CreatePriceTier](../../models/createpricetier.md)]                                                                                                                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                                                                                                  | Tiers determines the pricing tiers for this line item                                                                                                                                                                                                                                               |
| `transform_quantity`                                                                                                                                                                                                                                                                                | [Optional[models.PriceTransformQuantity]](../../models/pricetransformquantity.md)                                                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                                                                                                                  | N/A                                                                                                                                                                                                                                                                                                 |
| `retries`                                                                                                                                                                                                                                                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                                                                                                    | :heavy_minus_sign:                                                                                                                                                                                                                                                                                  | Configuration to override the default retry behavior of the client.                                                                                                                                                                                                                                 |

### Response

**[models.PriceResponse](../../models/priceresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## delete_price

Use when retiring a price (e.g. end-of-life or replacement). Optional effective date or cascade for subscriptions.

### Example Usage

<!-- UsageSnippet language="python" operationID="deletePrice" method="delete" path="/prices/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.prices.delete_price(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                            | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `id`                                                                 | *str*                                                                | :heavy_check_mark:                                                   | Price ID                                                             |
| `end_date`                                                           | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_minus_sign:                                                   | N/A                                                                  |
| `retries`                                                            | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)     | :heavy_minus_sign:                                                   | Configuration to override the default retry behavior of the client.  |

### Response

**[models.SuccessResponse](../../models/successresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |