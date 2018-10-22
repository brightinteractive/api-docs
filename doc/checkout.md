# Asset Checkout Base Resource
## POST
POSTing an AssetId to this resource returns a See Other response, referring to a Resource which can be used to check that asset in or out to a given user.

Example:
```
curl -v -X POST -H "Content-type: application/json" --data '{"assetId":5}' http://127.0.0.1:8080/asset-bank/rest/checkout
```

Response:
```
HTTP/1.1 303 See Other
Location: http://127.0.0.1:8080/asset-bank/rest/checkout/5
```


Asset Checkout Resource
## GET
Returns the checkout status for the given asset, which will be a user ID, indicating which user currently has the asset checked out.  If the user ID is less than or equal to 0 then the asset is not currently checked out.

Example (read the asset check-out status):
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/assets/5/checkout/
```

Response:
```
{"userId": "0"}
```

## PUT
Update the checkout status for the given asset, with a user ID, indicating which user to check the asset out to.  If the user ID is 0, then the asset should be checked in. If omitted, the asset will be checked out to the currently authenticated user (if using OAuth2), or the application user (otherwise).

Example (check-out the asset to user id 8):
```
curl -X PUT -H "Content-type: application/json" --data '{"userId":8}' -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/assets/5/checkout
```

Response:
```
{"userId": "8"}
```
