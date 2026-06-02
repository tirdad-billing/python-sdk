# Addons

## Overview

### Available Operations

* [create_addon](#create_addon) - Create addon
* [get_addon_by_lookup_key](#get_addon_by_lookup_key) - Get addon by lookup key
* [query_addon](#query_addon) - Query addons
* [get_addon](#get_addon) - Get addon
* [update_addon](#update_addon) - Update addon
* [delete_addon](#delete_addon) - Delete addon

## create_addon

Use when defining an optional purchasable item (e.g. extra storage or support tier). Ideal for add-ons that customers can attach to a subscription.

### Example Usage

<!-- UsageSnippet language="python" operationID="createAddon" method="post" path="/addons" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.addons.create_addon(lookup_key="<value>", name="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `lookup_key`                                                        | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `name`                                                              | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `description`                                                       | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `metadata`                                                          | Dict[str, *Any*]                                                    | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.CreateAddonResponse](../../models/createaddonresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_addon_by_lookup_key

Use when resolving an addon by external id (e.g. from your product catalog). Ideal for integrations.

### Example Usage

<!-- UsageSnippet language="python" operationID="getAddonByLookupKey" method="get" path="/addons/lookup/{lookup_key}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.addons.get_addon_by_lookup_key(lookup_key="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `lookup_key`                                                        | *str*                                                               | :heavy_check_mark:                                                  | Addon Lookup Key                                                    |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.AddonResponse](../../models/addonresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## query_addon

Use when listing or searching addons (e.g. catalog or subscription builder). Returns a paginated list; supports filtering and sorting.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryAddon" method="post" path="/addons/search" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.addons.query_addon()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                             | Type                                                                  | Required                                                              | Description                                                           |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| `addon_ids`                                                           | List[*str*]                                                           | :heavy_minus_sign:                                                    | N/A                                                                   |
| `end_time`                                                            | [date](https://docs.python.org/3/library/datetime.html#date-objects)  | :heavy_minus_sign:                                                    | N/A                                                                   |
| `expand`                                                              | *Optional[str]*                                                       | :heavy_minus_sign:                                                    | N/A                                                                   |
| `filters`                                                             | List[[models.FilterCondition](../../models/filtercondition.md)]       | :heavy_minus_sign:                                                    | filters allows complex filtering based on multiple fields             |
| `limit`                                                               | *Optional[int]*                                                       | :heavy_minus_sign:                                                    | N/A                                                                   |
| `lookup_keys`                                                         | List[*str*]                                                           | :heavy_minus_sign:                                                    | N/A                                                                   |
| `offset`                                                              | *Optional[int]*                                                       | :heavy_minus_sign:                                                    | N/A                                                                   |
| `order`                                                               | [Optional[models.AddonFilterOrder]](../../models/addonfilterorder.md) | :heavy_minus_sign:                                                    | N/A                                                                   |
| `sort`                                                                | List[[models.SortCondition](../../models/sortcondition.md)]           | :heavy_minus_sign:                                                    | N/A                                                                   |
| `start_time`                                                          | [date](https://docs.python.org/3/library/datetime.html#date-objects)  | :heavy_minus_sign:                                                    | N/A                                                                   |
| `status`                                                              | [Optional[models.Status]](../../models/status.md)                     | :heavy_minus_sign:                                                    | N/A                                                                   |
| `retries`                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)      | :heavy_minus_sign:                                                    | Configuration to override the default retry behavior of the client.   |

### Response

**[models.ListAddonsResponse](../../models/listaddonsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_addon

Use when you need to load a single addon (e.g. for display or to attach to a subscription).

### Example Usage

<!-- UsageSnippet language="python" operationID="getAddon" method="get" path="/addons/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.addons.get_addon(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Addon ID                                                            |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.AddonResponse](../../models/addonresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## update_addon

Use when changing addon details (e.g. name, pricing, or metadata).

### Example Usage

<!-- UsageSnippet language="python" operationID="updateAddon" method="put" path="/addons/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.addons.update_addon(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Addon ID                                                            |
| `description`                                                       | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `metadata`                                                          | Dict[str, *Any*]                                                    | :heavy_minus_sign:                                                  | N/A                                                                 |
| `name`                                                              | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.AddonResponse](../../models/addonresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## delete_addon

Use when retiring an addon (e.g. end-of-life). Returns 200 with success message.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteAddon" method="delete" path="/addons/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.addons.delete_addon(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Addon ID                                                            |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.SuccessResponse](../../models/successresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |