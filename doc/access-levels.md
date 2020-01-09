# Access Levels
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


## GET
Lists the details for the given access level

Example:
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/access-levels/1 > al.json
```

Response (content of "al.json" file):
```
{
 "url": "http://127.0.0.1:8081/asset-bank/rest/access-levels/1",
 "id": 1,
 "name": "Documents",
 "description": "Description",
 "parent": null,
 "imageUrl": "http://127.0.0.1:8081/asset-bank/rest/access-levels/1/image",
 "isAlwaysAssignable": true,
 "hasPermissions": true,
 "isSelectedOnLoad": false,
 "isBrowsable": true,
 "showPromotedItems": false,
 "showRecentItems": false,
 "children": [
   {
     "url": "http://127.0.0.1:8081/asset-bank/rest/access-levels/7",
     "id": 7,
     "name": "MyDocs",
     "description": "Description",
     "parent": "http://127.0.0.1:8081/asset-bank/rest/access-levels/1",
     "imageUrl": "http://127.0.0.1:8081/asset-bank/rest/access-levels/7/image",
     "isAlwaysAssignable": true,
     "hasPermissions": false,
     "isSelectedOnLoad": false,
     "isBrowsable": true,
     "showPromotedItems": false,
     "showRecentItems": false,
     "children": [],
     "count": 0
   }
 ],
 "count": 0
}
```


## PUT
Updates details for the given Access Level. API clients should first GET the resource, update the values as necessary and PUT the representation back to the original URL.
Some fields are not writable, if you attempt to update a read-only field through the API, it will not update it and the response will still show the original value.

Writable fields: name, description, parent, isAlwaysAssignable, hasPermissions (when not top-level), isSelectedOnLoad, isBrowsable, showPromotedItems, showRecentItems.

Example:
[Using "al.json" in the previous example, modify one or more of the writable values,
e.g. name: "Docs", parent: "http://127.0.0.1:8081/asset-bank/rest/access-levels/4"]

```
curl -X PUT -H "Content-Type: application/json" -H "Accept: application/json" --data "@al.json" http://127.0.0.1:8080/asset-bank/rest/access-levels/1 > al_updated.json
```

Response (content of "al_updated.json"):
```
{
 "url": "http://127.0.0.1:8081/asset-bank/rest/access-levels/1",
 "id": 1,
 "name": "Docs",
 "description": "Description",
 "parent": "http://127.0.0.1:8081/asset-bank/rest/access-levels/4",
 "imageUrl": "http://127.0.0.1:8081/asset-bank/rest/access-levels/1/image",
 "isAlwaysAssignable": true,
 "hasPermissions": true,
 "isSelectedOnLoad": false,
 "isBrowsable": true,
 "showPromotedItems": false,
 "showRecentItems": false,
 "children": [
   {
     "url": "http://127.0.0.1:8081/asset-bank/rest/access-levels/7",
     "id": 7,
     "name": "MyDocs",
     "description": "Description",
     "parent": "http://127.0.0.1:8081/asset-bank/rest/access-levels/1",
     "imageUrl": "http://127.0.0.1:8081/asset-bank/rest/access-levels/7/image",
     "isAlwaysAssignable": true,
     "hasPermissions": false,
     "isSelectedOnLoad": false,
     "isBrowsable": true,
     "showPromotedItems": false,
     "showRecentItems": false,
     "children": [],
     "count": 0
   }
 ],
 "count": 0
}
```


## DELETE
Deletes the given Access Level. Returns a 204 "No Content" response back.
Returns a 400 "Bad Request" when the Access Level is not empty (either contains at least one asset or one child access level) and when it is a "static" Access Level which cannot be deleted.

Example:
```
curl -X DELETE http://127.0.0.1:8080/asset-bank/rest/access-levels/7
```

Response:
```
204 No Content
```
