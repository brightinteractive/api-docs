# Keyword Base Resource
## GET
Returns the Keyword Instance Resource urls for all keywords for the given Keyword Picker attribute.

Example:
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/attributes/701/keywords > cat.json
```

Response (contents of "cat.json" file):
```
[
	"http://127.0.0.1:8080/asset-bank/rest/attributes/701/keywords/1",
	"http://127.0.0.1:8080/asset-bank/rest/attributes/701/keywords/3",
	"http://127.0.0.1:8080/asset-bank/rest/attributes/701/keywords/4",
	"http://127.0.0.1:8080/asset-bank/rest/attributes/701/keywords/5",
	"http://127.0.0.1:8080/asset-bank/rest/attributes/701/keywords/6"
]
```
