# Assets Base Resource
## POST
Creates a new asset and returns a 201 created response, linking to an Asset Instance Resource.  The asset created has no associated data except the supplied access levels and the specified asset type (if asset types are enabled in the Asset Bank). As such you will subsequently need to issue a PUT request to the Asset Instance Resource to set asset metadata (attributes) and to issue a PUT request to the Asset Content Resource to upload the asset content.

The access levels are supplied in the same format that the Access Level Search Resource returns them, although you only need to populate the id field (not name, children or description). You may populate these other fields if you like, for example if you are sending data that was originally obtained from the Access Level Search Resource, but all fields except id will be ignored.

If asset types are enabled in the Asset Bank you are POSTing to you must specify the asset type of the asset you are creating by providing the URL of a valid asset type resource. The URL is the same as that returned by the Asset Type Base Resource (when listing all asset types) and that included in url field when doing a GET on an Asset Type Instance Resource.

The create asset request can optionally contain a user id of the user to act as when creating the asset. If omitted, the asset will be created by the currently authenticated user (if using OAuth2), or the application user (otherwise).

When acting as a user who is not the application user, the user must have the appropriate permission to create an asset in the provided access levels. If not the POST will be refused. If the user has only upload with approval permission on one or more of the access levels then once submitted the asset will need to go through the standard approval process before it is visible to other users. Note, the asset can be submitted immediately when created (see below) or via a PUT to the Asset Instance Resource.

The create asset request can also optionally contain a flag to indicate whether to submit the asset to live when created (i.e. so it is immediately visible to asset bank users). If omitted the asset will be submitted to live.

Example (JSON):
```
curl -v -X POST -H "Content-type: application/json" --data '{"accessLevels": [{"id":5}, {"id": 1}], "createAsUserId" : "10", "submit" : "false", "assetTypeUrl": "http://127.0.0.1:8080/asset-bank/rest/asset-types/2"}' http://127.0.0.1:8080/asset-bank/rest/assets
```

Response:  
```
201 Created
Location: http://127.0.0.1:8080/asset-bank/rest/assets/16
```

Example (XML):
```
curl -v -X POST -H "Content-type: application/xml" --data '<?xml version="1.0" encoding="UTF-8" standalone="yes"?><createAsset><accessLevels><accessLevel><id>1</id></accessLevel><accessLevel><id>13</id></accessLevel></accessLevels><createAsUserId>10</createAsUserId><submit>true</submit><assetTypeUrl>"http://127.0.0.1:8080/asset-bank/rest/asset-types/2</assetTypeUrl></createAsset>' http://127.0.0.1:8080/asset-bank/rest/assets
```

Response:
```
201 Created
Location: http://127.0.0.1:8080/asset-bank/rest/assets/3309
```

If you do not supply any access levels then a 400 Bad Request response will be returned:

Example (bad request - no access levels):
```
curl -v -X POST http://127.0.0.1:8080/asset-bank/rest/assets
```

Response:
```
400 Bad Request
Content-Type: text/plain

You must supply some access levels to put the asset in when creating an asset.
```

If asset types are enabled in the Asset Bank you are POSTing to and you do not specify an asset type then a 400 Bad Request response will be returned:

Example (bad request - no access levels):
```
curl -v -X POST http://127.0.0.1:8080/asset-bank/rest/assets
```

Response:  
```
400 Bad Request
Content-Type: text/plain

You must provide an asset type.
```

Previous versions of the API allowed assets to be created without access levels and relied on the API client always supplying some access levels in a subsequent PUT to the Asset Instance Resource.  This was problematic because Asset Bank assumes that all assets are in at least one access level and behaves strangely when an asset has no access levels. The new design prevents problematic assets with no access levels from being created.
