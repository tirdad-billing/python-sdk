# Users

## Overview

### Available Operations

* [create_user](#create_user) - Create user or service account
* [get_user_info](#get_user_info) - Get current user
* [update_user](#update_user) - Update current user
* [query_user](#query_user) - Query users
* [update_service_account](#update_service_account) - Update service account
* [delete_service_account](#delete_service_account) - Delete service account

## create_user

Create a user account (type=user, email required; returns user + password for login) or a service account (type=service_account, roles required) for API/automation access.

### Example Usage

<!-- UsageSnippet language="python" operationID="createUser" method="post" path="/users" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.users.create_user(type_="user")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `type`                                                              | [models.UserType](../../models/usertype.md)                         | :heavy_check_mark:                                                  | N/A                                                                 |
| `email`                                                             | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Required when type is "user"                                        |
| `name`                                                              | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Display name; optional for service accounts                         |
| `roles`                                                             | List[*str*]                                                         | :heavy_minus_sign:                                                  | Required when type is "service_account"                             |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.CreateUserResponse](../../models/createuserresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_user_info

Use to show the logged-in user's profile in the UI or to check permissions and roles for the current session.

### Example Usage

<!-- UsageSnippet language="python" operationID="getUserInfo" method="get" path="/users/me" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.users.get_user_info()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.UserResponse](../../models/userresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 401                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## update_user

Update the current authenticated user. Supports name and metadata updates.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateUser" method="put" path="/users/me" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.users.update_user()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `metadata`                                                          | Dict[str, *str*]                                                    | :heavy_minus_sign:                                                  | N/A                                                                 |
| `name`                                                              | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.UpdateUserResponse](../../models/updateuserresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## query_user

Use when listing or searching service accounts in an admin UI, or when auditing who has API access and which roles they have.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryUser" method="post" path="/users/search" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.users.query_user()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                            | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `end_time`                                                           | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_minus_sign:                                                   | N/A                                                                  |
| `expand`                                                             | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | N/A                                                                  |
| `filters`                                                            | List[[models.FilterCondition](../../models/filtercondition.md)]      | :heavy_minus_sign:                                                   | filters allows complex filtering based on multiple fields            |
| `limit`                                                              | *Optional[int]*                                                      | :heavy_minus_sign:                                                   | N/A                                                                  |
| `offset`                                                             | *Optional[int]*                                                      | :heavy_minus_sign:                                                   | N/A                                                                  |
| `order`                                                              | [Optional[models.UserFilterOrder]](../../models/userfilterorder.md)  | :heavy_minus_sign:                                                   | N/A                                                                  |
| `roles`                                                              | List[*str*]                                                          | :heavy_minus_sign:                                                   | N/A                                                                  |
| `sort`                                                               | List[[models.SortCondition](../../models/sortcondition.md)]          | :heavy_minus_sign:                                                   | N/A                                                                  |
| `start_time`                                                         | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_minus_sign:                                                   | N/A                                                                  |
| `status`                                                             | [Optional[models.Status]](../../models/status.md)                    | :heavy_minus_sign:                                                   | N/A                                                                  |
| `type`                                                               | [Optional[models.UserType]](../../models/usertype.md)                | :heavy_minus_sign:                                                   | N/A                                                                  |
| `user_ids`                                                           | List[*str*]                                                          | :heavy_minus_sign:                                                   | Specific filters for users                                           |
| `retries`                                                            | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)     | :heavy_minus_sign:                                                   | Configuration to override the default retry behavior of the client.  |

### Response

**[models.ListUsersResponse](../../models/listusersresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## update_service_account

Update a service account by ID (name only).

### Example Usage

<!-- UsageSnippet language="python" operationID="updateServiceAccount" method="put" path="/users/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.users.update_service_account(id="<id>", name="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Service Account ID                                                  |
| `name`                                                              | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.UpdateServiceAccountResponse](../../models/updateserviceaccountresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## delete_service_account

Soft-delete (archive) a service account by ID.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteServiceAccount" method="delete" path="/users/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    tirdad.users.delete_service_account(id="<id>")

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Service Account ID                                                  |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |