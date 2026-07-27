# AWSMarketplaceAgreement


## Fields

| Field                                                                  | Type                                                                   | Required                                                               | Description                                                            |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| `concurrent_agreements`                                                | *Optional[bool]*                                                       | :heavy_minus_sign:                                                     | if true, ProductCode is omitted when reporting                         |
| `customer_aws_account_id`                                              | *str*                                                                  | :heavy_check_mark:                                                     | -> BatchMeterUsage's CustomerAWSAccountId                              |
| `dimension`                                                            | *str*                                                                  | :heavy_check_mark:                                                     | -> BatchMeterUsage's Dimension (always "usage_fee" in the cents model) |
| `license_arn`                                                          | *str*                                                                  | :heavy_check_mark:                                                     | -> BatchMeterUsage's LicenseArn; identifies the buyer's agreement      |
| `product_code`                                                         | *str*                                                                  | :heavy_check_mark:                                                     | -> BatchMeterUsage's ProductCode (omitted when ConcurrentAgreements)   |