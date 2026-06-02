# Alerts

## Overview

### Available Operations

* [query_alert_log](#query_alert_log) - Query alert logs

## query_alert_log

Use when viewing or searching alert history (e.g. support triage or customer-facing alert log). Returns a paginated list; supports filtering by type, customer, subscription.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryAlertLog" method="post" path="/alerts/search" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.alerts.query_alert_log()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                   | Type                                                                        | Required                                                                    | Description                                                                 |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| `alert_status`                                                              | [Optional[models.AlertState]](../../models/alertstate.md)                   | :heavy_minus_sign:                                                          | N/A                                                                         |
| `alert_type`                                                                | [Optional[models.AlertType]](../../models/alerttype.md)                     | :heavy_minus_sign:                                                          | N/A                                                                         |
| `customer_id`                                                               | *Optional[str]*                                                             | :heavy_minus_sign:                                                          | N/A                                                                         |
| `end_time`                                                                  | [date](https://docs.python.org/3/library/datetime.html#date-objects)        | :heavy_minus_sign:                                                          | N/A                                                                         |
| `entity_id`                                                                 | *Optional[str]*                                                             | :heavy_minus_sign:                                                          | N/A                                                                         |
| `entity_type`                                                               | [Optional[models.AlertEntityType]](../../models/alertentitytype.md)         | :heavy_minus_sign:                                                          | N/A                                                                         |
| `expand`                                                                    | *Optional[str]*                                                             | :heavy_minus_sign:                                                          | N/A                                                                         |
| `filters`                                                                   | List[[models.FilterCondition](../../models/filtercondition.md)]             | :heavy_minus_sign:                                                          | filters allows complex filtering based on multiple fields                   |
| `limit`                                                                     | *Optional[int]*                                                             | :heavy_minus_sign:                                                          | N/A                                                                         |
| `offset`                                                                    | *Optional[int]*                                                             | :heavy_minus_sign:                                                          | N/A                                                                         |
| `order`                                                                     | [Optional[models.AlertLogFilterOrder]](../../models/alertlogfilterorder.md) | :heavy_minus_sign:                                                          | N/A                                                                         |
| `sort`                                                                      | List[[models.SortCondition](../../models/sortcondition.md)]                 | :heavy_minus_sign:                                                          | N/A                                                                         |
| `start_time`                                                                | [date](https://docs.python.org/3/library/datetime.html#date-objects)        | :heavy_minus_sign:                                                          | N/A                                                                         |
| `status`                                                                    | [Optional[models.Status]](../../models/status.md)                           | :heavy_minus_sign:                                                          | N/A                                                                         |
| `retries`                                                                   | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)            | :heavy_minus_sign:                                                          | Configuration to override the default retry behavior of the client.         |

### Response

**[models.ListAlertLogsResponse](../../models/listalertlogsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |