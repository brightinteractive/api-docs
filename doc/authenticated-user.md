# Authenticated User Instance Resource
## GET
Provides details on the authenticated user that is making the current request.

Example:
```
curl -X GET -H "Accept: application/json" 'http://127.0.0.1:8080/asset-bank/rest/authenticated-user'
```

Response:
```
{
    "id": 2,
    "emailAddress": "admin2@bright-interactive.com",
    "forename": "Second",
    "groupIds": null,
    "lightboxUrl": "http://127.0.0.1:8080/asset-bank/rest/users/616/lightboxes",
    "surname": "Admin",
    "url": "http://127.0.0.1:8080/asset-bank/rest/users/616",
    "username": "admin2",
    "isAdmin": true
}
```
