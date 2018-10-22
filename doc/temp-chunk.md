# Temp Chunk Resource
## PUT
Adds part of the file content for a given temp file that was created using the Temp Chunked File Base resource. Construct the URL for a chunk by adding a slash and the chunk index to the URL of the Temp Chunked File.
The chunk index should be an integer that starts at 0 for the first chunk and then increments by 1 for every subsequent chunk.
The Content-Type header should be set to "application/octet-stream".
Returns a 200 OK response with no content.


Example:
```
curl -v -X PUT -T /path/to/example-part1.dat -H "Content-Type: application/octet-stream" http://127.0.0.1:8080/asset-bank/rest/temp-chunked-files/067e6162-3b6f-4ae2-a171-2470b63d/0
````

```
curl -v -X PUT -T /path/to/example-part2.dat -H "Content-Type: application/octet-stream" http://127.0.0.1:8080/asset-bank/rest/temp-chunked-files/067e6162-3b6f-4ae2-a171-2470b63d/1
```

Response:
```
200 OK
```
