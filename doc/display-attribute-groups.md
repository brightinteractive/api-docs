# Display Attribute Group Base Resource
## GET
Lists the Display Attribute Group Instance Resource URLs for all Display Attribute Groups in the system.

Example:
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/display-attribute-groups > dags.json
```

Response (contents of "dags.json" file):
```
[
	"http://127.0.0.1:8080/asset-bank-current/rest/display-attribute-groups/1",
	"http://127.0.0.1:8080/asset-bank-current/rest/display-attribute-groups/3",
	"http://127.0.0.1:8080/asset-bank-current/rest/display-attribute-groups/4",
	"http://127.0.0.1:8080/asset-bank-current/rest/display-attribute-groups/5",
	"http://127.0.0.1:8080/asset-bank-current/rest/display-attribute-groups/6"
]
```
