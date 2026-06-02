# AggregationType

## Example Usage

```python
from tirdad_sdk.models import AggregationType

# Open enum: unrecognized values are captured as UnrecognizedStr
value: AggregationType = "COUNT"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"COUNT"`
- `"SUM"`
- `"AVG"`
- `"COUNT_UNIQUE"`
- `"LATEST"`
- `"SUM_WITH_MULTIPLIER"`
- `"MAX"`
- `"WEIGHTED_SUM"`
