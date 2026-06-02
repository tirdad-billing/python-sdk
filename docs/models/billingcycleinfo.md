# BillingCycleInfo


## Fields

| Field                                                                | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `billing_anchor`                                                     | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_minus_sign:                                                   | billing_anchor is the new billing anchor                             |
| `billing_cadence`                                                    | [Optional[models.BillingCadence]](../models/billingcadence.md)       | :heavy_minus_sign:                                                   | N/A                                                                  |
| `billing_period`                                                     | [Optional[models.BillingPeriod]](../models/billingperiod.md)         | :heavy_minus_sign:                                                   | N/A                                                                  |
| `billing_period_count`                                               | *Optional[int]*                                                      | :heavy_minus_sign:                                                   | billing_period_count is the billing period count                     |
| `period_end`                                                         | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_minus_sign:                                                   | period_end is the end of the new billing period                      |
| `period_start`                                                       | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_minus_sign:                                                   | period_start is the start of the new billing period                  |