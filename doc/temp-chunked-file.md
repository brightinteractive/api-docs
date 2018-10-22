# Temp Chunked File Resource
## GET
Returns the file content for a given temp file that was created using the Temp Chunked File Base resource and whose content was previously PUT to this resource. Note that this content may not be complete, for example if GET is called on the resource before all the content chunks have been PUT.

Example:
```
curl -X GET -H "Accept: application/octet-stream" http://127.0.0.1:8080/asset-bank/rest/temp-chunked-files/067e6162-3b6f-4ae2-a171-2470b63dff00 > output.dat
```

Response
```
200 OK
```

## DELETE
Deletes a temp chunked file (and all its chunks)

Example:
```
curl -X DELETE http://127.0.0.1:8080/asset-bank/rest/temp-chunked-files/067e6162-3b6f-4ae2-a171-2470b63d
```

Response:  
```
204 No Content
```
