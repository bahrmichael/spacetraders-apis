# spacetraders-apis
A collection of helpful APIs for the game spacetraders.io

## Static API

An API with static information, such as information about routes.

URL: https://static.spacetraders.bahr.dev

### GET Route

**Warning**: Currently only available for the system OE. Also only shipTypes that cost less than 200k credits are considered.

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

**Error Codes**

404: The route does not exist, or the API has no data for it yet.

**Disclaimer**

Don't 100% rely on these numbers. I suggest to always buy 1 fuel more than the API tells you to. Still refining it :)

**Caching**

The result is cached for 3600 seconds.

## Market API

An API with market information, such as the latest prices and volumes.

URL: https://market.spacetraders.bahr.dev

### GET Location

Endpoint to get latest market information of a location.

`/locations/{location}/`

**Example**

```
GET https://market.spacetraders.bahr.dev/locations/OM-PM/

[
    {
        "symbol": "DRONES",
        "volumePerUnit": 1,
        "pricePerUnit": 29,
        "spread": 1,
        "purchasePricePerUnit": 30,
        "sellPricePerUnit": 28,
        "quantityAvailable": 35175
    },
    // ...
]
```

**Caching**

The result is cached for 10 seconds.

### GET Location And Good

Endpoint to get the latest market information of a good in a particular location.

`/locations/{location}/goods/{good}`

**Example**

```
GET https://market.spacetraders.bahr.dev/locations/OM-PM/good/MACHINERY/

{
    "symbol": "MACHINERY",
    "volumePerUnit": 2,
    "pricePerUnit": 402,
    "spread": 2,
    "purchasePricePerUnit": 404,
    "sellPricePerUnit": 400,
    "quantityAvailable": 36950
}
```

**Caching**

The result is cached for 10 seconds.
