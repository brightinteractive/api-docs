
# List Attribute Value Instance Resource
## GET
Returns the details for the given list attribute value.

Example:
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/list-attribute-values/1 > listValue.json
```

Response (contents of "listValue.json" file):
```
{
	    "url": "http://127.0.0.1:8080/asset-bank/rest/list-attribute-values/1",
    "value": "Active"
    "additionalValue: ""
}
```
