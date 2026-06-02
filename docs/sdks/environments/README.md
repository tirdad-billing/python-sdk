# Environments

## Overview

### Available Operations

* [clone_environment](#clone_environment) - Clone an environment

## clone_environment

Clone all published features and plans from the source environment into a target environment. If target_environment_id is provided, entities are cloned into that existing environment. Otherwise a new environment is created from name and type first.

### Example Usage

<!-- UsageSnippet language="python" operationID="cloneEnvironment" method="post" path="/environments/{id}/clone" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.environments.clone_environment(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                              | Type                                                                                                                                                                   | Required                                                                                                                                                               | Description                                                                                                                                                            |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                                                                                   | *str*                                                                                                                                                                  | :heavy_check_mark:                                                                                                                                                     | Source Environment ID                                                                                                                                                  |
| `name`                                                                                                                                                                 | *Optional[str]*                                                                                                                                                        | :heavy_minus_sign:                                                                                                                                                     | Name of the new environment (required when target_environment_id is not provided)                                                                                      |
| `target_environment_id`                                                                                                                                                | *Optional[str]*                                                                                                                                                        | :heavy_minus_sign:                                                                                                                                                     | TargetEnvironmentID is the ID of an existing environment to clone into (optional).<br/>When provided, Name and Type are ignored. When omitted, Name and Type are required. |
| `type`                                                                                                                                                                 | [Optional[models.EnvironmentType]](../../models/environmenttype.md)                                                                                                    | :heavy_minus_sign:                                                                                                                                                     | N/A                                                                                                                                                                    |
| `retries`                                                                                                                                                              | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                       | :heavy_minus_sign:                                                                                                                                                     | Configuration to override the default retry behavior of the client.                                                                                                    |

### Response

**[models.ModelsTemporalWorkflowResult](../../models/modelstemporalworkflowresult.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |