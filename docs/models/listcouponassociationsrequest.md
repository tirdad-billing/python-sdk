# ListCouponAssociationsRequest


## Fields

| Field                                     | Type                                      | Required                                  | Description                               |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| `subscription_ids`                        | List[*str*]                               | :heavy_minus_sign:                        | Filter by subscription IDs (max 100)      |
| `coupon_ids`                              | List[*str*]                               | :heavy_minus_sign:                        | Filter by coupon IDs (max 100)            |
| `active_only`                             | *Optional[bool]*                          | :heavy_minus_sign:                        | Return only currently active associations |
| `limit`                                   | *Optional[int]*                           | :heavy_minus_sign:                        | Page size                                 |
| `offset`                                  | *Optional[int]*                           | :heavy_minus_sign:                        | Page offset                               |