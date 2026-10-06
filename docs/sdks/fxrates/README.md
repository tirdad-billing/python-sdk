# FXRates

## Overview

### Available Operations

* [create_fx_rate](#create_fx_rate) - Create an FX rate
* [query_fx_rates](#query_fx_rates) - Query FX rates
* [get_fx_rate](#get_fx_rate) - Get an FX rate
* [update_fx_rate](#update_fx_rate) - Update an FX rate
* [delete_fx_rate](#delete_fx_rate) - Delete an FX rate

## create_fx_rate

Configure a fixed exchange rate at tenant, customer or subscription scope. Overrides need a tenant rate for the same pair.

### Example Usage

<!-- UsageSnippet language="python" operationID="createFXRate" method="post" path="/forex" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.fx_rates.create_fx_rate(from_currency="<value>", scope="tenant", to_currency="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                            | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `from_currency`                                                      | *str*                                                                | :heavy_check_mark:                                                   | N/A                                                                  |
| `scope`                                                              | [models.FXRateScope](../../models/fxratescope.md)                    | :heavy_check_mark:                                                   | N/A                                                                  |
| `to_currency`                                                        | *str*                                                                | :heavy_check_mark:                                                   | N/A                                                                  |
| `end_date`                                                           | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_minus_sign:                                                   | N/A                                                                  |
| `metadata`                                                           | Dict[str, *str*]                                                     | :heavy_minus_sign:                                                   | N/A                                                                  |
| `rate`                                                               | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | N/A                                                                  |
| `scope_id`                                                           | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | N/A                                                                  |
| `source`                                                             | [Optional[models.FXRateSource]](../../models/fxratesource.md)        | :heavy_minus_sign:                                                   | N/A                                                                  |
| `start_date`                                                         | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_minus_sign:                                                   | N/A                                                                  |
| `retries`                                                            | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)     | :heavy_minus_sign:                                                   | Configuration to override the default retry behavior of the client.  |

### Response

**[models.FXRateResponse](../../models/fxrateresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## query_fx_rates

Filter FX rates via a request body (POST used for a complex query, but read-only).

### Example Usage

<!-- UsageSnippet language="python" operationID="queryFXRates" method="post" path="/forex/query" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.fx_rates.query_fx_rates()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                               | Type                                                                    | Required                                                                | Description                                                             |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| `end_time`                                                              | [date](https://docs.python.org/3/library/datetime.html#date-objects)    | :heavy_minus_sign:                                                      | N/A                                                                     |
| `expand`                                                                | *Optional[str]*                                                         | :heavy_minus_sign:                                                      | N/A                                                                     |
| `filters`                                                               | List[[models.FilterCondition](../../models/filtercondition.md)]         | :heavy_minus_sign:                                                      | N/A                                                                     |
| `from_currency`                                                         | *Optional[str]*                                                         | :heavy_minus_sign:                                                      | N/A                                                                     |
| `fx_rate_ids`                                                           | List[*str*]                                                             | :heavy_minus_sign:                                                      | N/A                                                                     |
| `limit`                                                                 | *Optional[int]*                                                         | :heavy_minus_sign:                                                      | N/A                                                                     |
| `offset`                                                                | *Optional[int]*                                                         | :heavy_minus_sign:                                                      | N/A                                                                     |
| `order`                                                                 | [Optional[models.FXRateFilterOrder]](../../models/fxratefilterorder.md) | :heavy_minus_sign:                                                      | N/A                                                                     |
| `scope`                                                                 | [Optional[models.FXRateScope]](../../models/fxratescope.md)             | :heavy_minus_sign:                                                      | N/A                                                                     |
| `scope_id`                                                              | *Optional[str]*                                                         | :heavy_minus_sign:                                                      | N/A                                                                     |
| `sort`                                                                  | List[[models.SortCondition](../../models/sortcondition.md)]             | :heavy_minus_sign:                                                      | N/A                                                                     |
| `start_time`                                                            | [date](https://docs.python.org/3/library/datetime.html#date-objects)    | :heavy_minus_sign:                                                      | N/A                                                                     |
| `status`                                                                | [Optional[models.Status]](../../models/status.md)                       | :heavy_minus_sign:                                                      | N/A                                                                     |
| `to_currency`                                                           | *Optional[str]*                                                         | :heavy_minus_sign:                                                      | N/A                                                                     |
| `retries`                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)        | :heavy_minus_sign:                                                      | Configuration to override the default retry behavior of the client.     |

### Response

**[models.ListFXRatesResponse](../../models/listfxratesresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_fx_rate

Load a single FX rate by ID.

### Example Usage

<!-- UsageSnippet language="python" operationID="getFXRate" method="get" path="/forex/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.fx_rates.get_fx_rate(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | FX rate ID                                                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.FXRateResponse](../../models/fxrateresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## update_fx_rate

Update a rate's value, validity window (overrides only) or metadata. Scope, scope_id and the currency pair are immutable.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateFXRate" method="put" path="/forex/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.fx_rates.update_fx_rate(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                            | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `id`                                                                 | *str*                                                                | :heavy_check_mark:                                                   | FX rate ID                                                           |
| `end_date`                                                           | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_minus_sign:                                                   | N/A                                                                  |
| `metadata`                                                           | Dict[str, *str*]                                                     | :heavy_minus_sign:                                                   | N/A                                                                  |
| `rate`                                                               | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | N/A                                                                  |
| `start_date`                                                         | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_minus_sign:                                                   | N/A                                                                  |
| `retries`                                                            | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)     | :heavy_minus_sign:                                                   | Configuration to override the default retry behavior of the client.  |

### Response

**[models.FXRateResponse](../../models/fxrateresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## delete_fx_rate

Archive a customer or subscription override. Tenant rates cannot be deleted.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteFXRate" method="delete" path="/forex/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.fx_rates.delete_fx_rate(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | FX rate ID                                                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[Dict[str, str]](../../models/.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |