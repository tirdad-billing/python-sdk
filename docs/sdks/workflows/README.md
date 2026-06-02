# Workflows

## Overview

### Available Operations

* [query_workflow](#query_workflow) - Query workflows

## query_workflow

Use when listing or auditing workflow runs (e.g. ops dashboard or debugging). Returns a paginated list; supports filtering by workflow type and status.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryWorkflow" method="post" path="/workflows/search" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.workflows.query_workflow()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                     | Type                                                                                          | Required                                                                                      | Description                                                                                   |
| --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| `end_time`                                                                                    | [date](https://docs.python.org/3/library/datetime.html#date-objects)                          | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `entity`                                                                                      | *Optional[str]*                                                                               | :heavy_minus_sign:                                                                            | e.g. plan, invoice, subscription                                                              |
| `entity_id`                                                                                   | *Optional[str]*                                                                               | :heavy_minus_sign:                                                                            | e.g. plan_01ABC123                                                                            |
| `expand`                                                                                      | *Optional[str]*                                                                               | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `filters`                                                                                     | List[[models.FilterCondition](../../models/filtercondition.md)]                               | :heavy_minus_sign:                                                                            | filters allows complex filtering based on multiple fields (same as FeatureFilter)             |
| `limit`                                                                                       | *Optional[int]*                                                                               | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `offset`                                                                                      | *Optional[int]*                                                                               | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `order`                                                                                       | [Optional[models.WorkflowExecutionFilterOrder]](../../models/workflowexecutionfilterorder.md) | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `sort`                                                                                        | List[[models.SortCondition](../../models/sortcondition.md)]                                   | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `start_time`                                                                                  | [date](https://docs.python.org/3/library/datetime.html#date-objects)                          | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `status`                                                                                      | [Optional[models.Status]](../../models/status.md)                                             | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `task_queue`                                                                                  | *Optional[str]*                                                                               | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `workflow_id`                                                                                 | *Optional[str]*                                                                               | :heavy_minus_sign:                                                                            | Workflow-specific filters                                                                     |
| `workflow_status`                                                                             | *Optional[str]*                                                                               | :heavy_minus_sign:                                                                            | e.g. Running, Completed, Failed                                                               |
| `workflow_type`                                                                               | *Optional[str]*                                                                               | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `retries`                                                                                     | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                              | :heavy_minus_sign:                                                                            | Configuration to override the default retry behavior of the client.                           |

### Response

**[models.ListWorkflowsResponse](../../models/listworkflowsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |