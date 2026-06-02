# CreateUserRequest


## Fields

| Field                                    | Type                                     | Required                                 | Description                              |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| `email`                                  | *Optional[str]*                          | :heavy_minus_sign:                       | Required when type is "user"             |
| `roles`                                  | List[*str*]                              | :heavy_minus_sign:                       | Required when type is "service_account"  |
| `type`                                   | [models.UserType](../models/usertype.md) | :heavy_check_mark:                       | N/A                                      |