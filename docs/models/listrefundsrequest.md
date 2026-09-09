# ListRefundsRequest


## Fields

| Field                          | Type                           | Required                       | Description                    |
| ------------------------------ | ------------------------------ | ------------------------------ | ------------------------------ |
| `invoice_ids`                  | List[*str*]                    | :heavy_minus_sign:             | Filter by invoice IDs          |
| `payment_ids`                  | List[*str*]                    | :heavy_minus_sign:             | Filter by payment IDs          |
| `credit_note_ids`              | List[*str*]                    | :heavy_minus_sign:             | Filter by credit note IDs      |
| `refund_statuses`              | List[*str*]                    | :heavy_minus_sign:             | Filter by refund status        |
| `refund_destinations`          | List[*str*]                    | :heavy_minus_sign:             | Filter by refund destination   |
| `gateway`                      | *Optional[str]*                | :heavy_minus_sign:             | Filter by payment gateway      |
| `only_settled`                 | *Optional[bool]*               | :heavy_minus_sign:             | Only refunds that have settled |
| `limit`                        | *Optional[int]*                | :heavy_minus_sign:             | Limit                          |
| `offset`                       | *Optional[int]*                | :heavy_minus_sign:             | Offset                         |