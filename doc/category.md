# Category Instance Resource
## GET
Lists the details for the given category

Example:
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/categories/2 > cat.json
```

Response (contents of "cat.json" file):
```
{
    	"url":"http://127.0.0.1:8080/asset-bank/rest/categories/2",
 	"id":2,
 	"name":"Cat Name",
 	"description":"Description",
 	"children":[{
 		"url":"http://127.0.0.1:8080/asset-bank/rest/categories/9",
 		"id":9,
 		"name":"Child",
 		"description":"Description",
 		"parent":"http://127.0.0.1:8080/asset-bank/rest/categories/2"
 	]}

}
```
