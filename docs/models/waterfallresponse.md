# WaterfallResponse


## Fields

| Field                                                                  | Type                                                                   | Required                                                               | Description                                                            |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| `items`                                                                | List[[models.WaterfallRow](../models/waterfallrow.md)]                 | :heavy_minus_sign:                                                     | N/A                                                                    |
| `pagination`                                                           | [Optional[models.PaginationResponse]](../models/paginationresponse.md) | :heavy_minus_sign:                                                     | N/A                                                                    |
| `totals`                                                               | List[[models.WaterfallCell](../models/waterfallcell.md)]               | :heavy_minus_sign:                                                     | per period over all rows, never paged                                  |