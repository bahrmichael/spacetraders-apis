# spacetraders-apis
A collection of helpful APIs for the game spacetraders.io

## Static API

An API with static information, such as information about routes.

URL: https://static.spacetraders.bahr.dev

### GET Route

**Warning**: Only shipTypes that cost less than 200k credits are considered. Numbers aren't always 100% accurate, so better by 1 more fuel than the API tells you to.

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

403: You're using the wrong path. This error code is not about permissions.

404: The route does not exist, or the API has no data for it yet.

**Caching**

The result is cached for 3600 seconds. It's unlikely to change unless the game mechanics change.

## Market API

An API with market information, such as the latest prices and volumes.

URL: https://market.spacetraders.bahr.dev

### GET Market Location

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

**Error Codes**

403: You're using the wrong path. This error code is not about permissions.

**Caching**

The result is cached for 10 seconds.

### GET Market for Good at Location

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

**Error Codes**

403: You're using the wrong path. This error code is not about permissions.

**Caching**

The result is cached for 10 seconds.
