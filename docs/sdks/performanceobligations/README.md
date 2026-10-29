# PerformanceObligations

## Overview

### Available Operations

* [query_performance_obligation](#query_performance_obligation) - Query performance obligations
* [get_performance_obligation](#get_performance_obligation) - Get performance obligation

## query_performance_obligation

Use when searching performance obligations by contract, customer, status or recognition method. Returns a paginated list.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryPerformanceObligation" method="post" path="/performance_obligations/search" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.performance_obligations.query_performance_obligation()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                               | Type                                                                                    | Required                                                                                | Description                                                                             |
| --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| `contract_ids`                                                                          | List[*str*]                                                                             | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `customer_ids`                                                                          | List[*str*]                                                                             | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `end_time`                                                                              | [date](https://docs.python.org/3/library/datetime.html#date-objects)                    | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `expand`                                                                                | *Optional[str]*                                                                         | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `filters`                                                                               | List[[models.FilterCondition](../../models/filtercondition.md)]                         | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `limit`                                                                                 | *Optional[int]*                                                                         | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `offset`                                                                                | *Optional[int]*                                                                         | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `order`                                                                                 | [Optional[models.PobFilterOrder]](../../models/pobfilterorder.md)                       | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `performance_obligation_ids`                                                            | List[*str*]                                                                             | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `pob_statuses`                                                                          | List[[models.PerformanceObligationStatus](../../models/performanceobligationstatus.md)] | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `recognition_methods`                                                                   | List[[models.RecognitionMethod](../../models/recognitionmethod.md)]                     | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `sort`                                                                                  | List[[models.SortCondition](../../models/sortcondition.md)]                             | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `start_time`                                                                            | [date](https://docs.python.org/3/library/datetime.html#date-objects)                    | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `status`                                                                                | [Optional[models.Status]](../../models/status.md)                                       | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `retries`                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                        | :heavy_minus_sign:                                                                      | Configuration to override the default retry behavior of the client.                     |

### Response

**[models.ListPerformanceObligationsResponse](../../models/listperformanceobligationsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_performance_obligation

Use when you need to load a single performance obligation with the subscription line items it covers. Performance obligations are derived from subscriptions and are read-only.

### Example Usage

<!-- UsageSnippet language="python" operationID="getPerformanceObligation" method="get" path="/performance_obligations/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.performance_obligations.get_performance_obligation(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Performance obligation ID                                           |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.PerformanceObligationResponse](../../models/performanceobligationresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |