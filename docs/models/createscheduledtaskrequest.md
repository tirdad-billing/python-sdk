# CreateScheduledTaskRequest


## Fields

| Field                                                                  | Type                                                                   | Required                                                               | Description                                                            |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| `connection_id`                                                        | *str*                                                                  | :heavy_check_mark:                                                     | N/A                                                                    |
| `enabled`                                                              | *Optional[bool]*                                                       | :heavy_minus_sign:                                                     | N/A                                                                    |
| `entity_type`                                                          | [models.ScheduledTaskEntityType](../models/scheduledtaskentitytype.md) | :heavy_check_mark:                                                     | N/A                                                                    |
| `interval`                                                             | [models.ScheduledTaskInterval](../models/scheduledtaskinterval.md)     | :heavy_check_mark:                                                     | N/A                                                                    |
| `job_config`                                                           | [models.S3JobConfig](../models/s3jobconfig.md)                         | :heavy_check_mark:                                                     | N/A                                                                    |