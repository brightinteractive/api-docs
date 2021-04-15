# Access Level Image Resource

# GET
This resource doesn't serve the image directly. Instead it returns a 303 redirect to Asset Bank URL which serves the content. Returns a 204 No Content if there is no image associated with the given Access Level.

Example:
```
curl -L -X GET -H "Accept: application/octet-stream" http://127.0.0.1:8080/asset-bank/rest/access-levels/1/image > image.jpg
```

Response:
```
303 See Other
Location: http://127.0.0.1:8080/asset-bank/images/standard/categories/1.jpg
```


# PUT
Updates the image for the given Access Level.
Note:
The filename must be set using the Content-Disposition header (see example below).  
The Content-Type header should be set to "application/octet-stream".
The file content must be put in the request body

Example:

```
curl -v -X PUT -T /path/to/image.jpg -H "Content-Type: application/octet-stream" -H "Content-Disposition: attachment; filename=image.jpg" http://127.0.0.1:8080/asset-bank/rest/access-levels/1/image
```

Response:
```
200 OK
```

# DELETE
Deletes the image for the given Access Level.

Example:
```
curl -X DELETE http://127.0.0.1:8080/asset-bank/rest/access-levels/1/image
```

Response:
```
204 No Content
```
