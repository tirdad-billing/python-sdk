# GCPMarketplaceAgreement


## Fields

| Field                                                               | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `account_id`                                                        | *str*                                                               | :heavy_check_mark:                                                  | writes the customer mapping; not read in the report payload         |
| `metric_name`                                                       | *str*                                                               | :heavy_check_mark:                                                  | -> services.report's metricName (always "{service_name}/usage_fee") |
| `service_name`                                                      | *str*                                                               | :heavy_check_mark:                                                  | -> services.report URL's service_name; identifies the product       |
| `usage_reporting_id`                                                | *str*                                                               | :heavy_check_mark:                                                  | -> services.report's consumerId; identifies the buyer               |