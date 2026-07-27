# Marketplace

## Overview

### Available Operations

* [post_marketplace_agreements](#post_marketplace_agreements) - Register an AWS Marketplace agreement

## post_marketplace_agreements

Registers an AWS Marketplace buyer agreement against an existing Tirdad subscription, upserting plan/subscription/customer integration mappings in one call.

### Example Usage

<!-- UsageSnippet language="python" operationID="post_/marketplace/agreements" method="post" path="/marketplace/agreements" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.marketplace.post_marketplace_agreements(customer_id="<id>", plan_id="<id>", provider="tabs", subscription_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                               | Type                                                                                    | Required                                                                                | Description                                                                             |
| --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| `customer_id`                                                                           | *str*                                                                                   | :heavy_check_mark:                                                                      | N/A                                                                                     |
| `plan_id`                                                                               | *str*                                                                                   | :heavy_check_mark:                                                                      | N/A                                                                                     |
| `provider`                                                                              | [models.SecretProvider](../../models/secretprovider.md)                                 | :heavy_check_mark:                                                                      | N/A                                                                                     |
| `subscription_id`                                                                       | *str*                                                                                   | :heavy_check_mark:                                                                      | N/A                                                                                     |
| `aws`                                                                                   | [Optional[models.AWSMarketplaceAgreement]](../../models/awsmarketplaceagreement.md)     | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `azure`                                                                                 | [Optional[models.AzureMarketplaceAgreement]](../../models/azuremarketplaceagreement.md) | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `gcp`                                                                                   | [Optional[models.GCPMarketplaceAgreement]](../../models/gcpmarketplaceagreement.md)     | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `retries`                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                        | :heavy_minus_sign:                                                                      | Configuration to override the default retry behavior of the client.                     |

### Response

**[models.RegisterMarketplaceAgreementResponse](../../models/registermarketplaceagreementresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |