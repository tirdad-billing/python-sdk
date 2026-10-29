# AccountingPeriods

## Overview

### Available Operations

* [query_accounting_period](#query_accounting_period) - Query accounting periods

## query_accounting_period

Use when listing the monthly accounting periods revenue recognition posts to, by period status or a period start range. Returns a paginated list.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryAccountingPeriod" method="post" path="/accounting_periods/search" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.accounting_periods.query_accounting_period()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                   | Type                                                                                        | Required                                                                                    | Description                                                                                 |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `accounting_period_ids`                                                                     | List[*str*]                                                                                 | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `end_time`                                                                                  | [date](https://docs.python.org/3/library/datetime.html#date-objects)                        | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `expand`                                                                                    | *Optional[str]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `filters`                                                                                   | List[[models.FilterCondition](../../models/filtercondition.md)]                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `limit`                                                                                     | *Optional[int]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `offset`                                                                                    | *Optional[int]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `order`                                                                                     | [Optional[models.AccountingperiodFilterOrder]](../../models/accountingperiodfilterorder.md) | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `period_statuses`                                                                           | List[[models.AccountingPeriodStatus](../../models/accountingperiodstatus.md)]               | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `sort`                                                                                      | List[[models.SortCondition](../../models/sortcondition.md)]                                 | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `start_time`                                                                                | [date](https://docs.python.org/3/library/datetime.html#date-objects)                        | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `status`                                                                                    | [Optional[models.Status]](../../models/status.md)                                           | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `retries`                                                                                   | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                            | :heavy_minus_sign:                                                                          | Configuration to override the default retry behavior of the client.                         |

### Response

**[models.ListAccountingPeriodsResponse](../../models/listaccountingperiodsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |