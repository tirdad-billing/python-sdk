# SubModifyInheritanceRequest


## Fields

| Field                                                                | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `action`                                                             | [Optional[models.InheritanceAction]](../models/inheritanceaction.md) | :heavy_minus_sign:                                                   | N/A                                                                  |
| `external_customer_ids_to_inherit_subscription`                      | List[*str*]                                                          | :heavy_minus_sign:                                                   | ExternalCustomerIDsToInheritSubscription is used for action="add".   |
| `external_customer_ids_to_remove`                                    | List[*str*]                                                          | :heavy_minus_sign:                                                   | ExternalCustomerIDsToRemove is used for action="remove".             |