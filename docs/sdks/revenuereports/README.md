# RevenueReports

## Overview

### Available Operations

* [get_revenue_rollforward](#get_revenue_rollforward) - Get revenue rollforward
* [get_revenue_waterfall](#get_revenue_waterfall) - Get revenue waterfall

## get_revenue_rollforward

Use when explaining how deferred revenue, unbilled receivable or another ledger account moved in ended months: opening balance, movements by category (invoiced, earned, adjustments, payments, refunds) and closing balance, optionally per customer, contract or performance obligation.

### Example Usage

<!-- UsageSnippet language="python" operationID="getRevenueRollforward" method="post" path="/revenue_reports/rollforward" -->
```python
from tirdad_sdk import Tirdad
from tirdad_sdk.utils import parse_datetime


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.revenue_reports.get_revenue_rollforward(currency="Moldovan Leu", period_start=parse_datetime("2025-06-02T22:16:06.570Z"))

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `currency`                                                                | *str*                                                                     | :heavy_check_mark:                                                        | N/A                                                                       |
| `period_start`                                                            | [date](https://docs.python.org/3/library/datetime.html#date-objects)      | :heavy_check_mark:                                                        | YYYY-MM                                                                   |
| `accounts`                                                                | List[[models.LedgerAccountKey](../../models/ledgeraccountkey.md)]         | :heavy_minus_sign:                                                        | defaults to [deferred_revenue]                                            |
| `contract_ids`                                                            | List[*str*]                                                               | :heavy_minus_sign:                                                        | N/A                                                                       |
| `customer_ids`                                                            | List[*str*]                                                               | :heavy_minus_sign:                                                        | N/A                                                                       |
| `group_by`                                                                | List[[models.RevenueReportGroupBy](../../models/revenuereportgroupby.md)] | :heavy_minus_sign:                                                        | N/A                                                                       |
| `limit`                                                                   | *Optional[int]*                                                           | :heavy_minus_sign:                                                        | item rows per page; totals are never paged                                |
| `offset`                                                                  | *Optional[int]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `period_end`                                                              | [date](https://docs.python.org/3/library/datetime.html#date-objects)      | :heavy_minus_sign:                                                        | YYYY-MM, an ended month; defaults to period_start                         |
| `pob_ids`                                                                 | List[*str*]                                                               | :heavy_minus_sign:                                                        | N/A                                                                       |
| `posted_by`                                                               | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | only entries posted at or before it: the books as they were then          |
| `retries`                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)          | :heavy_minus_sign:                                                        | Configuration to override the default retry behavior of the client.       |

### Response

**[models.RollforwardResponse](../../models/rollforwardresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_revenue_waterfall

Use when showing revenue per customer, contract or performance obligation and month: actual (posted), pending (earned, not yet posted) and scheduled (invoiced, not yet earned), with optional month-end deferred and unbilled balances. Covers at most 36 months.

### Example Usage

<!-- UsageSnippet language="python" operationID="getRevenueWaterfall" method="post" path="/revenue_reports/waterfall" -->
```python
from tirdad_sdk import Tirdad
from tirdad_sdk.utils import parse_datetime


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.revenue_reports.get_revenue_waterfall(currency="Dalasi", period_end=parse_datetime("2025-08-28T20:02:24.445Z"), period_start=parse_datetime("2024-03-13T15:39:09.277Z"))

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                     | Type                                                                          | Required                                                                      | Description                                                                   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `currency`                                                                    | *str*                                                                         | :heavy_check_mark:                                                            | N/A                                                                           |
| `period_end`                                                                  | [date](https://docs.python.org/3/library/datetime.html#date-objects)          | :heavy_check_mark:                                                            | YYYY-MM, at most 36 months from period_start                                  |
| `period_start`                                                                | [date](https://docs.python.org/3/library/datetime.html#date-objects)          | :heavy_check_mark:                                                            | YYYY-MM                                                                       |
| `as_of`                                                                       | *Optional[str]*                                                               | :heavy_minus_sign:                                                            | report date: pending and scheduled split here; defaults to now                |
| `contract_ids`                                                                | List[*str*]                                                                   | :heavy_minus_sign:                                                            | N/A                                                                           |
| `customer_ids`                                                                | List[*str*]                                                                   | :heavy_minus_sign:                                                            | N/A                                                                           |
| `details`                                                                     | *Optional[bool]*                                                              | :heavy_minus_sign:                                                            | month-end deferred and unbilled balances                                      |
| `group_by`                                                                    | [Optional[models.RevenueReportGroupBy]](../../models/revenuereportgroupby.md) | :heavy_minus_sign:                                                            | N/A                                                                           |
| `limit`                                                                       | *Optional[int]*                                                               | :heavy_minus_sign:                                                            | rows per page; totals are never paged                                         |
| `offset`                                                                      | *Optional[int]*                                                               | :heavy_minus_sign:                                                            | N/A                                                                           |
| `pob_ids`                                                                     | List[*str*]                                                                   | :heavy_minus_sign:                                                            | N/A                                                                           |
| `retries`                                                                     | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)              | :heavy_minus_sign:                                                            | Configuration to override the default retry behavior of the client.           |

### Response

**[models.WaterfallResponse](../../models/waterfallresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |