# Commitments

## Overview

### Available Operations

* [create_commitment](#create_commitment) - Create commitment
* [preview_commitment](#preview_commitment) - Preview commitment
* [query_commitment](#query_commitment) - Query commitments
* [get_commitment](#get_commitment) - Get commitment
* [update_commitment](#update_commitment) - Update commitment
* [get_commitment_billing_terms](#get_commitment_billing_terms) - Get billing terms
* [replace_commitment_billing_terms](#replace_commitment_billing_terms) - Edit billing terms
* [preview_commitment_billing_terms](#preview_commitment_billing_terms) - Preview billing terms edit
* [list_commitment_instalments](#list_commitment_instalments) - List instalments
* [trigger_commitment_instalment](#trigger_commitment_instalment) - Trigger instalment
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
| `start_date`                                                                                           | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                   | :heavy_check_mark:                                                                                     | StartDate and EndDate within a second after a billing period edge are taken as that edge.              |
| `type`                                                                                                 | [models.CommitmentType](../../models/commitmenttype.md)                                                | :heavy_check_mark:                                                                                     | N/A                                                                                                    |
| `active_windows`                                                                                       | List[[models.ActiveWindow](../../models/activewindow.md)]                                              | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `billing_terms`                                                                                        | List[[models.BillingTermInput](../../models/billingterminput.md)]                                      | :heavy_minus_sign:                                                                                     | BillingTerms apply only to collection_method billing_terms, which requires at least one.               |
| `binding`                                                                                              | *Optional[bool]*                                                                                       | :heavy_minus_sign:                                                                                     | default false                                                                                          |
| `collection_method`                                                                                    | [Optional[models.CommitmentCollectionMethod]](../../models/commitmentcollectionmethod.md)              | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `committed_price`                                                                                      | [Optional[models.CommitmentPriceInput]](../../models/commitmentpriceinput.md)                          | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `end_date`                                                                                             | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                   | :heavy_minus_sign:                                                                                     | EndDate is exclusive; omit it for an open-ended commitment, which bills every period until terminated. |
| `idempotency_key`                                                                                      | *Optional[str]*                                                                                        | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `instalment_invoicing`                                                                                 | [Optional[models.InstalmentDelivery]](../../models/instalmentdelivery.md)                              | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
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
| `start_date`                                                                                           | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                   | :heavy_check_mark:                                                                                     | StartDate and EndDate within a second after a billing period edge are taken as that edge.              |
| `type`                                                                                                 | [models.CommitmentType](../../models/commitmenttype.md)                                                | :heavy_check_mark:                                                                                     | N/A                                                                                                    |
| `active_windows`                                                                                       | List[[models.ActiveWindow](../../models/activewindow.md)]                                              | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `billing_terms`                                                                                        | List[[models.BillingTermInput](../../models/billingterminput.md)]                                      | :heavy_minus_sign:                                                                                     | BillingTerms apply only to collection_method billing_terms, which requires at least one.               |
| `binding`                                                                                              | *Optional[bool]*                                                                                       | :heavy_minus_sign:                                                                                     | default false                                                                                          |
| `collection_method`                                                                                    | [Optional[models.CommitmentCollectionMethod]](../../models/commitmentcollectionmethod.md)              | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `committed_price`                                                                                      | [Optional[models.CommitmentPriceInput]](../../models/commitmentpriceinput.md)                          | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `end_date`                                                                                             | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                   | :heavy_minus_sign:                                                                                     | EndDate is exclusive; omit it for an open-ended commitment, which bills every period until terminated. |
| `idempotency_key`                                                                                      | *Optional[str]*                                                                                        | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
| `instalment_invoicing`                                                                                 | [Optional[models.InstalmentDelivery]](../../models/instalmentdelivery.md)                              | :heavy_minus_sign:                                                                                     | N/A                                                                                                    |
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

| Parameter                                                            | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `id`                                                                 | *str*                                                                | :heavy_check_mark:                                                   | Commitment ID                                                        |
| `end_date`                                                           | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_minus_sign:                                                   | EndDate can't be changed yet; terminate the commitment to end it.    |
| `invoice_description`                                                | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | N/A                                                                  |
| `invoice_label`                                                      | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | N/A                                                                  |
| `metadata`                                                           | Dict[str, *str*]                                                     | :heavy_minus_sign:                                                   | N/A                                                                  |
| `name`                                                               | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | N/A                                                                  |
| `retries`                                                            | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)     | :heavy_minus_sign:                                                   | Configuration to override the default retry behavior of the client.  |

### Response

**[models.CommitmentResponse](../../models/commitmentresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_commitment_billing_terms

Returns the commitment's current billing terms with its scheduled and invoiced instalments in billing order. Invoiced instalments may come from terms an edit replaced. Cancelled instalments are listed by the instalments endpoint.

### Example Usage

<!-- UsageSnippet language="python" operationID="getCommitmentBillingTerms" method="get" path="/commitments/{id}/billing-terms" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.commitments.get_commitment_billing_terms(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Commitment ID                                                       |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.BillingTermsResponse](../../models/billingtermsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## replace_commitment_billing_terms

Replaces the whole set of billing terms of an active commitment. Its scheduled instalments are cancelled and the new terms generate instalments for what the invoiced ones leave of the commitment total; invoiced instalments and their invoices are kept. A term without bill_on or start_date starts at the billing period holding now, or at the commitment start once its term has ended. Returns the new terms with the scheduled and invoiced instalments in billing order.

### Example Usage

<!-- UsageSnippet language="python" operationID="replaceCommitmentBillingTerms" method="put" path="/commitments/{id}/billing-terms" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.commitments.replace_commitment_billing_terms(id="<id>", billing_terms=[])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Commitment ID                                                       |
| `billing_terms`                                                     | List[[models.BillingTermInput](../../models/billingterminput.md)]   | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.BillingTermsResponse](../../models/billingtermsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## preview_commitment_billing_terms

Returns what editing the billing terms would produce, without saving anything: the new terms with the invoiced and new instalments in billing order.

### Example Usage

<!-- UsageSnippet language="python" operationID="previewCommitmentBillingTerms" method="post" path="/commitments/{id}/billing-terms/preview" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.commitments.preview_commitment_billing_terms(id="<id>", billing_terms=[
        {
            "kind": "once",
            "value_type": "fixed",
        },
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Commitment ID                                                       |
| `billing_terms`                                                     | List[[models.BillingTermInput](../../models/billingterminput.md)]   | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.BillingTermsResponse](../../models/billingtermsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## list_commitment_instalments

Lists the instalments of the commitment in billing order. Without a status filter every instalment is listed, cancelled ones included.

### Example Usage

<!-- UsageSnippet language="python" operationID="listCommitmentInstalments" method="get" path="/commitments/{id}/instalments" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.commitments.list_commitment_instalments(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Commitment ID                                                       |
| `status`                                                            | List[*str*]                                                         | :heavy_minus_sign:                                                  | Only instalments in these statuses (scheduled, invoiced, cancelled) |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ListInstalmentsResponse](../../models/listinstalmentsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## trigger_commitment_instalment

Bills a manual instalment of an active commitment on bill_on, now by default, which must fall within the commitment term. The instalment goes on the first subscription invoice at or after that date, or on its own invoice once due when its instalment_invoicing, the term's or else the commitment's, is separate_invoice. Either way it waits while the subscription is trialing or paused. Until it is triggered, a manual instalment waits at the end of the term, and bill_on can only move earlier; edit the billing terms to bill it later.

### Example Usage

<!-- UsageSnippet language="python" operationID="triggerCommitmentInstalment" method="post" path="/commitments/{id}/instalments/{instalment_id}/trigger" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.commitments.trigger_commitment_instalment(id="<id>", instalment_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `id`                                                                      | *str*                                                                     | :heavy_check_mark:                                                        | Commitment ID                                                             |
| `instalment_id`                                                           | *str*                                                                     | :heavy_check_mark:                                                        | Instalment ID                                                             |
| `bill_on`                                                                 | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | BillOn within a second after a billing period edge is taken as that edge. |
| `retries`                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)          | :heavy_minus_sign:                                                        | Configuration to override the default retry behavior of the client.       |

### Response

**[models.BillingtermInstalment](../../models/billingterminstalment.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## terminate_commitment

Ends a commitment immediately. effective_at defaults to now and cannot be in the future. Under billing terms, its scheduled instalments are cancelled, and those already due by effective_at are billed together as one settlement; later instalments are not billed and nothing is refunded. The settlement and a fixed cancellation fee, when given, are billed together on one one-off invoice.

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

| Parameter                                                                                          | Type                                                                                               | Required                                                                                           | Description                                                                                        |
| -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| `id`                                                                                               | *str*                                                                                              | :heavy_check_mark:                                                                                 | Commitment ID                                                                                      |
| `cancellation_fee`                                                                                 | [Optional[models.CancellationFeeInput]](../../models/cancellationfeeinput.md)                      | :heavy_minus_sign:                                                                                 | N/A                                                                                                |
| `effective_at`                                                                                     | [date](https://docs.python.org/3/library/datetime.html#date-objects)                               | :heavy_minus_sign:                                                                                 | EffectiveAt defaults to now; within a second after a billing period edge it is taken as that edge. |
| `retries`                                                                                          | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                   | :heavy_minus_sign:                                                                                 | Configuration to override the default retry behavior of the client.                                |

### Response

**[models.CommitmentResponse](../../models/commitmentresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |