# Spacetraders Helper APIs
A collection of helpful APIs for the game spacetraders.io.

The reset of this API will be about 6h behind the game server's reset.

## Static API

An API with static information, such as information about routes.

URL: https://static.spacetraders.bahr.dev

### GET `/goods/{good}`

**Warning**: Only goods that are available on the market will be present here.

Endpoint to get information about a good. Use it with the Static API URL.

**Example**

```
GET https://static.spacetraders.bahr.dev/good/MACHINERY/

{
    "volumePerUnit": 2,
    "symbol": "MACHINERY"
}
```

**Error Codes**

403: You're using the wrong path. This error code is not about permissions.

404: The good does not exist, or the API has no data for it yet.

**Caching**

The result is cached for 3600 seconds. It's unlikely to change unless the game mechanics change.

### GET `/route/{origin}/{destination}/`

**Warning**: Only shipTypes that cost less than 200k credits are considered. Numbers aren't always 100% accurate, so better by 1 more fuel than the API tells you to.

Endpoint to get information about a route. Use it with the Static API URL.

This will yield the result with the higest fuel consumption. Use the optional query parameter `shipType` to get the result for a particular ship.

If you omit the `shipType` the response will tell you which ship type has been used for the resulting fuel.

**Example**

```
GET https://static.spacetraders.bahr.dev/route/OE-UC-AD/OE-BO/?shipType=GR-MK-I

{
    "origin": "OE-UC-AD",
    "destination": "OE-BO",
    "fuel": 46,
    "shipType": "GR-MK-I",
    // optional until data is properly populated
    "duration": 418,
    // optional until data is properly populated
    "distance": 179
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

### GET `/locations/{location}/`

This returns pretty much the same information as [the original market API](https://api.spacetraders.io/#api-marketplace-marketplace).

Endpoint to get latest market information of a location.

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

The result is cached for 30 seconds.

### GET `/locations/{location}/goods/{good}/`

This returns pretty much the same information as [the original market API](https://api.spacetraders.io/#api-marketplace-marketplace).

Endpoint to get the latest market information of a good in a particular location.

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

The result is cached for 30 seconds.

### GET Market Data History

Coming Soon

## Accountant API

Coming Soon

### POST Purchase Goods

Coming Soon. Proxy for [purchase goods API](https://api.spacetraders.io/#api-purchase_orders-NewPurchaseOrder) with transaction recording.

### POST Sell Goods

Coming Soon. Proxy for [sell goods API](https://api.spacetraders.io/#api-sell_orders-NewSellOrder) with transaction recording.

### Get Transactions

Coming Soon. Lists the transactions that you performed through the Accountant API.
