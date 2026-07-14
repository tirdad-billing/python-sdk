# Integrations

## Overview

### Available Operations

* [get_integration_config](#get_integration_config) - Get integration configurations
* [link_integration_mapping](#link_integration_mapping) - Link integration mapping
* [delink_integration_mapping](#delink_integration_mapping) - Delink integration mapping
* [get_entity_integration_mappings](#get_entity_integration_mappings) - Get entity integration mappings

## get_integration_config

Returns the base capabilities and current sync configuration for all connected providers.

### Example Usage

<!-- UsageSnippet language="python" operationID="getIntegrationConfig" method="get" path="/integrations/config" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.integrations.get_integration_config()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.IntegrationConfigResponse](../../models/integrationconfigresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## link_integration_mapping

Link a Tirdad entity to provider entity with provider-specific side effects.

### Example Usage

<!-- UsageSnippet language="python" operationID="linkIntegrationMapping" method="post" path="/integrations/link" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.integrations.link_integration_mapping(entity_id="<id>", entity_type="price", provider_entity_id="<id>", provider_type="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                             | Type                                                                  | Required                                                              | Description                                                           |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| `entity_id`                                                           | *str*                                                                 | :heavy_check_mark:                                                    | N/A                                                                   |
| `entity_type`                                                         | [models.IntegrationEntityType](../../models/integrationentitytype.md) | :heavy_check_mark:                                                    | N/A                                                                   |
| `provider_entity_id`                                                  | *str*                                                                 | :heavy_check_mark:                                                    | N/A                                                                   |
| `provider_type`                                                       | *str*                                                                 | :heavy_check_mark:                                                    | N/A                                                                   |
| `metadata`                                                            | Dict[str, *Any*]                                                      | :heavy_minus_sign:                                                    | N/A                                                                   |
| `retries`                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)      | :heavy_minus_sign:                                                    | Configuration to override the default retry behavior of the client.   |

### Response

**[models.LinkIntegrationMappingResponse](../../models/linkintegrationmappingresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## delink_integration_mapping

Soft-delete (archive) the mapping between a Tirdad entity and a provider entity.

### Example Usage

<!-- UsageSnippet language="python" operationID="delinkIntegrationMapping" method="delete" path="/integrations/link" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.integrations.delink_integration_mapping(entity_id="<id>", entity_type="item_price", provider_type="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                             | Type                                                                  | Required                                                              | Description                                                           |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| `entity_id`                                                           | *str*                                                                 | :heavy_check_mark:                                                    | N/A                                                                   |
| `entity_type`                                                         | [models.IntegrationEntityType](../../models/integrationentitytype.md) | :heavy_check_mark:                                                    | N/A                                                                   |
| `provider_type`                                                       | *str*                                                                 | :heavy_check_mark:                                                    | N/A                                                                   |
| `retries`                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)      | :heavy_minus_sign:                                                    | Configuration to override the default retry behavior of the client.   |

### Response

**[models.SuccessResponse](../../models/successresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_entity_integration_mappings

Get integration mappings for a specific entity by entity type and entity ID.

### Example Usage

<!-- UsageSnippet language="python" operationID="getEntityIntegrationMappings" method="get" path="/integrations/mappings" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.integrations.get_entity_integration_mappings(entity_type="<value>", entity_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                 | Type                                                                                                      | Required                                                                                                  | Description                                                                                               |
| --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| `entity_type`                                                                                             | *str*                                                                                                     | :heavy_check_mark:                                                                                        | Entity type (customer, plan, invoice, subscription, payment, credit_note, addon, item, item_price, price) |
| `entity_id`                                                                                               | *str*                                                                                                     | :heavy_check_mark:                                                                                        | Entity ID                                                                                                 |
| `retries`                                                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                          | :heavy_minus_sign:                                                                                        | Configuration to override the default retry behavior of the client.                                       |

### Response

**[models.ListEntityIntegrationMappingsResponse](../../models/listentityintegrationmappingsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |