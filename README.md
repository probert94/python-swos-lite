# python-swos-lite
Python library to interact with MikroTik SwitchOS Lite

## Features

- Get identity, model, serial number, OS version, MAC and IP address

- Read cpu temperature, current, voltage, and power consumption of the switch

- List ports with name, status, speed, duplex mode etc.

- Check PoE status, power usage, voltage, and current per port

## Installation

Install via pip:

```bash
pip install python-swos-lite
```

> Requires Python 3.10 or higher

## Dependencies

- aiohttp 3.8.5 or higher – for HTTP communication with the switch
- demjson3 3.0.6 or higher - for tolerant JSON parsing

## Usage Example

```python
from aiohttp import ClientSession, DigestAuthMiddleware
from swos_lite.client import Client
from swos_lite.endpoints.link import LinkEndpoint
from swos_lite.endpoints.sys import SystemEndpoint
from swos_lite.endpoints.poe import PoEEndpoint

async def main():
    (digest_auth) = DigestAuthMiddleware(login="user", password="password")
    async with ClientSession() as session:
        session._middlewares = (digest_auth,)
        client = Client(session, "http://swos-lite.local")
        await client.fetch(SystemEndpoint)
```

## Supported Devices

This library targets MikroTik switches running **SwitchOS Lite** and has been tested with:
- MikroTik CSS610-8P-2S+ running Switch OS Lite 2.19

Other models with SwitchOS Lite may also work.

## License

MIT License

## Contributing

Contributions are welcome!\
Feel free to open issues, submit pull requests, or suggest features.

