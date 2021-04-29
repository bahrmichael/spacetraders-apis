# spacetraders-apis
A collection of helpful APIs for the game spacetraders.io

## Static API

An API with static information, such as information about routes.

URL: https://static.spacetraders.bahr.dev

### GET Route

**Warning**: Currently only available for the system OE.

Endpoint to get information about a route. Use it with the Static API URL.

`/route/{origin}/{destination}/`

This will yield the result with the higest fuel consumption. Use the optional query parameter `shipType` to get the result for a particular ship.

**Example**

```
GET https://static.spacetraders.bahr.dev/route/OE-PM/OE-PM-TR/?shipType=EM-MK-I

{
    "origin": "OE-PM",
    "destination": "OE-PM-TR",
    "fuel": 3,
    "shipType": "EM-MK-I"
}
```

**Disclaimer**

Don't 100% rely on these numbers. I suggest to always buy 1 fuel more than the API tells you to. Still refining it :)

**Caching**

The result is cached for 3600 seconds.

