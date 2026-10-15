# ResumeSubscriptionRequest

Resumes a paused subscription now. The billing anchor is kept, so the first period runs from the resume time to the next billing date.


## Fields

| Field                                                                | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `metadata`                                                           | Dict[str, *str*]                                                     | :heavy_minus_sign:                                                   | Metadata merged into the pause<br/>@Example {"resumed_by": "admin"}  |
| `proration_behavior`                                                 | [Optional[models.ProrationBehavior]](../models/prorationbehavior.md) | :heavy_minus_sign:                                                   | N/A                                                                  |