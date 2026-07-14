# AlertSettings

## Overview

### Available Operations

* [create_alert_settings](#create_alert_settings) - Create alert settings
* [query_alert_settings](#query_alert_settings) - Query alert settings
* [get_alert_settings](#get_alert_settings) - Get alert settings
* [update_alert_settings](#update_alert_settings) - Update alert settings
* [delete_alert_settings](#delete_alert_settings) - Delete alert settings

## create_alert_settings

Configure a subscription, line item, or group spend alert.

### Example Usage

<!-- UsageSnippet language="python" operationID="createAlertSettings" method="post" path="/alerts/setting" -->
```python
from tirdad_sdk import Tirdad, models


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.alert_settings.create_alert_settings(config=models.AlertSettings(), entity_id="<id>", entity_type="feature")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                              | Type                                                                                                                                                                                   | Required                                                                                                                                                                               | Description                                                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `config`                                                                                                                                                                               | [models.AlertSettings](../../models/alertsettings.md)                                                                                                                                  | :heavy_check_mark:                                                                                                                                                                     | N/A                                                                                                                                                                                    |
| `entity_id`                                                                                                                                                                            | *str*                                                                                                                                                                                  | :heavy_check_mark:                                                                                                                                                                     | entity_id is the id of the monitored entity: subscription id, subscription_line_item id, or<br/>group id, matching entity_type.                                                        |
| `entity_type`                                                                                                                                                                          | [models.AlertEntityType](../../models/alertentitytype.md)                                                                                                                              | :heavy_check_mark:                                                                                                                                                                     | N/A                                                                                                                                                                                    |
| `parent_entity_id`                                                                                                                                                                     | *Optional[str]*                                                                                                                                                                        | :heavy_minus_sign:                                                                                                                                                                     | parent_entity_id is the subscription id that owns a line-item or group alert. Required when<br/>entity_type is "subscription_line_item" or "group"; omitted for subscription-level alerts. |
| `parent_entity_type`                                                                                                                                                                   | [Optional[models.AlertEntityType]](../../models/alertentitytype.md)                                                                                                                    | :heavy_minus_sign:                                                                                                                                                                     | N/A                                                                                                                                                                                    |
| `retries`                                                                                                                                                                              | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                     | Configuration to override the default retry behavior of the client.                                                                                                                    |

### Response

**[models.AlertSettingsResponse](../../models/alertsettingsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## query_alert_settings

List or search alert settings. Returns a paginated list.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryAlertSettings" method="post" path="/alerts/setting/search" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.alert_settings.query_alert_settings()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                             | Type                                                                                  | Required                                                                              | Description                                                                           |
| ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `enabled`                                                                             | *Optional[bool]*                                                                      | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `end_time`                                                                            | [date](https://docs.python.org/3/library/datetime.html#date-objects)                  | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `entity_id`                                                                           | *Optional[str]*                                                                       | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `entity_ids`                                                                          | List[*str*]                                                                           | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `entity_type`                                                                         | [Optional[models.AlertEntityType]](../../models/alertentitytype.md)                   | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `expand`                                                                              | *Optional[str]*                                                                       | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `filters`                                                                             | List[[models.FilterCondition](../../models/filtercondition.md)]                       | :heavy_minus_sign:                                                                    | filters allows complex filtering based on multiple fields                             |
| `limit`                                                                               | *Optional[int]*                                                                       | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `offset`                                                                              | *Optional[int]*                                                                       | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `order`                                                                               | [Optional[models.AlertSettingsFilterOrder]](../../models/alertsettingsfilterorder.md) | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `parent_entity_id`                                                                    | *Optional[str]*                                                                       | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `parent_entity_ids`                                                                   | List[*str*]                                                                           | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `parent_entity_type`                                                                  | [Optional[models.AlertEntityType]](../../models/alertentitytype.md)                   | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `sort`                                                                                | List[[models.SortCondition](../../models/sortcondition.md)]                           | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `start_time`                                                                          | [date](https://docs.python.org/3/library/datetime.html#date-objects)                  | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `status`                                                                              | [Optional[models.Status]](../../models/status.md)                                     | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `retries`                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                      | :heavy_minus_sign:                                                                    | Configuration to override the default retry behavior of the client.                   |

### Response

**[models.ListAlertSettingsResponse](../../models/listalertsettingsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_alert_settings

Fetch a single alert setting by id.

### Example Usage

<!-- UsageSnippet language="python" operationID="getAlertSettings" method="get" path="/alerts/setting/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.alert_settings.get_alert_settings(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Alert Settings ID                                                   |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.AlertSettingsResponse](../../models/alertsettingsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## update_alert_settings

Patch an alert setting's config; omitted fields keep their stored value.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateAlertSettings" method="put" path="/alerts/setting/{id}" -->
```python
from tirdad_sdk import Tirdad, models


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.alert_settings.update_alert_settings(id="<id>", config=models.AlertSettings())

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Alert Settings ID                                                   |
| `config`                                                            | [models.AlertSettings](../../models/alertsettings.md)               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.AlertSettingsResponse](../../models/alertsettingsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## delete_alert_settings

Soft delete an alert setting.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteAlertSettings" method="delete" path="/alerts/setting/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    tirdad.alert_settings.delete_alert_settings(id="<id>")

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Alert Settings ID                                                   |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |