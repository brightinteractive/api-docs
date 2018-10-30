# Editor Dependencies Resource
This Resource is for internal use only, and must not be used by regular API clients.

## GET
  Returns a primary URL for the asset, and optionally a list of secondary URLs.

  The primary URL is the main file that must be downloaded in order for the asset to be edited locally.  It is assumed that the client will be able both to download and upload to the primary URL.  Uploading to the primary URL is used to save the asset content after it has been edited locally.

  The secondary URLs are files that must also be downloaded in order for the asset to be edited locally.  It is assumed the secondary URLs are download-only URLs.  Saving the file to the API after a local edit does not require the secondary files to be uploaded.

  The primary URL and secondary URLs are often, but not always, links to an Asset Content Resource.

Example:
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/assets/5/editor-dependencies
```

Response:
```
{
  "primaryUrl": "http://127.0.0.1:8080/asset-bank/rest/assets/5/content"
}
```
