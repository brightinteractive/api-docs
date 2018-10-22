# Temp Chunked Files Base Resource
For a step by step guide to chunked file upload see http://www.assetbank.co.uk/go/knowledgebase/upload-chunks.html.
## POST
Returns a 201 Created response, linking to a new Temp Chunked File resource.  The new resource has no content, so you will need to subsequently issue one or more PUT requests to the Temp Chunked File resource to upload the contents of the file.

Example:
```
curl -v -X POST -H "Content-type: application/json" http://127.0.0.1:8080/asset-bank/rest/temp-chunked-files
```

Response:  
```
201 Created
Location: http://127.0.0.1:8080/asset-bank/rest/temp-chunked-files/067e6162-3b6f-4ae2-a171-2470b63dff00
```
