# Features

## Overview

### Available Operations

* [create_feature](#create_feature) - Create feature
* [query_feature](#query_feature) - Query features
* [update_feature](#update_feature) - Update feature
* [delete_feature](#delete_feature) - Delete feature
* [clone_feature](#clone_feature) - Clone a feature

## create_feature

Use when defining a new feature or capability to gate or meter (e.g. feature flags or usage-based limits). Ideal for boolean or usage features.

### Example Usage

<!-- UsageSnippet language="python" operationID="createFeature" method="post" path="/features" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.features.create_feature(name="<value>", type_="metered", meter={
        "aggregation": {},
        "event_name": "api_request",
        "name": "API Usage Meter",
        "reset_usage": "NEVER",
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `name`                                                                    | *str*                                                                     | :heavy_check_mark:                                                        | N/A                                                                       |
| `type`                                                                    | [models.FeatureType](../../models/featuretype.md)                         | :heavy_check_mark:                                                        | N/A                                                                       |
| `alert_settings`                                                          | [Optional[models.AlertSettings]](../../models/alertsettings.md)           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `description`                                                             | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `group_id`                                                                | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | GroupID is the id of the group to add the feature to                      |
| `lookup_key`                                                              | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `metadata`                                                                | Dict[str, *str*]                                                          | :heavy_minus_sign:                                                        | N/A                                                                       |
| `meter`                                                                   | [Optional[models.CreateMeterRequest]](../../models/createmeterrequest.md) | :heavy_minus_sign:                                                        | N/A                                                                       |
| `meter_id`                                                                | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `reporting_unit`                                                          | [Optional[models.ReportingUnit]](../../models/reportingunit.md)           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `unit_plural`                                                             | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `unit_singular`                                                           | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `retries`                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)          | :heavy_minus_sign:                                                        | Configuration to override the default retry behavior of the client.       |

### Response

**[models.FeatureResponse](../../models/featureresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## query_feature

Use when listing or searching features (e.g. catalog or entitlement setup). Returns a paginated list; supports filtering and sorting.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryFeature" method="post" path="/features/search" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.features.query_feature()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `end_time`                                                                | [date](https://docs.python.org/3/library/datetime.html#date-objects)      | :heavy_minus_sign:                                                        | N/A                                                                       |
| `expand`                                                                  | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `feature_ids`                                                             | List[*str*]                                                               | :heavy_minus_sign:                                                        | Feature specific filters                                                  |
| `filters`                                                                 | List[[models.FilterCondition](../../models/filtercondition.md)]           | :heavy_minus_sign:                                                        | filters allows complex filtering based on multiple fields                 |
| `limit`                                                                   | *Optional[int]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `lookup_key`                                                              | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `lookup_keys`                                                             | List[*str*]                                                               | :heavy_minus_sign:                                                        | N/A                                                                       |
| `meter_ids`                                                               | List[*str*]                                                               | :heavy_minus_sign:                                                        | N/A                                                                       |
| `name_contains`                                                           | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `offset`                                                                  | *Optional[int]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `order`                                                                   | [Optional[models.FeatureFilterOrder]](../../models/featurefilterorder.md) | :heavy_minus_sign:                                                        | N/A                                                                       |
| `sort`                                                                    | List[[models.SortCondition](../../models/sortcondition.md)]               | :heavy_minus_sign:                                                        | N/A                                                                       |
| `start_time`                                                              | [date](https://docs.python.org/3/library/datetime.html#date-objects)      | :heavy_minus_sign:                                                        | N/A                                                                       |
| `status`                                                                  | [Optional[models.Status]](../../models/status.md)                         | :heavy_minus_sign:                                                        | N/A                                                                       |
| `retries`                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)          | :heavy_minus_sign:                                                        | Configuration to override the default retry behavior of the client.       |

### Response

**[models.ListFeaturesResponse](../../models/listfeaturesresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## update_feature

Use when changing feature definition (e.g. name, type, or meter). Request body contains the fields to update.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateFeature" method="put" path="/features/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.features.update_feature(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                            | Type                                                                                 | Required                                                                             | Description                                                                          |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| `id`                                                                                 | *str*                                                                                | :heavy_check_mark:                                                                   | Feature ID                                                                           |
| `alert_settings`                                                                     | [Optional[models.AlertSettings]](../../models/alertsettings.md)                      | :heavy_minus_sign:                                                                   | N/A                                                                                  |
| `description`                                                                        | *Optional[str]*                                                                      | :heavy_minus_sign:                                                                   | N/A                                                                                  |
| `filters`                                                                            | List[[models.MeterFilter](../../models/meterfilter.md)]                              | :heavy_minus_sign:                                                                   | N/A                                                                                  |
| `group_id`                                                                           | *Optional[str]*                                                                      | :heavy_minus_sign:                                                                   | GroupID is the id of the group to assign the feature to. Pass empty string to clear. |
| `metadata`                                                                           | Dict[str, *str*]                                                                     | :heavy_minus_sign:                                                                   | N/A                                                                                  |
| `name`                                                                               | *Optional[str]*                                                                      | :heavy_minus_sign:                                                                   | N/A                                                                                  |
| `reporting_unit`                                                                     | [Optional[models.ReportingUnit]](../../models/reportingunit.md)                      | :heavy_minus_sign:                                                                   | N/A                                                                                  |
| `unit_plural`                                                                        | *Optional[str]*                                                                      | :heavy_minus_sign:                                                                   | N/A                                                                                  |
| `unit_singular`                                                                      | *Optional[str]*                                                                      | :heavy_minus_sign:                                                                   | N/A                                                                                  |
| `retries`                                                                            | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                     | :heavy_minus_sign:                                                                   | Configuration to override the default retry behavior of the client.                  |

### Response

**[models.FeatureResponse](../../models/featureresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## delete_feature

Use when retiring a feature (e.g. deprecated capability). Returns 200 with success message.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteFeature" method="delete" path="/features/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.features.delete_feature(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Feature ID                                                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.SuccessResponse](../../models/successresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## clone_feature

Clone an existing feature

### Example Usage

<!-- UsageSnippet language="python" operationID="cloneFeature" method="post" path="/features/{id}/clone" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.features.clone_feature(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                             | Type                                                                  | Required                                                              | Description                                                           |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| `id`                                                                  | *str*                                                                 | :heavy_check_mark:                                                    | Source Feature ID                                                     |
| `description`                                                         | *Optional[str]*                                                       | :heavy_minus_sign:                                                    | Description overrides the source feature's description when provided  |
| `lookup_key`                                                          | *Optional[str]*                                                       | :heavy_minus_sign:                                                    | LookupKey is required and must be unique across published features    |
| `metadata`                                                            | Dict[str, *str*]                                                      | :heavy_minus_sign:                                                    | N/A                                                                   |
| `name`                                                                | *Optional[str]*                                                       | :heavy_minus_sign:                                                    | Name is required and must be different from the source feature's name |
| `retries`                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)      | :heavy_minus_sign:                                                    | Configuration to override the default retry behavior of the client.   |

### Response

**[models.FeatureResponse](../../models/featureresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404, 409                    | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |