# User Instance Resource
## GET
Returns the details for the given user.

Example:
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/users/1 > user.json
```

Response (contents of "user.json" file):
```
{
    "id": 1,
    "emailAddress": "admin@test.com",
    "forename": "Admin",
    "groupIds": [1,2,3],
    "lightboxUrl": "http://127.0.0.1:8080/asset-bank/rest/users/1/lightboxes",
    "surname": "User",
    "url": "http://127.0.0.1:8080/asset-bank/rest/users/1",
    "username": "admin",
    "isAdmin": true
}
```

## PUT
Updates the details for the given user.  API clients should first GET the details on the user, update the attributes as necessary, and then PUT the representation back to the original URL.


Example:
[Using "user.json" in the previous example, modify one of the writable values, e.g. forename "forename": "Admin" -> "forename": "Frank"]

```
curl -X PUT -H "Content-Type: application/json" -H "Accept: application/json" --data "@user.json" http://127.0.0.1:8080/asset-bank/rest/users/1
```

Response:
```
{
    "id": 1,
    "emailAddress": "",
    "forename": "Frank",
    "groupIds": [1,2,3],
    "lightboxUrl": "http://127.0.0.1:8080/asset-bank/rest/users/1/lightboxes",
    "surname": "User",
    "url": "http://127.0.0.1:8080/asset-bank/rest/users/1",
    "username": "admin",
    "isAdmin": true
}
```


## DELETE
Deletes the given user. Returns a 204 "No Content" response back.

Example:
```
curl -X DELETE http://127.0.0.1:8080/asset-bank/rest/users/7
```

Response:
```
204 No Content
```
