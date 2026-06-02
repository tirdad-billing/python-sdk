# SubModifyTrialEndRequest


## Fields

| Field                                                                            | Type                                                                             | Required                                                                         | Description                                                                      |
| -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| `action`                                                                         | [models.TrialEndAction](../models/trialendaction.md)                             | :heavy_check_mark:                                                               | N/A                                                                              |
| `new_trial_end`                                                                  | [date](https://docs.python.org/3/library/datetime.html#date-objects)             | :heavy_minus_sign:                                                               | NewTrialEnd is the new trial end date. Required when action is "scheduled_date". |