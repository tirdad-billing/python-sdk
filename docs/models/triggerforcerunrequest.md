# TriggerForceRunRequest


## Fields

| Field                                                                         | Type                                                                          | Required                                                                      | Description                                                                   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `customer_external_ids`                                                       | List[*str*]                                                                   | :heavy_check_mark:                                                            | Limits a wallet_ledger export to these customers; empty means every customer. |
| `end_time`                                                                    | [date](https://docs.python.org/3/library/datetime.html#date-objects)          | :heavy_minus_sign:                                                            | N/A                                                                           |
| `start_time`                                                                  | [date](https://docs.python.org/3/library/datetime.html#date-objects)          | :heavy_minus_sign:                                                            | N/A                                                                           |