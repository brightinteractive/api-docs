# Display Attribute Group Instance Resource
## GET
Returns the details for the given display attribute group.

Example:
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/display-attribute-groups/1 > dag.json
```

Response (contents of "dag.json" file):
```
{
   "url": "http://127.0.0.1:8080/asset-bank/rest/display-attribute-groups/1",
   “id”: 1,
   “displayAreaId”: 1,
   “entityId”: 0,
   "attributes": [
       {
           "id": "1",
           "label": "File",
           "type": "0",
	    "url": "http://127.0.0.1:8080/asset-bank/rest/attributes/1"
       },
       {
           "id": "2",
           "label": "ID",
           "type": "0",
	    "url": "http://127.0.0.1:8080/asset-bank/rest/attributes/2"
       },
       <...ETC...>
   ],
   "name": "View / Edit"
}
```
