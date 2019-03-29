# How to upload a new Asset

The following steps are required:

- Create new Asset
- Upload file content into asset
- Update attribute metadata

## Create new asset

Example (JSON):
```
curl -v -X POST -H "Content-type: application/json" --data 
'
{
  "accessLevels": [{"id": 1}], 
  "createAsUserId" : "1", 
  "submit" : "false", 
  "assetTypeUrl": "http://127.0.0.1:8080/asset-bank/rest/asset-types/2"
}
' http://127.0.0.1:8080/asset-bank/rest/assets
```

Response:  
```
201 Created
Location: http://127.0.0.1:8080/asset-bank/rest/assets/16
```

See [assets documentation](doc/assets.md).

## Upload Content

Example (JSON):
```
curl -v -X PUT -T /path/to/example.dat 
-H "Content-Type: application/octet-stream" 
-H "Content-Disposition: attachment; filename=68.jpg" 
http://127.0.0.1:8080/asset-bank/rest/assets/1/content
```

Response:
```
200 OK
```

See [asset documentation](doc/asset.md).

## update asset metadata

Example (JSON):
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/assets/1
```

Response:
```
{
  "attributes": [
    {
      "id": "8",
      "name": "dateAdded",
      "value": "17/03/2011 16:05:02"
    },
    {
      "id": "6",
      "name": "originalFilename",
      "value": "1.jpg"
    }
    {
      "id": "9",
      "name": "title",
      "value": "An oak tree"
    },
    <...ETC...>
  ],
  "parents":["http://127.0.0.1:8080/asset-bank/rest/assets/10"],
  "submitted": false,
  "url": "http://127.0.0.1:8080/asset-bank/rest/assets/1",
  "contentUrl": "http://127.0.0.1:8080/asset-bank/rest/assets/1/content",
  "displayUrl": "http://127.0.0.1:8080/asset-bank/rest/assets/1/display",
  "thumbnailUrl": "http://127.0.0.1:8080/asset-bank/servlet/display?file=9ab.jpg",
  "previewUrl": "http://127.0.0.1:8080/asset-bank/servlet/display?file=9cd.jpg",
  "conversionUrl": "http://127.0.0.1:8080/asset-bank/rest/assets/1/conversion",
  "unwatermarkedLargeImageUrl": "http://127.0.0.1:8080/asset-bank/servlet/display?file=8a8.jpg",
  "approved": true
}
```

See [content documentation](doc/content.md).
