# WebhookDtoAlertWebhookPayload


## Fields

| Field                                                              | Type                                                               | Required                                                           | Description                                                        |
| ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ |
| `alert_status`                                                     | *Optional[str]*                                                    | :heavy_minus_sign:                                                 | N/A                                                                |
| `alert_type`                                                       | *Optional[str]*                                                    | :heavy_minus_sign:                                                 | N/A                                                                |
| `customer`                                                         | [Optional[models.CustomerResponse]](../models/customerresponse.md) | :heavy_minus_sign:                                                 | Customer response object containing all customer information       |
| `event_type`                                                       | [Optional[models.WebhookEventName]](../models/webhookeventname.md) | :heavy_minus_sign:                                                 | N/A                                                                |
| `feature`                                                          | [Optional[models.FeatureResponse]](../models/featureresponse.md)   | :heavy_minus_sign:                                                 | N/A                                                                |
| `wallet`                                                           | [Optional[models.WalletResponse]](../models/walletresponse.md)     | :heavy_minus_sign:                                                 | N/A                                                                |