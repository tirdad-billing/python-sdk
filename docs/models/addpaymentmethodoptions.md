# AddPaymentMethodOptions


## Fields

| Field                                                                               | Type                                                                                | Required                                                                            | Description                                                                         |
| ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `payment_method_types`                                                              | List[*str*]                                                                         | :heavy_minus_sign:                                                                  | PaymentMethodTypes are the methods it sets up, e.g. ["enach"] for Razorpay.         |
| `sets_default`                                                                      | *Optional[bool]*                                                                    | :heavy_minus_sign:                                                                  | SetsDefault reports whether it can make the saved method the default (Stripe only). |