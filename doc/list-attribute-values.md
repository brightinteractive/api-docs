# List Attribute Values Base Resource
## GET
Returns the allowed values for the given List Attribute.

Example:
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/attributes/21/list-attribute-values > listValues.json
```


Response (contents of "listValues.json" file):
```
[
    {"url":"http://127.0.0.1:8080/asset-bank/rest/list-attribute-values/6","value":"Inactive","additionalValue":"Inactive (no longer visible)"},	
    {"url":"http://127.0.0.1:8080/asset-bank/rest/list-attribute-values/7","value":"Active","additionalValue":""},
    {"url":"http://127.0.0.1:8080/asset-bank/rest/list-attribute-values/8","value":"Expired","additionalValue":"Expired (no longer visible)"}
]
```

The "additional values" are optional items of text for the attribute values which if present are shown instead of the value text on the asset detail page.
## POST
Add a new value for the list attribute. The format for the data is the same as that returned by the List Attribute Value Instance Resource GET method (see below), except the url field is not required (and will be ignored if sent). The value field is required and cannot be empty. The additional value field is not required so can be excluded or can be empty if included.
Returns a 201 Created response is successful, linking to the new List Attribute Value resource.  

Example (JSON):
```
curl -v -X POST -H "Content-type: application/json" --data '{"value":"Delete", "additionalValue":"Expired, reviewed and marked for deletion"}' http://127.0.0.1:8080/asset-bank/rest/attributes/21/list-attribute-values
```

Response:
```
201 Created
Location: http://127.0.0.1:8080/asset-bank/list-attribute-values/9
```
If the value is excluded or empty a bad request response will be sent

Example (bad request - no value):
```
curl -v -X POST http://127.0.0.1:8080/asset-bank/rest/attributes/21/list-attribute-values
```

Response:
```
400 Bad Request
Content-Type: text/plain
The list value cannot be blank.
```
