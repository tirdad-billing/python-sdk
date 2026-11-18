# GetSubscriptionEntitlementsRequest


## Fields

| Field                                                             | Type                                                              | Required                                                          | Description                                                       |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| `id`                                                              | *str*                                                             | :heavy_check_mark:                                                | Subscription ID                                                   |
| `feature_ids`                                                     | List[*str*]                                                       | :heavy_minus_sign:                                                | Feature IDs to filter by                                          |
| `refresh_grants`                                                  | *Optional[bool]*                                                  | :heavy_minus_sign:                                                | Evaluate entitlement grants before returning their usage (slower) |