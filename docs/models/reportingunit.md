# ReportingUnit


## Fields

| Field                                                                        | Type                                                                         | Required                                                                     | Description                                                                  |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `conversion_rate`                                                            | *Optional[float]*                                                            | :heavy_minus_sign:                                                           | Multiplier: reporting_unit_value = unit_value * conversion_rate; must be > 0 |
| `unit_plural`                                                                | *Optional[str]*                                                              | :heavy_minus_sign:                                                           | Display unit label, plural (e.g. "seconds")                                  |
| `unit_singular`                                                              | *Optional[str]*                                                              | :heavy_minus_sign:                                                           | Display unit label, singular (e.g. "second")                                 |