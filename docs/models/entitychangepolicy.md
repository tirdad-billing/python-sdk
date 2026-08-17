# EntityChangePolicy


## Fields

| Field                                                                           | Type                                                                            | Required                                                                        | Description                                                                     |
| ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| `default_behaviour`                                                             | [Optional[models.EntityChangeBehaviour]](../models/entitychangebehaviour.md)    | :heavy_minus_sign:                                                              | N/A                                                                             |
| `overrides`                                                                     | Dict[str, [models.EntityChangeBehaviour](../models/entitychangebehaviour.md)]   | :heavy_minus_sign:                                                              | Overrides is keyed by addon_associations.id (instance), not catalogue addon_id. |