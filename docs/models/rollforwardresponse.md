# RollforwardResponse


## Fields

| Field                                                                  | Type                                                                   | Required                                                               | Description                                                            |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| `items`                                                                | List[[models.RollforwardRow](../models/rollforwardrow.md)]             | :heavy_minus_sign:                                                     | per period, account and group; empty without group_by                  |
| `pagination`                                                           | [Optional[models.PaginationResponse]](../models/paginationresponse.md) | :heavy_minus_sign:                                                     | N/A                                                                    |
| `totals`                                                               | List[[models.RollforwardRow](../models/rollforwardrow.md)]             | :heavy_minus_sign:                                                     | per period and account, all groups                                     |