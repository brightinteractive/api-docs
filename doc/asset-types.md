# Asset Types Base Resource
## GET
Returns the Asset Type Instance Resource urls for all Asset Types in the system.

Example:
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/asset-types > asset-types.json
```

Response (contents of "asset-types.json" file):
```
[
	"http://127.0.0.1:8080/asset-bank/rest/asset-types/1",
	"http://127.0.0.1:8080/asset-bank/rest/asset-types/2",
	"http://127.0.0.1:8080/asset-bank/rest/asset-types/3",
	"http://127.0.0.1:8080/asset-bank/rest/asset-types/4",
	"http://127.0.0.1:8080/asset-bank/rest/asset-types/5"
]
```
