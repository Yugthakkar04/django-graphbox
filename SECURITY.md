# Security Policy

## Supported Versions

Use this section to tell people about which versions of your project are
currently being supported with security updates.

| Version | Supported          |
| ------- | ------------------ |
| 5.1.x   | :white_check_mark: |
| 5.0.x   | :x:                |
| 4.0.x   | :white_check_mark: |
| < 4.0   | :x:                |

import asyncio
from tartiflette import Engine, Resolver
@Resolver("Query.hello")
async def resolver_hello(parent, args, ctx, info):
    return "hello " + args["name"]
async def run():
    tftt_engine = Engine("""
    type Query {
        hello(name: String): String
    }
    """)
    result = await tftt_engine.execute(
        query='query { hello(name: "Chuck") }'
    )
    print(result)
    # {'data': {'hello': 'hello Chuck'}}
if __name__ == "__main__":
    loop = asyncio.get_event_loop()
    loop.run_until_complete(run())

    

## Reporting a Vulnerability

Use this section to tell people how to report a vulnerability.

Tell them where to go, how often they can expect to get an update on a
reported vulnerability, what to expect if the vulnerability is accepted or
declined, etc.
