# UpdateUserResponse


## Fields

| Field                                                          | Type                                                           | Required                                                       | Description                                                    |
| -------------------------------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------- |
| `email`                                                        | *Optional[str]*                                                | :heavy_minus_sign:                                             | Empty for service accounts                                     |
| `id`                                                           | *Optional[str]*                                                | :heavy_minus_sign:                                             | N/A                                                            |
| `metadata`                                                     | Dict[str, *str*]                                               | :heavy_minus_sign:                                             | N/A                                                            |
| `name`                                                         | *Optional[str]*                                                | :heavy_minus_sign:                                             | N/A                                                            |
| `roles`                                                        | List[*str*]                                                    | :heavy_minus_sign:                                             | N/A                                                            |
| `tenant`                                                       | [Optional[models.TenantResponse]](../models/tenantresponse.md) | :heavy_minus_sign:                                             | N/A                                                            |
| `type`                                                         | [Optional[models.UserType]](../models/usertype.md)             | :heavy_minus_sign:                                             | N/A                                                            |