# Embedded Data Mapping Base

## GET
Returns all embedded data mappings currently in the system.

Example:
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/embedded-data-mappings > mappings.json
```

Response (contents of "mappings.json" file):
```
[
    {"url":"http://127.0.0.1:8080/asset-bank/rest/embedded-data-mappings/1",
    	"type":"IPTC",
    	"displayName":"Some Caption",
     	"tagName":"SomeCaption",
	“mappingDirection”:”Upload”,
	“attributeLabel”:”Description”,
	“attributeUrl”:”http://127.0.0.1:8080/asset-bank/rest/attributes/1”},

    {"url":"http://127.0.0.1:8080/asset-bank/rest/embedded-data-mappings/2",
    	"type":"EXIF",
    	"displayName":"Artist",
     	"tagName":"Artist",
	“mappingDirection”:”Download”,
	“attributeLabel”:”Title”,
	“attributeUrl”:”http://127.0.0.1:8080/asset-bank/rest/attributes/2”}

]
```
