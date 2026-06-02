# ErrorCode

## Example Usage

```python
from tirdad_sdk.models import ErrorCode

# Open enum: unrecognized values are captured as UnrecognizedStr
value: ErrorCode = "http_client_error"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"http_client_error"`
- `"system_error"`
- `"internal_error"`
- `"not_found"`
- `"already_exists"`
- `"version_conflict"`
- `"validation_error"`
- `"invalid_operation"`
- `"permission_denied"`
- `"database_error"`
- `"service_unavailable"`
- `"too_many_requests"`
