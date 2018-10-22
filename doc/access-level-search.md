## Access Level Search Resource
# GET

Searches for access levels based on the given criteria.
Access levels that match the given criteria are returned along with their descendants.
The ‘Accept-Language’ http header may optionally be provided to get a particular translation of the category. If this is not provided or it is not a valid Asset Bank language code, the default language will be used.
Parameters
parentId (optional): Asset Bank id of the access level to use as the root node of the tree search.
userId (optional): Asset Bank id of the user to restrict the returned tree to (i.e. only return access levels that would be visible to this user if they logged in to Asset Bank). If omitted, the returned tree will be restricted by the permissions of the currently authenticated user (if using OAuth2), or the application user.
count (optional): true or false parameter to determine whether to include the asset count for the requested access levels, if a userId has been provided counts returned will be restricted to assets visible to the selected user, otherwise it will be the full count of all assets in the access levels. Note: retrieving counts may place a higher load on the server.

Example:
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/access-level-search > tree.json
```

Response (contents of "tree.json" file):
```
[
        {"id":"2","name":"Art","children":[
                {"id":"27",
    "parent":"http://127.0.0.1:8080/asset-bank/rest/categories/2",
                 "name":"Modern"},
   {"id":"28",
"parent":"http://127.0.0.1:8080/asset-bank/rest/categories/2",      "name":"Renaissance"}]
        },
        {"id":"3","name":"Concepts"},
        {"id":"4","name":"Diagrams"},
        {"id":"5","name":"Documents"},
        {"id":"6","name":"Events"},
        {"id":"7","name":"Graphics"},
        {"id":"8","name":"Logos","children":[
                {"id":"29",
    "parent":"http://127.0.0.1:8080/asset-bank/rest/categories/8",
                 "name":"Coporate"},
                {"id":"30",
    "parent":"http://127.0.0.1:8080/asset-bank/rest/categories/8",
                 "name":"Charity"},
                {"id":"31",
    "parent":"http://127.0.0.1:8080/asset-bank/rest/categories/8",
                 "name":"Club"}]
        },
        {"id":"9","name":"People"},
        {"id":"10","name":"Publications"},
        {"id":"11","name":"Screenshots"},
        {"id":"12","name":"Video clips"}
]
```

Example (specifying language):
```
curl -X GET -H "Accept: application/json" -H "Accept-Language: fr" http://127.0.0.1:8080/asset-bank/rest/access-level-search
```
