# Category Base Resource
## GET
Returns the Category Instance Resource urls for all Categories in the system.

Example:
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/categories > cat.json
```

Response (contents of "cat.json" file):
```
[
	"http://127.0.0.1:8080/asset-bank/rest/categories/1",
	"http://127.0.0.1:8080/asset-bank/rest/categories/2",
	"http://127.0.0.1:8080/asset-bank/rest/categories/3",
	"http://127.0.0.1:8080/asset-bank/rest/categories/4",
	"http://127.0.0.1:8080/asset-bank/rest/categories/5"
]
```


