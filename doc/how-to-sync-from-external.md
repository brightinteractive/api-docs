# How to synchronise assets in Asset Bank from an external source

It's a common requirement where a separate system like a PIM is the source of assets and you want to ensure that Asset Bank is kept updated when changes are made.

In this case there will a unique identifier for each asset from the source system e.g. 'PIM10001'

In Asset Bank you create a new attribute e.g. 'PIM Identifier' which will be assigned an Asset Bank attribute ID e.g. '704'

## Creating new Assets

The process to create a new asset will follow the standard [upload process](how-to-upload.md).

Ensure that the metadata external unique identifier has been populated.
```
{
  "attributes": [
    {
      "id": "704",
      "name": "PIMIdentifier",
      "value": "PIM10001"
    },
    ...
  ],
  ...
}
```

## Updating Assets

To update an asset in Asset Bank the caller will require the Asset ID.
```
http://127.0.0.1:8080/asset-bank/rest/asset-search?attribute_704=PIM10001
```

Response
```
[
	{
		"id": 123456,
    ...
	}
]
```
### Update asset file
Using the Asset ID, the file data can be updated.
Example (single-part content in request body):
```
curl -v -X PUT -T /path/to/new_file.pdf -H "Content-Type: application/octet-stream" -H "Content-Disposition: attachment; filename=new_file.jpg" http://127.0.0.1:8080/asset-bank/rest/assets/123456/content
```
Response
```
200 OK
```

### Update metadata
Using the Asset ID, the metadata can be updated via PUT using the standard [attribute update call](asset.md).

