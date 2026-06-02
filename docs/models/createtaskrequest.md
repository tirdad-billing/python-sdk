# CreateTaskRequest


## Fields

| Field                                        | Type                                         | Required                                     | Description                                  |
| -------------------------------------------- | -------------------------------------------- | -------------------------------------------- | -------------------------------------------- |
| `entity_type`                                | [models.EntityType](../models/entitytype.md) | :heavy_check_mark:                           | N/A                                          |
| `file_name`                                  | *Optional[str]*                              | :heavy_minus_sign:                           | N/A                                          |
| `file_type`                                  | [models.FileType](../models/filetype.md)     | :heavy_check_mark:                           | N/A                                          |
| `file_url`                                   | *str*                                        | :heavy_check_mark:                           | N/A                                          |
| `metadata`                                   | Dict[str, *Any*]                             | :heavy_minus_sign:                           | N/A                                          |
| `task_type`                                  | [models.TaskType](../models/tasktype.md)     | :heavy_check_mark:                           | N/A                                          |