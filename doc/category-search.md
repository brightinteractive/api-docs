# Category Search Resource
## GET
Searches for categories based on the given criteria.
categories that match the given criteria are returned along with their descendants.
The ‘Accept-Language’ http header may optionally be provided to get a particular translation of the category. If this is not provided or it is not a valid Asset Bank language code, the default language will be used.
Parameters
parentId (optional): Asset Bank id of the category to use as the root node of the tree search.
userId (optional): Asset Bank id of the user to restrict the returned tree to (i.e. only return categories that would be visible to this user if they logged in to Asset Bank). If omitted, the returned tree will be restricted by the permissions of the currently authenticated user (if using OAuth2), or the application user (otherwise).
count (optional): If true, include a count of the number of assets in each category in the response. If userId is specified then this count will be of the number of assets visible to the user specified. Note: retrieving counts may place a higher load on the server.

Example:
```
curl -X GET -H "Accept: application/json" 'http://127.0.0.1:8080/asset-bank/rest/category-search?userId=1' > tree.json
```

Response (contents of "tree.json" file):
```
[
    {
        "children": [
            {
                "children": [],
		   "parent":"http://127.0.0.1:8080/asset-bank/rest/categories/2",
                "description": null,
                "id": 128,
                "name": "Renaissance"
            },
            {
                "children": [],
                "parent":"http://127.0.0.1:8080/asset-bank/rest/categories/2",
                "description": null,
                "id": 129,
                "name": "Modern"
            }
        ],
        "description": null,
        "id": 2,
        "name": "Art"
    },
    {
        "children": [],
        "description": null,
        "id": 3,
        "name": "Concepts"
    },
    {
        "children": [],
        "description": null,
        "id": 4,
        "name": "Diagrams"
    },
    {
        "children": [],
        "description": null,
        "id": 5,
        "name": "Documents"
    }
]
```

Example (including counts):
```
curl -X GET -H "Accept: application/json" 'http://127.0.0.1:8080/asset-bank/rest/category-search?userId=1&count=true' > tree.json
```

Response (contents of "tree.json" file):
```
[
    {
        "children": [
            {
                "children": [],
                "description": null,
                "parent":"http://127.0.0.1:8080/asset-bank/rest/categories/2",
                "id": 128,
                "name": "Renaissance",
		  “count”: 1
            },
            {
                "children": [],
                "description": null,
                "parent":"http://127.0.0.1:8080/asset-bank/rest/categories/2",
                "id": 129,
                "name": "Modern",
		  “count”: 2
            }
        ],
        "description": null,
        "id": 2,
        "name": "Art",
	 “count”: 10,
    },
    {
        "children": [],
        "description": null,
        "id": 3,
        "name": "Concepts",
	 “count”: 0
    },
    {
        "children": [],
        "description": null,
        "id": 4,
        "name": "Diagrams",
	 “count”: 3
    },
    {
        "children": [],
        "description": null,
        "id": 5,
        "name": "Documents”,
	 “count”: 12
    }
]
```

Example (specifying language):
```
curl -X GET -H "Accept: application/json" -H "Accept-Language: fr" http://127.0.0.1:8080/asset-bank/rest/category-search
```
