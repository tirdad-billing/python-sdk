# SubModifyGroupedInvoicingParams


## Fields

| Field                                                                | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `action`                                                             | [models.GroupedInvoicingAction](../models/groupedinvoicingaction.md) | :heavy_check_mark:                                                   | N/A                                                                  |
| `child_subscription_ids`                                             | List[*str*]                                                          | :heavy_minus_sign:                                                   | N/A                                                                  |
| `parent_subscription_id`                                             | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | ParentSubscriptionID is required for action 'add'.                   |