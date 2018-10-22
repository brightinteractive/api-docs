# Embedded Data Mapping Instance Resource
## GET
Returns a single specified embedded data mapping.

Example:
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/embedded-data-mappings/1 > mapping.json
```

Response (contents of "mappings.json" file):
```
{
  "url":"http://127.0.0.1:8080/asset-bank/rest/embedded-data-mappings/1",
	"type":"IPTC",
	"displayName":"Some Caption",
 	"tagName":"SomeCaption",
  “mappingDirection”:”Upload”,
  “attributeLabel”:”Description”,
  “attributeUrl”:”http://127.0.0.1:8080/asset-bank/rest/attributes/1”
}
```
