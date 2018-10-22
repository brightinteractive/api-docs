# User Lightboxes Resource
## GET
Returns a list of lightboxes for a given user.
Each item in the list will contain the lightbox name and size,  and links to the Lightbox Instance Resource and the Lightbox Contents Resource.

Example (read the lightboxes for user id 1):
```
curl -X GET http://127.0.0.1:8080/asset-bank/rest/users/1/lightboxes -H "Accept: application/json"
```

Response:
```
[
    {
 		"id": 1,
        "lightboxInstanceUrl": "http://127.0.0.1:8080/asset-bank/rest/users/1/lightboxes/1",
        "lightboxContentsUrl": "http://127.0.0.1:8080/asset-bank/rest/users/1/lightboxes/1/contents",
        "lightboxPublicUrl": null,
        "name": "My Lightbox",
        "size": 3
    },
    {
 		"id": 30,
        "lightboxInstanceUrl": "http://127.0.0.1:8080/asset-bank/rest/users/1/lightboxes/30",
        "lightboxContentsUrl": "http://127.0.0.1:8080/asset-bank/rest/users/1/lightboxes/30/contents",
        "lightboxPublicUrl": "http://127.0.0.1:8080/asset-bank/action/viewPublicAssetBox?assetBoxId=30",
        "name": "My second lightbox",
        "size": 0
    }
]
```

## POST
Creates a new lightbox with the given name, for the given user.
If the new lightbox is created successfully then a 201 created response is returned, linking to the Lightbox Instance Resource. If the user already has a lightbox with exactly the same name as the one provided then a 409 Conflict response is returned.

Example (JSON):
```
curl -v -X POST -H "Content-type: application/json" --data '{"name":"my new lightbox"}' http://127.0.0.1:8080/asset-bank/rest/users/1/lightboxes
```


Response:
```
201 Created
Location: http://127.0.0.1:8080/asset-bank/rest/users/1/lightboxes/2
```

or if the name exists:

```
409 Conflict
Content-Type: text/plain

A Lightbox named my new lightbox already exists for the user.
```

If you do not supply a name for the lightbox then a 400 Bad Request response will be returned:
Example (bad request - no name):
```
curl -v -X POST http://127.0.0.1:8080/asset-bank/rest/users/1/lightboxes
```

Response:
```
400 Bad Request
Content-Type: text/plain

You must supply a name when creating a new lightbox.
```
