# GetPendingSchedulesResponse

List of pending schedules for a subscription


## Fields

| Field                                                                                  | Type                                                                                   | Required                                                                               | Description                                                                            |
| -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| `count`                                                                                | *Optional[int]*                                                                        | :heavy_minus_sign:                                                                     | count is the number of pending schedules                                               |
| `schedules`                                                                            | List[[models.SubscriptionScheduleResponse](../models/subscriptionscheduleresponse.md)] | :heavy_minus_sign:                                                                     | schedules is the list of pending schedules                                             |