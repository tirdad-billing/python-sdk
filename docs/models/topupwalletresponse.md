# TopUpWalletResponse


## Fields

| Field                                                                                | Type                                                                                 | Required                                                                             | Description                                                                          |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| `invoice_id`                                                                         | *Optional[str]*                                                                      | :heavy_minus_sign:                                                                   | Invoice ID if an invoice was created (only for PURCHASED_CREDIT_INVOICED)            |
| `wallet`                                                                             | [Optional[models.WalletResponse]](../models/walletresponse.md)                       | :heavy_minus_sign:                                                                   | N/A                                                                                  |
| `wallet_transaction`                                                                 | [Optional[models.WalletTransactionResponse]](../models/wallettransactionresponse.md) | :heavy_minus_sign:                                                                   | N/A                                                                                  |