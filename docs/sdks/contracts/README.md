# Contracts

## Overview

### Available Operations

* [query_contract](#query_contract) - Query contracts
* [get_contract](#get_contract) - Get contract

## query_contract

Use when searching revenue recognition contracts by customer, subscription or contract status. Returns a paginated list.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryContract" method="post" path="/contracts/search" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.contracts.query_contract()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                   | Type                                                                        | Required                                                                    | Description                                                                 |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| `contract_ids`                                                              | List[*str*]                                                                 | :heavy_minus_sign:                                                          | N/A                                                                         |
| `contract_statuses`                                                         | List[[models.ContractStatus](../../models/contractstatus.md)]               | :heavy_minus_sign:                                                          | N/A                                                                         |
| `customer_ids`                                                              | List[*str*]                                                                 | :heavy_minus_sign:                                                          | N/A                                                                         |
| `end_time`                                                                  | [date](https://docs.python.org/3/library/datetime.html#date-objects)        | :heavy_minus_sign:                                                          | N/A                                                                         |
| `ended_at_gte`                                                              | [date](https://docs.python.org/3/library/datetime.html#date-objects)        | :heavy_minus_sign:                                                          | N/A                                                                         |
| `expand`                                                                    | *Optional[str]*                                                             | :heavy_minus_sign:                                                          | N/A                                                                         |
| `filters`                                                                   | List[[models.FilterCondition](../../models/filtercondition.md)]             | :heavy_minus_sign:                                                          | N/A                                                                         |
| `limit`                                                                     | *Optional[int]*                                                             | :heavy_minus_sign:                                                          | N/A                                                                         |
| `offset`                                                                    | *Optional[int]*                                                             | :heavy_minus_sign:                                                          | N/A                                                                         |
| `order`                                                                     | [Optional[models.ContractFilterOrder]](../../models/contractfilterorder.md) | :heavy_minus_sign:                                                          | N/A                                                                         |
| `sort`                                                                      | List[[models.SortCondition](../../models/sortcondition.md)]                 | :heavy_minus_sign:                                                          | N/A                                                                         |
| `start_time`                                                                | [date](https://docs.python.org/3/library/datetime.html#date-objects)        | :heavy_minus_sign:                                                          | N/A                                                                         |
| `status`                                                                    | [Optional[models.Status]](../../models/status.md)                           | :heavy_minus_sign:                                                          | N/A                                                                         |
| `subscription_ids`                                                          | List[*str*]                                                                 | :heavy_minus_sign:                                                          | N/A                                                                         |
| `retries`                                                                   | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)            | :heavy_minus_sign:                                                          | Configuration to override the default retry behavior of the client.         |

### Response

**[models.ListContractsResponse](../../models/listcontractsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_contract

Use when you need to load a single revenue recognition contract with the subscriptions it covers. Contracts are derived from subscriptions and are read-only.

### Example Usage

<!-- UsageSnippet language="python" operationID="getContract" method="get" path="/contracts/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.contracts.get_contract(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Contract ID                                                         |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ContractResponse](../../models/contractresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |