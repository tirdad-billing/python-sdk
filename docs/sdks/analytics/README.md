# Analytics

## Overview

### Available Operations

* [query_analytics](#query_analytics) - Run an ad-hoc analytics query
* [create_analytics_view](#create_analytics_view) - Create an analytics view
* [query_analytics_view](#query_analytics_view) - Query an analytics view

## query_analytics

Resolves the given view definition against the supplied variables and executes it.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryAnalytics" method="post" path="/analytics/query" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.analytics.query_analytics(definition={
        "metrics": [
            "usage_quantity",
        ],
        "shape": "breakdown",
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `definition`                                                              | [models.AnalyticsViewDefinition](../../models/analyticsviewdefinition.md) | :heavy_check_mark:                                                        | N/A                                                                       |
| `variables`                                                               | Dict[str, List[*str*]]                                                    | :heavy_minus_sign:                                                        | N/A                                                                       |
| `retries`                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)          | :heavy_minus_sign:                                                        | Configuration to override the default retry behavior of the client.       |

### Response

**[models.AnalyticsQueryResult](../../models/analyticsqueryresult.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## create_analytics_view

Persists a named view definition that can later be queried by ID.

### Example Usage

<!-- UsageSnippet language="python" operationID="createAnalyticsView" method="post" path="/analytics/views" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.analytics.create_analytics_view(definition={
        "metrics": [
            "event_count",
        ],
        "shape": "breakdown",
    }, name="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `definition`                                                              | [models.AnalyticsViewDefinition](../../models/analyticsviewdefinition.md) | :heavy_check_mark:                                                        | N/A                                                                       |
| `name`                                                                    | *str*                                                                     | :heavy_check_mark:                                                        | N/A                                                                       |
| `retries`                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)          | :heavy_minus_sign:                                                        | Configuration to override the default retry behavior of the client.       |

### Response

**[models.ViewResponse](../../models/viewresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## query_analytics_view

Resolves the view's definition against the supplied variables and executes it.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryAnalyticsView" method="post" path="/analytics/views/{id}/query" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.analytics.query_analytics_view(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | View ID                                                             |
| `variables`                                                         | Dict[str, List[*str*]]                                              | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.AnalyticsQueryResult](../../models/analyticsqueryresult.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |