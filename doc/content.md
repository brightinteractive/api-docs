# Asset Content Resource
## GET
This resource doesn't serve the asset content directly. Instead it returns a 303 redirect to a signed URL which serves the content.
This URL will either be an S3 URL or an Asset Bank file servlet URL depending on where the asset file is stored.

Example:
```
curl -L -X GET -H "Accept: application/octet-stream" http://127.0.0.1:8080/asset-bank/rest/assets/1/content > output.dat
```

Response:
```
303 See Other
```
## PUT
Update the file content for a given asset.  The filename must be set using the Content-Disposition header.  The Content-Type header should be set to "application/octet-stream".

The file content can either come from the request body, or from a temp chunked file that has been uploaded previously. If an X-Copy-Temp-Chunked-File header is present then that temp chunked file’s content will be used, if not then the request body will be used.
By default, the resource replaces the existing file content for the given asset. However, it can also be used to create a new version of the given asset by adding an Upload-As-New-Version header and setting this to “true”.
Note that after a temp chunked file has been copied to an asset’s contents then the temp chunked file will still remain on disk until it is DELETEd (or is cleaned up by a scheduled job), so it is recommended that clients DELETE temp chunked files after they have been used to prevent the Asset Bank server from running out of disk space.
Returns a 200 OK response with no content.
### Parameters
**userId** (optional): Asset Bank id of the user to update the asset file content as. The user must have edit permission on the asset. If omitted, the asset will be updated by the currently authenticated user (if using OAuth2), or the application user.
When acting as a user who is not the application user, the user must have the appropriate permission to edit the asset. If not the PUT will be refused. If the user has only edit with approval permission on the asset then it will go through the standard approval process and the new asset file will need to be approved before being visible to other users.

**extractEmbeddedData** (optional, defaults to false): whether to extract embedded metadata from the asset file. When true this option will allow to populate the asset attributes based on the "embedded data mappings" configuration.

*NB Implementation detail:* This also represents the behaviour of PrecursorFileResource, in a way that is transparent to the client.
The POST method is also supported, for internal use only.  In the case of a PrecursorFileResource a POST request will result in a 202 Accepted response, linking to a Precursor File Save Status Resource.


Example (single-part content in request body):
```
curl -v -X PUT -T /path/to/example.dat -H "Content-Type: application/octet-stream" -H "Content-Disposition: attachment; filename=68.jpg" http://127.0.0.1:8080/asset-bank/rest/assets/1/content
```

Response:
```
200 OK
```

Example (get content from a previously-uploaded temp chunked file):
```
curl -v -X PUT -T /path/to/example.dat -H "Content-Type: application/octet-stream" -H "Content-Disposition: attachment; filename=68.jpg" -H "X-Copy-Temp-Chunked-File: http://127.0.0.1:8080/asset-bank/rest/temp-chunked-files/067e6162-3b6f-4ae2-a171-2470b63d" http://127.0.0.1:8080/asset-bank/rest/assets/1/content
```

Response:
```
200 OK
```


# Asset Content URL Resource
## GET
The above asset content resource doesn't serve the asset content directly, instead it returns the URL that serves the content in the body of a 200 response.
This is a convenience resource for callers who don't want to immediately read the content but instead pass the signed URL onto something else that will.

Example:
```
curl -X GET http://127.0.0.1:8080/asset-bank/rest/assets/1/content/url
```

```
200 OK
Location: https://assetbank.s3-eu-west-1.amazonaws.com/7dd/file.txt?response-content-disposition=attachment%3B%20filename%3D%22file.txtX-Amz-Signature=ad084ed9176a2
```
