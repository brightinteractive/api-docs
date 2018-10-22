# Attributes Base Resource
## GET
Returns the Attribute Instance Resource urls for all Attributes in the system.

Example:
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/attributes > attributes.json
```

Response (contents of "attributes.json" file):
```
[
	"http://127.0.0.1:8080/asset-bank-current/rest/attributes/1",
	"http://127.0.0.1:8080/asset-bank-current/rest/attributes/3",
	"http://127.0.0.1:8080/asset-bank-current/rest/attributes/4",
	"http://127.0.0.1:8080/asset-bank-current/rest/attributes/5",
	"http://127.0.0.1:8080/asset-bank-current/rest/attributes/6"
]
```
