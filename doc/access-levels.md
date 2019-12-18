# Access Level Base Resource
## GET

Returns the Access Level Instance Resource urls for all Access Levels in the system.

Example:

```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/access-levels > al.json
```

Response (contents of "al.json" file):
```
[
	"http://127.0.0.1:8080/asset-bank/rest/access-levels/1",
	"http://127.0.0.1:8080/asset-bank/rest/access-levels/2",
	"http://127.0.0.1:8080/asset-bank/rest/access-levels/3",
	"http://127.0.0.1:8080/asset-bank/rest/access-levels/4",
	"http://127.0.0.1:8080/asset-bank/rest/access-levels/5"
]
```

## POST
Creates a new Access Level.

Returns a 201 Created response if successful, linking to the new Access Level resource.

Example:
```
curl -v -H "Content-type: application/json" --data '{"name": "Templates", "parent": "http://127.0.0.1:8080/asset-bank/rest/access-levels/6"}' http://127.0.0.1:8080/asset-bank/rest/access-levels
```


Response:
```
201 Created
Location: http://127.0.0.1:8080/asset-bank/rest/access-levels/12
```

Parameters:
name: access level name, cannot be empty
parent (optional): resource URL of parent Access Level
isAlwaysAssignable (optional, default false): boolean value to specify whether the Access Level can be assigned to assets even if it has sub-access levels
hasPermissions (optional, default false): boolean value to specify whether the Access Level can have permissions independently from its parent (defaults to true for top-level Access Levels)

