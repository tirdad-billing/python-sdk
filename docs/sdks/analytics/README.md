# Analytics

## Overview

### Available Operations

* [query_analytics](#query_analytics) - Run an ad-hoc analytics query
* [list_analytics_reports](#list_analytics_reports) - List financial reports
* [run_analytics_report](#run_analytics_report) - Run a financial report
* [get_revenue_analytics](#get_revenue_analytics) - Query revenue analytics
* [list_analytics_views](#list_analytics_views) - List analytics views
* [create_analytics_view](#create_analytics_view) - Create an analytics view
* [get_analytics_view](#get_analytics_view) - Get an analytics view
* [update_analytics_view](#update_analytics_view) - Update an analytics view
* [delete_analytics_view](#delete_analytics_view) - Delete an analytics view
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
            "events_volume",
        ],
        "shape": "scalar",
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

## list_analytics_reports

Returns the catalog of reports with their allowed shapes, dimensions and grains.

### Example Usage

<!-- UsageSnippet language="python" operationID="listAnalyticsReports" method="get" path="/analytics/reports" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.analytics.list_analytics_reports()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ReportCatalogResponse](../../models/reportcatalogresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 403                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## run_analytics_report

Runs the report identified by key. range is an absolute YYYY-MM-DD..YYYY-MM-DD (end exclusive) or last_N_days. compare is previous_period or previous_year.

### Example Usage

<!-- UsageSnippet language="python" operationID="runAnalyticsReport" method="post" path="/analytics/reports/{key}/query" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.analytics.run_analytics_report(key="<key>", range="2026-09-01..2026-10-01", shape="breakdown")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                               | Type                                                                                    | Required                                                                                | Description                                                                             | Example                                                                                 |
| --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| `key`                                                                                   | *str*                                                                                   | :heavy_check_mark:                                                                      | Report key                                                                              |                                                                                         |
| `range`                                                                                 | *str*                                                                                   | :heavy_check_mark:                                                                      | N/A                                                                                     | 2026-09-01..2026-10-01                                                                  |
| `shape`                                                                                 | [models.ReportQueryRequestShape](../../models/reportqueryrequestshape.md)               | :heavy_check_mark:                                                                      | N/A                                                                                     |                                                                                         |
| `compare`                                                                               | [Optional[models.ReportQueryRequestCompare]](../../models/reportqueryrequestcompare.md) | :heavy_minus_sign:                                                                      | N/A                                                                                     |                                                                                         |
| `currency`                                                                              | *Optional[str]*                                                                         | :heavy_minus_sign:                                                                      | N/A                                                                                     |                                                                                         |
| `dimensions`                                                                            | List[*str*]                                                                             | :heavy_minus_sign:                                                                      | N/A                                                                                     |                                                                                         |
| `filters`                                                                               | List[[models.ReportFilter](../../models/reportfilter.md)]                               | :heavy_minus_sign:                                                                      | N/A                                                                                     |                                                                                         |
| `grain`                                                                                 | [Optional[models.ReportQueryRequestGrain]](../../models/reportqueryrequestgrain.md)     | :heavy_minus_sign:                                                                      | N/A                                                                                     |                                                                                         |
| `limit`                                                                                 | *Optional[int]*                                                                         | :heavy_minus_sign:                                                                      | N/A                                                                                     |                                                                                         |
| `sort`                                                                                  | List[[models.ReportSort](../../models/reportsort.md)]                                   | :heavy_minus_sign:                                                                      | N/A                                                                                     |                                                                                         |
| `retries`                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                        | :heavy_minus_sign:                                                                      | Configuration to override the default retry behavior of the client.                     |                                                                                         |

### Response

**[models.AnalyticsQueryResult](../../models/analyticsqueryresult.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 403, 404                    | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_revenue_analytics

Aggregates revenue_facts by the requested dimensions at day/period/total granularity. allocation_policy places whole-period charges on their booked day (billed) or spreads them across the period (amortized); include_adjustments breaks out true-up/overage/revert amounts as labeled rows. Requires the tenant's revenue analytics setting.

### Example Usage

<!-- UsageSnippet language="python" operationID="getRevenueAnalytics" method="post" path="/analytics/revenue" -->
```python
from tirdad_sdk import Tirdad
from tirdad_sdk.utils import parse_datetime


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.analytics.get_revenue_analytics(start_time=parse_datetime("2026-09-19T08:36:56.747Z"))

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                                                                             | Type                                                                                                                                                                                                                                                                                                                                                                  | Required                                                                                                                                                                                                                                                                                                                                                              | Description                                                                                                                                                                                                                                                                                                                                                           |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `start_time`                                                                                                                                                                                                                                                                                                                                                          | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                                                                                                                                                                                                                                                                                  | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                    | StartTime/EndTime bound the day range (inclusive days derived in UTC).<br/>EndTime is optional and defaults to now.                                                                                                                                                                                                                                                   |
| `allocation_policy`                                                                                                                                                                                                                                                                                                                                                   | [Optional[models.RevenueAllocationPolicy]](../../models/revenueallocationpolicy.md)                                                                                                                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                    | N/A                                                                                                                                                                                                                                                                                                                                                                   |
| `currency`                                                                                                                                                                                                                                                                                                                                                            | *Optional[str]*                                                                                                                                                                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                    | N/A                                                                                                                                                                                                                                                                                                                                                                   |
| `customer_ids`                                                                                                                                                                                                                                                                                                                                                        | List[*str*]                                                                                                                                                                                                                                                                                                                                                           | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                    | Filters restrict the rows before aggregation.                                                                                                                                                                                                                                                                                                                         |
| `end_time`                                                                                                                                                                                                                                                                                                                                                            | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                                                                                                                                                                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                    | N/A                                                                                                                                                                                                                                                                                                                                                                   |
| `granularity`                                                                                                                                                                                                                                                                                                                                                         | [Optional[models.RevenueGranularity]](../../models/revenuegranularity.md)                                                                                                                                                                                                                                                                                             | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                    | N/A                                                                                                                                                                                                                                                                                                                                                                   |
| `group_by`                                                                                                                                                                                                                                                                                                                                                            | List[*str*]                                                                                                                                                                                                                                                                                                                                                           | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                    | GroupBy dimensions: revenue_source, source (the event source recorded in<br/>meter_usage; requires customer_ids or subscription_ids), customer_id,<br/>subscription_id, price_id, meter_id, currency. revenue_source is always<br/>applied — every row says what kind of revenue it is — and requested<br/>dimensions are added on top.                               |
| `include_adjustments`                                                                                                                                                                                                                                                                                                                                                 | *Optional[bool]*                                                                                                                                                                                                                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                    | IncludeAdjustments breaks the non-obvious components — commitment<br/>true-ups, overage and revert (contra) rows — out as their own rows,<br/>each labeled with its kind in adjustment_type. Off, they fold into<br/>their parent buckets (true-up/overage into usage, reverts into their<br/>own source) so visible rows read as plain usage/fixed. Totals are<br/>identical either way. |
| `meter_ids`                                                                                                                                                                                                                                                                                                                                                           | List[*str*]                                                                                                                                                                                                                                                                                                                                                           | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                    | N/A                                                                                                                                                                                                                                                                                                                                                                   |
| `price_ids`                                                                                                                                                                                                                                                                                                                                                           | List[*str*]                                                                                                                                                                                                                                                                                                                                                           | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                    | N/A                                                                                                                                                                                                                                                                                                                                                                   |
| `status`                                                                                                                                                                                                                                                                                                                                                              | [Optional[models.FactStatus]](../../models/factstatus.md)                                                                                                                                                                                                                                                                                                             | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                    | N/A                                                                                                                                                                                                                                                                                                                                                                   |
| `subscription_ids`                                                                                                                                                                                                                                                                                                                                                    | List[*str*]                                                                                                                                                                                                                                                                                                                                                           | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                    | N/A                                                                                                                                                                                                                                                                                                                                                                   |
| `retries`                                                                                                                                                                                                                                                                                                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                    | Configuration to override the default retry behavior of the client.                                                                                                                                                                                                                                                                                                   |

### Response

**[models.RevenueAnalyticsResponse](../../models/revenueanalyticsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 403                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## list_analytics_views

Lists saved views, optionally filtered by family.

### Example Usage

<!-- UsageSnippet language="python" operationID="listAnalyticsViews" method="get" path="/analytics/views" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.analytics.list_analytics_views()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `family`                                                            | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Filter by view family                                               |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ListViewsResponse](../../models/listviewsresponse.md)**

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
            "net_billing",
        ],
        "shape": "scalar",
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

## get_analytics_view

Returns a saved view by ID.

### Example Usage

<!-- UsageSnippet language="python" operationID="getAnalyticsView" method="get" path="/analytics/views/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.analytics.get_analytics_view(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | View ID                                                             |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ViewResponse](../../models/viewresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 404                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## update_analytics_view

Replaces the name and definition of a saved view.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateAnalyticsView" method="put" path="/analytics/views/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.analytics.update_analytics_view(id="<id>", definition={
        "metrics": [],
        "shape": "timeseries",
    }, name="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `id`                                                                      | *str*                                                                     | :heavy_check_mark:                                                        | View ID                                                                   |
| `definition`                                                              | [models.AnalyticsViewDefinition](../../models/analyticsviewdefinition.md) | :heavy_check_mark:                                                        | N/A                                                                       |
| `name`                                                                    | *str*                                                                     | :heavy_check_mark:                                                        | N/A                                                                       |
| `retries`                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)          | :heavy_minus_sign:                                                        | Configuration to override the default retry behavior of the client.       |

### Response

**[models.ViewResponse](../../models/viewresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## delete_analytics_view

Deletes a saved view by ID.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteAnalyticsView" method="delete" path="/analytics/views/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    tirdad.analytics.delete_analytics_view(id="<id>")

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | View ID                                                             |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 404                              | application/json                 |
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