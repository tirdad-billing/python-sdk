# GetCustomerEntitlementsByExternalIDRequest


## Fields

| Field                                                             | Type                                                              | Required                                                          | Description                                                       |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| `external_id`                                                     | *str*                                                             | :heavy_check_mark:                                                | Customer External ID                                              |
| `refresh_grants`                                                  | *Optional[bool]*                                                  | :heavy_minus_sign:                                                | Evaluate entitlement grants before returning their usage (slower) |