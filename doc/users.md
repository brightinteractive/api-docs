# Users Base Resource
## GET
Lists the User Instance Resource URLs for all Users in the system.

Example:
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/users > users.json
```

Response (contents of "users.json" file):
```
[
	"http://127.0.0.1:8080/asset-bank-current/rest/users/1",
	"http://127.0.0.1:8080/asset-bank-current/rest/users/3",
	"http://127.0.0.1:8080/asset-bank-current/rest/users/4",
	"http://127.0.0.1:8080/asset-bank-current/rest/users/5",
	"http://127.0.0.1:8080/asset-bank-current/rest/users/6"
]
```

## POST
Creates a new empty User with the given username and returns a 201 created response, linking to a User Instance Resource.  You will still need to issue a PUT request to the User Instance Resource to set the user's details on the resource.

Example:
```
curl -X POST http://127.0.0.1:8080/asset-bank/rest/users?username=TESTING
```

Response:  
```
201 Created
Location: http://127.0.0.1:8080/asset-bank/rest/users/16
```
