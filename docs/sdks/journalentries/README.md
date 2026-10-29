# JournalEntries

## Overview

### Available Operations

* [query_journal_entry](#query_journal_entry) - Query journal entries
* [get_journal_entry](#get_journal_entry) - Get journal entry

## query_journal_entry

Use when listing journal entries by period, event type, account, customer, contract, performance obligation or source. Returns a paginated list with lines.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryJournalEntry" method="post" path="/journal_entries/search" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.journal_entries.query_journal_entry()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `accounting_period_ids`                                                   | List[*str*]                                                               | :heavy_minus_sign:                                                        | N/A                                                                       |
| `accounts`                                                                | List[[models.LedgerAccountKey](../../models/ledgeraccountkey.md)]         | :heavy_minus_sign:                                                        | N/A                                                                       |
| `contract_ids`                                                            | List[*str*]                                                               | :heavy_minus_sign:                                                        | N/A                                                                       |
| `customer_ids`                                                            | List[*str*]                                                               | :heavy_minus_sign:                                                        | N/A                                                                       |
| `end_time`                                                                | [date](https://docs.python.org/3/library/datetime.html#date-objects)      | :heavy_minus_sign:                                                        | N/A                                                                       |
| `event_types`                                                             | List[[models.JournalEventType](../../models/journaleventtype.md)]         | :heavy_minus_sign:                                                        | N/A                                                                       |
| `expand`                                                                  | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `filters`                                                                 | List[[models.FilterCondition](../../models/filtercondition.md)]           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `journal_entry_ids`                                                       | List[*str*]                                                               | :heavy_minus_sign:                                                        | N/A                                                                       |
| `limit`                                                                   | *Optional[int]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `offset`                                                                  | *Optional[int]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `order`                                                                   | [Optional[models.JournalFilterOrder]](../../models/journalfilterorder.md) | :heavy_minus_sign:                                                        | N/A                                                                       |
| `pob_ids`                                                                 | List[*str*]                                                               | :heavy_minus_sign:                                                        | N/A                                                                       |
| `sort`                                                                    | List[[models.SortCondition](../../models/sortcondition.md)]               | :heavy_minus_sign:                                                        | N/A                                                                       |
| `source_entity_ids`                                                       | List[*str*]                                                               | :heavy_minus_sign:                                                        | N/A                                                                       |
| `source_entity_type`                                                      | [Optional[models.RevRecEntityType]](../../models/revrecentitytype.md)     | :heavy_minus_sign:                                                        | N/A                                                                       |
| `start_time`                                                              | [date](https://docs.python.org/3/library/datetime.html#date-objects)      | :heavy_minus_sign:                                                        | N/A                                                                       |
| `status`                                                                  | [Optional[models.Status]](../../models/status.md)                         | :heavy_minus_sign:                                                        | N/A                                                                       |
| `retries`                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)          | :heavy_minus_sign:                                                        | Configuration to override the default retry behavior of the client.       |

### Response

**[models.ListJournalEntriesResponse](../../models/listjournalentriesresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_journal_entry

Use when you need one revenue recognition journal entry with its debit and credit lines. The journal is derived from billing and recognition and is read-only.

### Example Usage

<!-- UsageSnippet language="python" operationID="getJournalEntry" method="get" path="/journal_entries/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.journal_entries.get_journal_entry(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Journal entry ID                                                    |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.JournalEntryResponse](../../models/journalentryresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |