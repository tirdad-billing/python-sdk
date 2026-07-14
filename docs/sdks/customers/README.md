# Customers

## Overview

### Available Operations

* [update_customer](#update_customer) - Update customer
* [create_customer](#create_customer) - Create customer
* [get_customer_by_external_id](#get_customer_by_external_id) - Get customer by external ID
* [get_customer_entitlements_by_external_id](#get_customer_entitlements_by_external_id) - Get customer entitlements by external ID
* [query_customer](#query_customer) - Query customers
* [get_customer_usage_summary](#get_customer_usage_summary) - Get customer usage summary
* [get_customer](#get_customer) - Get customer
* [delete_customer](#delete_customer) - Delete customer
* [get_customer_entitlements](#get_customer_entitlements) - Get customer entitlements
* [get_customer_upcoming_grants](#get_customer_upcoming_grants) - Get upcoming credit grant applications

## update_customer

Use when updating customer details (e.g. name, email, or metadata). Identify by id or external_customer_id.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateCustomer" method="put" path="/customers" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.customers.update_customer()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                   | Type                                                                                                        | Required                                                                                                    | Description                                                                                                 |
| ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                        | *Optional[str]*                                                                                             | :heavy_minus_sign:                                                                                          | Customer ID                                                                                                 |
| `external_customer_id`                                                                                      | *Optional[str]*                                                                                             | :heavy_minus_sign:                                                                                          | Customer External ID                                                                                        |
| `address_city`                                                                                              | *Optional[str]*                                                                                             | :heavy_minus_sign:                                                                                          | address_city is the updated city name with maximum 100 characters                                           |
| `address_country`                                                                                           | *Optional[str]*                                                                                             | :heavy_minus_sign:                                                                                          | address_country is the updated two-letter ISO 3166-1 alpha-2 country code                                   |
| `address_line1`                                                                                             | *Optional[str]*                                                                                             | :heavy_minus_sign:                                                                                          | address_line1 is the updated primary address line with maximum 255 characters                               |
| `address_line2`                                                                                             | *Optional[str]*                                                                                             | :heavy_minus_sign:                                                                                          | address_line2 is the updated secondary address line with maximum 255 characters                             |
| `address_postal_code`                                                                                       | *Optional[str]*                                                                                             | :heavy_minus_sign:                                                                                          | address_postal_code is the updated postal code with maximum 20 characters                                   |
| `address_state`                                                                                             | *Optional[str]*                                                                                             | :heavy_minus_sign:                                                                                          | address_state is the updated state, province, or region name with maximum 100 characters                    |
| `email`                                                                                                     | *Optional[str]*                                                                                             | :heavy_minus_sign:                                                                                          | email is the updated email address and must be a valid email format if provided                             |
| `external_id`                                                                                               | *Optional[str]*                                                                                             | :heavy_minus_sign:                                                                                          | external_id is the updated external identifier for the customer                                             |
| `integration_entity_mapping`                                                                                | List[[models.CreateEntityIntegrationMappingRequest](../../models/createentityintegrationmappingrequest.md)] | :heavy_minus_sign:                                                                                          | integration_entity_mapping contains provider integration mappings for this customer                         |
| `metadata`                                                                                                  | Dict[str, *str*]                                                                                            | :heavy_minus_sign:                                                                                          | metadata contains updated key-value pairs that will replace existing metadata                               |
| `name`                                                                                                      | *Optional[str]*                                                                                             | :heavy_minus_sign:                                                                                          | name is the updated name or company name for the customer                                                   |
| `timezone`                                                                                                  | *Optional[str]*                                                                                             | :heavy_minus_sign:                                                                                          | timezone is the updated IANA timezone name for the customer (e.g. "Asia/Kolkata", "America/New_York")       |
| `retries`                                                                                                   | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                            | :heavy_minus_sign:                                                                                          | Configuration to override the default retry behavior of the client.                                         |

### Response

**[models.CustomerResponse](../../models/customerresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## create_customer

Use when onboarding a new billing customer (e.g. sign-up or CRM sync). Ideal for linking via external_customer_id to your app's user id.

### Example Usage

<!-- UsageSnippet language="python" operationID="createCustomer" method="post" path="/customers" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.customers.create_customer(external_id="<id>", name="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                     | Type                                                                                                                                                                                                          | Required                                                                                                                                                                                                      | Description                                                                                                                                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `external_id`                                                                                                                                                                                                 | *str*                                                                                                                                                                                                         | :heavy_check_mark:                                                                                                                                                                                            | external_id is the unique identifier from your system to reference this customer (required)                                                                                                                   |
| `name`                                                                                                                                                                                                        | *str*                                                                                                                                                                                                         | :heavy_check_mark:                                                                                                                                                                                            | name is the full name or company name of the customer                                                                                                                                                         |
| `address_city`                                                                                                                                                                                                | *Optional[str]*                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                            | address_city is the city name with maximum 100 characters                                                                                                                                                     |
| `address_country`                                                                                                                                                                                             | *Optional[str]*                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                            | address_country is the two-letter ISO 3166-1 alpha-2 country code                                                                                                                                             |
| `address_line1`                                                                                                                                                                                               | *Optional[str]*                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                            | address_line1 is the primary address line with maximum 255 characters                                                                                                                                         |
| `address_line2`                                                                                                                                                                                               | *Optional[str]*                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                            | address_line2 is the secondary address line with maximum 255 characters                                                                                                                                       |
| `address_postal_code`                                                                                                                                                                                         | *Optional[str]*                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                            | address_postal_code is the ZIP code or postal code with maximum 20 characters                                                                                                                                 |
| `address_state`                                                                                                                                                                                               | *Optional[str]*                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                            | address_state is the state, province, or region name with maximum 100 characters                                                                                                                              |
| `email`                                                                                                                                                                                                       | *Optional[str]*                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                            | email is the customer's email address and must be a valid email format if provided                                                                                                                            |
| `integration_entity_mapping`                                                                                                                                                                                  | List[[models.CreateEntityIntegrationMappingRequest](../../models/createentityintegrationmappingrequest.md)]                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                            | integration_entity_mapping contains provider integration mappings for this customer                                                                                                                           |
| `metadata`                                                                                                                                                                                                    | Dict[str, *str*]                                                                                                                                                                                              | :heavy_minus_sign:                                                                                                                                                                                            | metadata contains additional key-value pairs for storing extra information                                                                                                                                    |
| `skip_onboarding_workflow`                                                                                                                                                                                    | *Optional[bool]*                                                                                                                                                                                              | :heavy_minus_sign:                                                                                                                                                                                            | skip_onboarding_workflow when true, prevents the customer onboarding workflow from being triggered<br/>This is used internally when a customer is created via a workflow to prevent infinite loops<br/>Default: false |
| `tax_rate_overrides`                                                                                                                                                                                          | List[[models.TaxRateOverride](../../models/taxrateoverride.md)]                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                            | tax_rate_overrides contains tax rate configurations to be linked to this customer                                                                                                                             |
| `timezone`                                                                                                                                                                                                    | *Optional[str]*                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                            | timezone is the customer's IANA timezone name (e.g. "Asia/Kolkata", "America/New_York")<br/>Defaults to "UTC" if not provided                                                                                 |
| `retries`                                                                                                                                                                                                     | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                              | :heavy_minus_sign:                                                                                                                                                                                            | Configuration to override the default retry behavior of the client.                                                                                                                                           |

### Response

**[models.CustomerResponse](../../models/customerresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_customer_by_external_id

Use when resolving a customer by your app's id (e.g. from your user table). Ideal for integrations that key by external id.

### Example Usage

<!-- UsageSnippet language="python" operationID="getCustomerByExternalId" method="get" path="/customers/external/{external_id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.customers.get_customer_by_external_id(external_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `external_id`                                                       | *str*                                                               | :heavy_check_mark:                                                  | Customer External ID                                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.CustomerResponse](../../models/customerresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_customer_entitlements_by_external_id

Use when checking entitlements by your app's customer id (e.g. feature gating at the edge). Supports optional filters (feature_ids, subscription_ids).

### Example Usage

<!-- UsageSnippet language="python" operationID="getCustomerEntitlementsByExternalID" method="get" path="/customers/external/{external_id}/entitlements" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.customers.get_customer_entitlements_by_external_id(external_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `external_id`                                                       | *str*                                                               | :heavy_check_mark:                                                  | Customer External ID                                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.CustomerEntitlementsResponse](../../models/customerentitlementsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## query_customer

Use when listing or searching customers (e.g. admin CRM or reporting). Returns a paginated list; supports filtering and sorting.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryCustomer" method="post" path="/customers/search" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.customers.query_customer()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                   | Type                                                                        | Required                                                                    | Description                                                                 |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| `customer_ids`                                                              | List[*str*]                                                                 | :heavy_minus_sign:                                                          | N/A                                                                         |
| `email`                                                                     | *Optional[str]*                                                             | :heavy_minus_sign:                                                          | N/A                                                                         |
| `end_time`                                                                  | [date](https://docs.python.org/3/library/datetime.html#date-objects)        | :heavy_minus_sign:                                                          | N/A                                                                         |
| `expand`                                                                    | *Optional[str]*                                                             | :heavy_minus_sign:                                                          | N/A                                                                         |
| `external_id`                                                               | *Optional[str]*                                                             | :heavy_minus_sign:                                                          | N/A                                                                         |
| `external_ids`                                                              | List[*str*]                                                                 | :heavy_minus_sign:                                                          | N/A                                                                         |
| `filters`                                                                   | List[[models.FilterCondition](../../models/filtercondition.md)]             | :heavy_minus_sign:                                                          | N/A                                                                         |
| `limit`                                                                     | *Optional[int]*                                                             | :heavy_minus_sign:                                                          | N/A                                                                         |
| `metadata`                                                                  | Dict[str, *str*]                                                            | :heavy_minus_sign:                                                          | N/A                                                                         |
| `offset`                                                                    | *Optional[int]*                                                             | :heavy_minus_sign:                                                          | N/A                                                                         |
| `order`                                                                     | [Optional[models.CustomerFilterOrder]](../../models/customerfilterorder.md) | :heavy_minus_sign:                                                          | N/A                                                                         |
| `sort`                                                                      | List[[models.SortCondition](../../models/sortcondition.md)]                 | :heavy_minus_sign:                                                          | N/A                                                                         |
| `start_time`                                                                | [date](https://docs.python.org/3/library/datetime.html#date-objects)        | :heavy_minus_sign:                                                          | N/A                                                                         |
| `status`                                                                    | [Optional[models.Status]](../../models/status.md)                           | :heavy_minus_sign:                                                          | N/A                                                                         |
| `retries`                                                                   | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)            | :heavy_minus_sign:                                                          | Configuration to override the default retry behavior of the client.         |

### Response

**[models.ListCustomersResponse](../../models/listcustomersresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_customer_usage_summary

Use when showing a customer's usage (e.g. portal or overage alerts). Identify by customer_id or customer_lookup_key; supports filters.

### Example Usage

<!-- UsageSnippet language="python" operationID="getCustomerUsageSummary" method="get" path="/customers/usage" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.customers.get_customer_usage_summary()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `customer_id`                                                       | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `customer_lookup_key`                                               | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `feature_ids`                                                       | List[*str*]                                                         | :heavy_minus_sign:                                                  | N/A                                                                 |
| `feature_lookup_keys`                                               | List[*str*]                                                         | :heavy_minus_sign:                                                  | N/A                                                                 |
| `subscription_ids`                                                  | List[*str*]                                                         | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.CustomerUsageSummaryResponse](../../models/customerusagesummaryresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_customer

Use when you need to load a single customer (e.g. for a billing portal or to attach a subscription).

### Example Usage

<!-- UsageSnippet language="python" operationID="getCustomer" method="get" path="/customers/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.customers.get_customer(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Customer ID                                                         |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.CustomerResponse](../../models/customerresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## delete_customer

Use when removing a customer (e.g. GDPR or churn). Returns 204 No Content on success.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteCustomer" method="delete" path="/customers/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    tirdad.customers.delete_customer(id="<id>")

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Customer ID                                                         |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_customer_entitlements

Use when checking what a customer can access (e.g. feature gating or usage limits). Supports optional filters (feature_ids, subscription_ids).

### Example Usage

<!-- UsageSnippet language="python" operationID="getCustomerEntitlements" method="get" path="/customers/{id}/entitlements" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.customers.get_customer_entitlements(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Customer ID                                                         |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.CustomerEntitlementsResponse](../../models/customerentitlementsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_customer_upcoming_grants

Use when showing upcoming or pending credits for a customer (e.g. in a portal or for forecasting).

### Example Usage

<!-- UsageSnippet language="python" operationID="getCustomerUpcomingGrants" method="get" path="/customers/{id}/grants/upcoming" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.customers.get_customer_upcoming_grants(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Customer ID                                                         |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ListCreditGrantApplicationsResponse](../../models/listcreditgrantapplicationsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |