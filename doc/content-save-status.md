# Precursor File Save Status Resource

This Resource is for internal use only, and must not be used by regular API clients.
## GET
Returns the status of the last save of an asset content resource if the asset is one where the main file is generated asynchronously from a precursor file, which is very rare (only InDesign Server Plugin assets at the time of writing, not Simple InDesign Plugin assets).
Returns 404 not found for other assets.

Example (read the status of an asset's content that was saved successfully):
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/assets/5/content-save-status/
```

Response :
```
{"successful": ""}
```

Example (read the status of an asset's content that is in the process of being saved):
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/assets/5/content-save-status/
```

Response :
```
{"pending": ""}
```

Example: (read the status of an asset's content that failed, i.e. an error occurred)
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/assets/5/content-save-status/
```

Response :
```
{"failure": "The file was not saved because..."}
```
