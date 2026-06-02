# Groups

## Overview

### Available Operations

* [create_group](#create_group) - Create group
* [query_group](#query_group) - Query groups
* [get_group](#get_group) - Get group
* [delete_group](#delete_group) - Delete group

## create_group

Use when organizing entities into a group (e.g. for filtering prices or plans by product line or region).

### Example Usage

<!-- UsageSnippet language="python" operationID="createGroup" method="post" path="/groups" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.groups.create_group(entity_type="<value>", lookup_key="<value>", name="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `entity_type`                                                       | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `lookup_key`                                                        | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `name`                                                              | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.GroupResponse](../../models/groupresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## query_group

Use when listing or searching groups (e.g. admin catalog). Returns a paginated list; supports filtering and sorting.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryGroup" method="post" path="/groups/search" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.groups.query_group()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                             | Type                                                                  | Required                                                              | Description                                                           |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| `end_time`                                                            | [date](https://docs.python.org/3/library/datetime.html#date-objects)  | :heavy_minus_sign:                                                    | N/A                                                                   |
| `entity_type`                                                         | *Optional[str]*                                                       | :heavy_minus_sign:                                                    | N/A                                                                   |
| `expand`                                                              | *Optional[str]*                                                       | :heavy_minus_sign:                                                    | N/A                                                                   |
| `filters`                                                             | List[[models.FilterCondition](../../models/filtercondition.md)]       | :heavy_minus_sign:                                                    | filters allows complex filtering based on multiple fields             |
| `group_ids`                                                           | List[*str*]                                                           | :heavy_minus_sign:                                                    | Group specific filters                                                |
| `limit`                                                               | *Optional[int]*                                                       | :heavy_minus_sign:                                                    | N/A                                                                   |
| `lookup_key`                                                          | *Optional[str]*                                                       | :heavy_minus_sign:                                                    | N/A                                                                   |
| `name`                                                                | *Optional[str]*                                                       | :heavy_minus_sign:                                                    | N/A                                                                   |
| `offset`                                                              | *Optional[int]*                                                       | :heavy_minus_sign:                                                    | N/A                                                                   |
| `order`                                                               | [Optional[models.GroupFilterOrder]](../../models/groupfilterorder.md) | :heavy_minus_sign:                                                    | N/A                                                                   |
| `sort`                                                                | List[[models.SortCondition](../../models/sortcondition.md)]           | :heavy_minus_sign:                                                    | N/A                                                                   |
| `start_time`                                                          | [date](https://docs.python.org/3/library/datetime.html#date-objects)  | :heavy_minus_sign:                                                    | N/A                                                                   |
| `status`                                                              | [Optional[models.Status]](../../models/status.md)                     | :heavy_minus_sign:                                                    | N/A                                                                   |
| `retries`                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)      | :heavy_minus_sign:                                                    | Configuration to override the default retry behavior of the client.   |

### Response

**[models.ListGroupsResponse](../../models/listgroupsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_group

Use when you need to load a single group (e.g. for display or to assign entities).

### Example Usage

<!-- UsageSnippet language="python" operationID="getGroup" method="get" path="/groups/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.groups.get_group(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Group ID                                                            |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.GroupResponse](../../models/groupresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## delete_group

Use when removing a group and clearing its entity associations (e.g. retiring a product line). Returns 204 or 200 on success.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteGroup" method="delete" path="/groups/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    tirdad.groups.delete_group(id="<id>")

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Group ID                                                            |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |