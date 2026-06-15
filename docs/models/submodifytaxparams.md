# SubModifyTaxParams


## Fields

| Field                                                                   | Type                                                                    | Required                                                                | Description                                                             |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| `action`                                                                | [models.SubModifyTaxAction](../models/submodifytaxaction.md)            | :heavy_check_mark:                                                      | N/A                                                                     |
| `association_id`                                                        | *Optional[str]*                                                         | :heavy_minus_sign:                                                      | Required when action="remove". ID of the TaxAssociation to soft-delete. |
| `effective_date`                                                        | [date](https://docs.python.org/3/library/datetime.html#date-objects)    | :heavy_minus_sign:                                                      | Optional. When to apply the change; defaults to now if omitted.         |
| `tax_rate_id`                                                           | *Optional[str]*                                                         | :heavy_minus_sign:                                                      | Required when action="add". ID of the active tax rate to attach.        |