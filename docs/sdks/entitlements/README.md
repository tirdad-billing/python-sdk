# Entitlements

## Overview

### Available Operations

* [get_addon_entitlements](#get_addon_entitlements) - Get addon entitlements
* [create_entitlement](#create_entitlement) - Create entitlement
* [create_entitlements_bulk](#create_entitlements_bulk) - Create entitlements in bulk
* [query_entitlement](#query_entitlement) - Query entitlements
* [get_entitlement](#get_entitlement) - Get entitlement
* [update_entitlement](#update_entitlement) - Update entitlement
* [delete_entitlement](#delete_entitlement) - Delete entitlement
* [get_plan_entitlements](#get_plan_entitlements) - Get plan entitlements

## get_addon_entitlements

Use when checking what features or limits an addon grants (e.g. for display or entitlement logic).

### Example Usage

<!-- UsageSnippet language="python" operationID="getAddonEntitlements" method="get" path="/addons/{id}/entitlements" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.entitlements.get_addon_entitlements(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Addon ID                                                            |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ListEntitlementsResponse](../../models/listentitlementsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## create_entitlement

Use when attaching a feature (and its limit) to a plan or addon (e.g. "10 seats" or "1000 API calls"). Defines what the plan/addon includes.

### Example Usage

<!-- UsageSnippet language="python" operationID="createEntitlement" method="post" path="/entitlements" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.entitlements.create_entitlement(feature_id="<id>", feature_type="metered")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                   | Type                                                                                        | Required                                                                                    | Description                                                                                 |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `feature_id`                                                                                | *str*                                                                                       | :heavy_check_mark:                                                                          | N/A                                                                                         |
| `feature_type`                                                                              | [models.FeatureType](../../models/featuretype.md)                                           | :heavy_check_mark:                                                                          | N/A                                                                                         |
| `config_value`                                                                              | Dict[str, *Any*]                                                                            | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `end_date`                                                                                  | [date](https://docs.python.org/3/library/datetime.html#date-objects)                        | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `entity_id`                                                                                 | *Optional[str]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `entity_type`                                                                               | [Optional[models.EntitlementEntityType]](../../models/entitlemententitytype.md)             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `is_enabled`                                                                                | *Optional[bool]*                                                                            | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `is_soft_limit`                                                                             | *Optional[bool]*                                                                            | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `parent_entitlement_id`                                                                     | *Optional[str]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `plan_id`                                                                                   | *Optional[str]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `start_date`                                                                                | [date](https://docs.python.org/3/library/datetime.html#date-objects)                        | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `static_value`                                                                              | *Optional[str]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `usage_limit`                                                                               | *Optional[int]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `usage_reset_period`                                                                        | [Optional[models.EntitlementUsageResetPeriod]](../../models/entitlementusageresetperiod.md) | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `retries`                                                                                   | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                            | :heavy_minus_sign:                                                                          | Configuration to override the default retry behavior of the client.                         |

### Response

**[models.EntitlementResponse](../../models/entitlementresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## create_entitlements_bulk

Use when attaching many features to a plan or addon at once (e.g. initial plan setup or import). Bulk version of create entitlement.

### Example Usage

<!-- UsageSnippet language="python" operationID="createEntitlementsBulk" method="post" path="/entitlements/bulk" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.entitlements.create_entitlements_bulk(items=[
        {
            "feature_id": "<id>",
            "feature_type": "config",
        },
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                         | Type                                                                              | Required                                                                          | Description                                                                       |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `items`                                                                           | List[[models.CreateEntitlementRequest](../../models/createentitlementrequest.md)] | :heavy_check_mark:                                                                | N/A                                                                               |
| `retries`                                                                         | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                  | :heavy_minus_sign:                                                                | Configuration to override the default retry behavior of the client.               |

### Response

**[models.CreateBulkEntitlementResponse](../../models/createbulkentitlementresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## query_entitlement

Use when listing or searching entitlements (e.g. plan editor or audit). Returns a paginated list; supports filtering by plan, addon, feature.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryEntitlement" method="post" path="/entitlements/search" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.entitlements.query_entitlement()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                         | Type                                                                              | Required                                                                          | Description                                                                       |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `end_time`                                                                        | [date](https://docs.python.org/3/library/datetime.html#date-objects)              | :heavy_minus_sign:                                                                | N/A                                                                               |
| `entity_ids`                                                                      | List[*str*]                                                                       | :heavy_minus_sign:                                                                | N/A                                                                               |
| `entity_type`                                                                     | [Optional[models.EntitlementEntityType]](../../models/entitlemententitytype.md)   | :heavy_minus_sign:                                                                | N/A                                                                               |
| `expand`                                                                          | *Optional[str]*                                                                   | :heavy_minus_sign:                                                                | N/A                                                                               |
| `feature_ids`                                                                     | List[*str*]                                                                       | :heavy_minus_sign:                                                                | N/A                                                                               |
| `feature_type`                                                                    | [Optional[models.FeatureType]](../../models/featuretype.md)                       | :heavy_minus_sign:                                                                | N/A                                                                               |
| `filters`                                                                         | List[[models.FilterCondition](../../models/filtercondition.md)]                   | :heavy_minus_sign:                                                                | Specific filters for entitlements                                                 |
| `is_enabled`                                                                      | *Optional[bool]*                                                                  | :heavy_minus_sign:                                                                | N/A                                                                               |
| `limit`                                                                           | *Optional[int]*                                                                   | :heavy_minus_sign:                                                                | N/A                                                                               |
| `offset`                                                                          | *Optional[int]*                                                                   | :heavy_minus_sign:                                                                | N/A                                                                               |
| `order`                                                                           | [Optional[models.EntitlementFilterOrder]](../../models/entitlementfilterorder.md) | :heavy_minus_sign:                                                                | N/A                                                                               |
| `plan_ids`                                                                        | List[*str*]                                                                       | :heavy_minus_sign:                                                                | N/A                                                                               |
| `sort`                                                                            | List[[models.SortCondition](../../models/sortcondition.md)]                       | :heavy_minus_sign:                                                                | N/A                                                                               |
| `start_time`                                                                      | [date](https://docs.python.org/3/library/datetime.html#date-objects)              | :heavy_minus_sign:                                                                | N/A                                                                               |
| `status`                                                                          | [Optional[models.Status]](../../models/status.md)                                 | :heavy_minus_sign:                                                                | N/A                                                                               |
| `retries`                                                                         | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                  | :heavy_minus_sign:                                                                | Configuration to override the default retry behavior of the client.               |

### Response

**[models.ListEntitlementsResponse](../../models/listentitlementsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_entitlement

Use when you need to load a single entitlement (e.g. to display or edit a feature limit).

### Example Usage

<!-- UsageSnippet language="python" operationID="getEntitlement" method="get" path="/entitlements/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.entitlements.get_entitlement(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Entitlement ID                                                      |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.EntitlementResponse](../../models/entitlementresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## update_entitlement

Use when changing an entitlement (e.g. increasing or decreasing a limit). Request body contains the fields to update.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateEntitlement" method="put" path="/entitlements/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.entitlements.update_entitlement(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                   | Type                                                                                        | Required                                                                                    | Description                                                                                 |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `id`                                                                                        | *str*                                                                                       | :heavy_check_mark:                                                                          | Entitlement ID                                                                              |
| `config_value`                                                                              | Dict[str, *Any*]                                                                            | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `is_enabled`                                                                                | *Optional[bool]*                                                                            | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `is_soft_limit`                                                                             | *Optional[bool]*                                                                            | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `static_value`                                                                              | *Optional[str]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `usage_limit`                                                                               | *Optional[int]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `usage_reset_period`                                                                        | [Optional[models.EntitlementUsageResetPeriod]](../../models/entitlementusageresetperiod.md) | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `retries`                                                                                   | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                            | :heavy_minus_sign:                                                                          | Configuration to override the default retry behavior of the client.                         |

### Response

**[models.EntitlementResponse](../../models/entitlementresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## delete_entitlement

Use when removing a feature from a plan or addon (e.g. deprecating a capability). Returns 200 with success message.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteEntitlement" method="delete" path="/entitlements/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.entitlements.delete_entitlement(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Entitlement ID                                                      |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.SuccessResponse](../../models/successresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_plan_entitlements

Use when checking what a plan includes (e.g. feature list or limits for display or gating).

### Example Usage

<!-- UsageSnippet language="python" operationID="getPlanEntitlements" method="get" path="/plans/{id}/entitlements" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.entitlements.get_plan_entitlements(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Plan ID                                                             |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ListEntitlementsResponse](../../models/listentitlementsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |