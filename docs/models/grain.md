# Grain

## Example Usage

```python
from tirdad_sdk.models import Grain

# Open enum: unrecognized values are captured as UnrecognizedStr
value: Grain = "hour"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"hour"`
- `"day"`
- `"week"`
- `"month"`
