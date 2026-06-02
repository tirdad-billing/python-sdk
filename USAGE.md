<!-- Start SDK Example Usage [usage] -->
```python
# Synchronous Example
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.addons.create_addon(lookup_key="<value>", name="<value>")

    # Handle response
    print(res)
```

</br>

The same SDK client can also be used to make asynchronous requests by importing asyncio.

```python
# Asynchronous Example
import asyncio
from tirdad_sdk import Tirdad

async def main():

    async with Tirdad(
        api_key_auth="<YOUR_API_KEY_HERE>",
    ) as tirdad:

        res = await tirdad.addons.create_addon_async(lookup_key="<value>", name="<value>")

        # Handle response
        print(res)

asyncio.run(main())
```
<!-- End SDK Example Usage [usage] -->