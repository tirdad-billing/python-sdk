# CloneFeatureRequest


## Fields

| Field                                                                 | Type                                                                  | Required                                                              | Description                                                           |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| `description`                                                         | *Optional[str]*                                                       | :heavy_minus_sign:                                                    | Description overrides the source feature's description when provided  |
| `lookup_key`                                                          | *Optional[str]*                                                       | :heavy_minus_sign:                                                    | LookupKey is required and must be unique across published features    |
| `metadata`                                                            | Dict[str, *str*]                                                      | :heavy_minus_sign:                                                    | N/A                                                                   |
| `name`                                                                | *Optional[str]*                                                       | :heavy_minus_sign:                                                    | Name is required and must be different from the source feature's name |