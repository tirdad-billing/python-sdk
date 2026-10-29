# Commitments

## Overview

### Available Operations

* [create_commitment](#create_commitment) - Create commitment
* [preview_commitment](#preview_commitment) - Preview commitment
* [query_commitment](#query_commitment) - Query commitments
* [get_commitment](#get_commitment) - Get commitment
* [update_commitment](#update_commitment) - Update commitment
* [terminate_commitment](#terminate_commitment) - Terminate commitment

## create_commitment

Creates a commitment on a subscription: a minimum spend or quantity over a term, with optional committed and overage rates.

### Example Usage

<!-- UsageSnippet language="python" operationID="createCommitment" method="post" path="/commitments" -->
```python
from tirdad_sdk import Tirdad
from tirdad_sdk.utils import parse_datetime


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.commitments.create_commitment(measurement="billing_period", name="<value>", scope={
        "entity_type": "group",
    }, start_date=parse_datetime("2025-03-05T22:53:12.661Z"), type_="quantity")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                              | Type                                                                                                   | Required                                                                                               | Description                                                                                            |
| ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ |
| `measurement`                                                                                          | [models.CommitmentMeasurement](../../models/commitmentmeasurement.md)                                  | :heavy_check_mark:                                                                                     | N/A                                                                                                    |
| `name`                                                                                                 | *str*                                                                                                  | :heavy_check_mark:                                                                                     | N/A                                                                                                    |
| `scope`                                                                                                | [models.CommitmentScopeInput](../../models/commitmentscopeinput.md)                                    | :heavy_check_mark:                                                                                     | N/A                                                                                                    |
| `start_date`                                                                                           | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                   | :heavy_check_mark:                                                                                     | N/A                                                                                                    |
| `type`                                                                                                 | [models.CommitmentType](../../models/commitmenttype.md)                                                | :heavy_check_mark:                                                                                     | N/A                                                                                                    |
| `active_windows`                                                                                       | List[[models.ActiveWindow](../../models/activewindow.md)]                                              | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `binding`                                                                                              | *Optional[bool]*                                                                                       | :heavy_minus_sign:                                                                                     | default false                                                                                          |
| `collection_method`                                                                                    | [Optional[models.CommitmentCollectionMethod]](../../models/commitmentcollectionmethod.md)              | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `committed_price`                                                                                      | [Optional[models.CommitmentPriceInput]](../../models/commitmentpriceinput.md)                          | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `end_date`                                                                                             | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                   | :heavy_minus_sign:                                                                                     | EndDate is exclusive; omit it for an open-ended commitment, which bills every period until terminated. |
| `idempotency_key`                                                                                      | *Optional[str]*                                                                                        | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `invoice_description`                                                                                  | *Optional[str]*                                                                                        | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `invoice_label`                                                                                        | *Optional[str]*                                                                                        | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `metadata`                                                                                             | Dict[str, *str*]                                                                                       | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `overage_price`                                                                                        | [Optional[models.CommitmentPriceInput]](../../models/commitmentpriceinput.md)                          | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `priority`                                                                                             | *Optional[int]*                                                                                        | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `subscription_id`                                                                                      | *Optional[str]*                                                                                        | :heavy_minus_sign:                                                                                     | SubscriptionID is required on POST /commitments and set server-side on inline commitments.             |
| `timezone`                                                                                             | *Optional[str]*                                                                                        | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `value`                                                                                                | *Optional[str]*                                                                                        | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `retries`                                                                                              | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                       | :heavy_minus_sign:                                                                                     | Configuration to override the default retry behavior of the client.                                    |

### Response

**[models.CommitmentResponse](../../models/commitmentresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## preview_commitment

Validates a commitment and returns its computed value without creating it.

### Example Usage

<!-- UsageSnippet language="python" operationID="previewCommitment" method="post" path="/commitments/preview" -->
```python
from tirdad_sdk import Tirdad
from tirdad_sdk.utils import parse_datetime


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.commitments.preview_commitment(measurement="billing_period", name="<value>", scope={
        "entity_type": "meter",
    }, start_date=parse_datetime("2024-11-23T11:41:25.905Z"), type_="amount")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                              | Type                                                                                                   | Required                                                                                               | Description                                                                                            |
| ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ |
| `measurement`                                                                                          | [models.CommitmentMeasurement](../../models/commitmentmeasurement.md)                                  | :heavy_check_mark:                                                                                     | N/A                                                                                                    |
| `name`                                                                                                 | *str*                                                                                                  | :heavy_check_mark:                                                                                     | N/A                                                                                                    |
| `scope`                                                                                                | [models.CommitmentScopeInput](../../models/commitmentscopeinput.md)                                    | :heavy_check_mark:                                                                                     | N/A                                                                                                    |
| `start_date`                                                                                           | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                   | :heavy_check_mark:                                                                                     | N/A                                                                                                    |
| `type`                                                                                                 | [models.CommitmentType](../../models/commitmenttype.md)                                                | :heavy_check_mark:                                                                                     | N/A                                                                                                    |
| `active_windows`                                                                                       | List[[models.ActiveWindow](../../models/activewindow.md)]                                              | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `binding`                                                                                              | *Optional[bool]*                                                                                       | :heavy_minus_sign:                                                                                     | default false                                                                                          |
| `collection_method`                                                                                    | [Optional[models.CommitmentCollectionMethod]](../../models/commitmentcollectionmethod.md)              | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `committed_price`                                                                                      | [Optional[models.CommitmentPriceInput]](../../models/commitmentpriceinput.md)                          | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `end_date`                                                                                             | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                   | :heavy_minus_sign:                                                                                     | EndDate is exclusive; omit it for an open-ended commitment, which bills every period until terminated. |
| `idempotency_key`                                                                                      | *Optional[str]*                                                                                        | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `invoice_description`                                                                                  | *Optional[str]*                                                                                        | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `invoice_label`                                                                                        | *Optional[str]*                                                                                        | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `metadata`                                                                                             | Dict[str, *str*]                                                                                       | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `overage_price`                                                                                        | [Optional[models.CommitmentPriceInput]](../../models/commitmentpriceinput.md)                          | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `priority`                                                                                             | *Optional[int]*                                                                                        | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `subscription_id`                                                                                      | *Optional[str]*                                                                                        | :heavy_minus_sign:                                                                                     | SubscriptionID is required on POST /commitments and set server-side on inline commitments.             |
| `timezone`                                                                                             | *Optional[str]*                                                                                        | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `value`                                                                                                | *Optional[str]*                                                                                        | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `retries`                                                                                              | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                       | :heavy_minus_sign:                                                                                     | Configuration to override the default retry behavior of the client.                                    |

### Response

**[models.CommitmentResponse](../../models/commitmentresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## query_commitment

Lists commitments with filtering and sorting. Returns a paginated list.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryCommitment" method="post" path="/commitments/search" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.commitments.query_commitment()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                          | Type                                                                               | Required                                                                           | Description                                                                        |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `active_from`                                                                      | *Optional[str]*                                                                    | :heavy_minus_sign:                                                                 | ActiveFrom/ActiveTo select commitments whose term overlaps [ActiveFrom, ActiveTo). |
| `active_to`                                                                        | *Optional[str]*                                                                    | :heavy_minus_sign:                                                                 | N/A                                                                                |
| `customer_ids`                                                                     | List[*str*]                                                                        | :heavy_minus_sign:                                                                 | N/A                                                                                |
| `end_time`                                                                         | [date](https://docs.python.org/3/library/datetime.html#date-objects)               | :heavy_minus_sign:                                                                 | N/A                                                                                |
| `expand`                                                                           | *Optional[str]*                                                                    | :heavy_minus_sign:                                                                 | N/A                                                                                |
| `filters`                                                                          | List[[models.FilterCondition](../../models/filtercondition.md)]                    | :heavy_minus_sign:                                                                 | N/A                                                                                |
| `ids`                                                                              | List[*str*]                                                                        | :heavy_minus_sign:                                                                 | N/A                                                                                |
| `limit`                                                                            | *Optional[int]*                                                                    | :heavy_minus_sign:                                                                 | N/A                                                                                |
| `offset`                                                                           | *Optional[int]*                                                                    | :heavy_minus_sign:                                                                 | N/A                                                                                |
| `order`                                                                            | [Optional[models.CommitmentFilterOrder]](../../models/commitmentfilterorder.md)    | :heavy_minus_sign:                                                                 | N/A                                                                                |
| `scope_entity_ids`                                                                 | List[*str*]                                                                        | :heavy_minus_sign:                                                                 | N/A                                                                                |
| `scope_entity_type`                                                                | [Optional[models.CommitmentScopeType]](../../models/commitmentscopetype.md)        | :heavy_minus_sign:                                                                 | N/A                                                                                |
| `sort`                                                                             | List[[models.SortCondition](../../models/sortcondition.md)]                        | :heavy_minus_sign:                                                                 | N/A                                                                                |
| `start_time`                                                                       | [date](https://docs.python.org/3/library/datetime.html#date-objects)               | :heavy_minus_sign:                                                                 | N/A                                                                                |
| `status`                                                                           | [Optional[models.Status]](../../models/status.md)                                  | :heavy_minus_sign:                                                                 | N/A                                                                                |
| `statuses`                                                                         | List[[models.CommitmentStatus](../../models/commitmentstatus.md)]                  | :heavy_minus_sign:                                                                 | N/A                                                                                |
| `subscription_ids`                                                                 | List[*str*]                                                                        | :heavy_minus_sign:                                                                 | N/A                                                                                |
| `retries`                                                                          | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                   | :heavy_minus_sign:                                                                 | Configuration to override the default retry behavior of the client.                |

### Response

**[models.ListCommitmentsResponse](../../models/listcommitmentsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_commitment

Loads a single commitment by ID.

### Example Usage

<!-- UsageSnippet language="python" operationID="getCommitment" method="get" path="/commitments/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.commitments.get_commitment(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Commitment ID                                                       |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.CommitmentResponse](../../models/commitmentresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## update_commitment

Updates the descriptive fields of a commitment. Economic terms are immutable.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateCommitment" method="put" path="/commitments/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.commitments.update_commitment(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Commitment ID                                                       |
| `invoice_description`                                               | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `invoice_label`                                                     | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `metadata`                                                          | Dict[str, *str*]                                                    | :heavy_minus_sign:                                                  | N/A                                                                 |
| `name`                                                              | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.CommitmentResponse](../../models/commitmentresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## terminate_commitment

Ends a commitment early, effective at the given time or now.

### Example Usage

<!-- UsageSnippet language="python" operationID="terminateCommitment" method="post" path="/commitments/{id}/terminate" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.commitments.terminate_commitment(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                            | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `id`                                                                 | *str*                                                                | :heavy_check_mark:                                                   | Commitment ID                                                        |
| `cancellation_fee`                                                   | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | N/A                                                                  |
| `effective_at`                                                       | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_minus_sign:                                                   | N/A                                                                  |
| `retries`                                                            | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)     | :heavy_minus_sign:                                                   | Configuration to override the default retry behavior of the client.  |

### Response

**[models.CommitmentResponse](../../models/commitmentresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |