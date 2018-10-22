# User Search Resource
## GET
Searches for users based on the given criteria.
Parameters
username: the username to match users to
emailAddress: the email address to find matching users for
forename: the forename of the user in Asset Bank to match against
surname: the surname of the user in Asset Bank to match against
includeHidden: whether to return hidden users in the search results (true or false - default is false)
includeExpired: whether to return expired users in the search results (true or false - default is false)
exactTextMatch: only results which exactly match the given text parameters will be returned e.g. 'rob' will not match 'robert' (true or false - default is false)


Example:
```
curl -X GET -H "Accept: application/json" 'http://127.0.0.1:8080/asset-bank/rest/user-search?username=admin'
```

Response:
```
[
    {
        "id": 1,
        "emailAddress": "",
        "forename": "Frank",
        "groupIds": null,
        "lightboxUrl": "http://127.0.0.1:8080/asset-bank/rest/users/1/lightboxes",
        "surname": "User",
        "url": "http://127.0.0.1:8080/asset-bank/rest/users/1",
        "username": "admin"
    },
    {
        "id": 2,
 "emailAddress": "admin2@bright-interactive.com",
        "forename": "Second",
        "groupIds": null,
        "lightboxUrl": "http://127.0.0.1:8080/asset-bank/rest/users/616/lightboxes",
        "surname": "Admin",
        "url": "http://127.0.0.1:8080/asset-bank/rest/users/616",
        "username": "admin2"
    }
]
```
