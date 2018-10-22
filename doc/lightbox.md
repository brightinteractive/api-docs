# Lightbox Instance Resource
## GET
Returns details for the given lightbox.

Example:
```
curl -X GET http://127.0.0.1:8080/asset-bank/rest/users/1/lightboxes/1 -H "Accept: application/json" > lightbox.json
```

Response (contents of "lightbox.json" file):
```
{
"id": 1,
"name": "My Lightbox",
"size": 3,
 	"lightboxContentsUrl": "http://127.0.0.1:8080/asset-bank/rest/users/1/lightboxes/1/contents",
 	"lightboxContentsUrl": "http://127.0.0.1:8080/asset-bank/rest/users/1/lightboxes/1/contents",
	"lightboxPublicUrl":  "http://127.0.0.1:8080/asset-bank/action/viewPublicAssetBox?assetBoxId=1",
}
```


Lightbox Contents Resource
## GET
Returns the contents of a given lightbox.
Each asset will represent an individual asset in the lightbox, and will contain a list of attributes for that asset, and a link to an Asset Instance Resource.
Each attribute of each asset will contain an id, a name and a value.

Example:
```
curl -X GET http://127.0.0.1:8080/asset-bank/rest/users/1/lightboxes/1/contents -H "Accept: application/json"
```

Response:
```
[
  {
    "attributes": [
      {
        "id": "8",
        "label": "dateAdded",
        "value": "17/03/2011 16:05:02"
      },
      {
        "id": "6",
        "label": "originalFilename",
        "value": "1.jpg"
      },
      <...ETC...>
    ],
    "assetInLightboxUrl":
      "http://127.0.0.1:8080/asset-bank/rest/users/1/lightboxes/1/contents/1",
    "contentUrl": "http://127.0.0.1:8080/asset-bank/rest/assets/1/content",
    "displayUrl": "http://127.0.0.1:8080/asset-bank/rest/assets/1/display",
    "thumbnailUrl": "http://127.0.0.1:8080/asset-bank/servlet/display?file=9ab.jpg",
    "previewUrl": "http://127.0.0.1:8080/asset-bank/servlet/display?file=9cd.jpg",
    "unwatermarkedLargeImageUrl":
      "http://127.0.0.1:8080/asset-bank/servlet/display?file=8a8.jpg",
    "url": "http://127.0.0.1:8080/asset-bank/rest/assets/1",
    "approved": "true"
  },
  {
    "attributes": [
      {
        "id": "8",
        "name": "dateAdded",
        "value": "17/03/2011 14:33:50"
      },
      {
        "id": "6",
        "name": "originalFilename",
        "value": "2.jpg"
      },
      <...ETC...>
    ],
    "assetInLightboxUrl":
      "http://127.0.0.1:8080/asset-bank/rest/users/1/lightboxes/1/contents/2",
    "contentUrl": "http://127.0.0.1:8080/asset-bank/rest/assets/2/content",
    "displayUrl": "http://127.0.0.1:8080/asset-bank/rest/assets/2/display",
    "thumbnailUrl": "http://127.0.0.1:8080/asset-bank/servlet/display?file=134a.jpg",
    "previewUrl": "http://127.0.0.1:8080/asset-bank/servlet/display?file=a431.jpg",
    "unwatermarkedLargeImageUrl":
      "http://127.0.0.1:8080/asset-bank/servlet/display?file=b21c.jpg",
    "approved": "true"
  }
]
```

## POST
Adds the given asset to the given lightbox. As with all URLs in this API clients should look up the URL (in this case by navigating to the User Lightboxes Resource and examining the  "lightboxContentsUrl" property) and must not hard-code the URL format (hard coding the URL format will result in API clients breaking when used with newer versions of Asset Bank).

Example (add the asset with id 2 to the lightbox with id 1 owned by user with ID 1):
```
curl -X POST -H "Content-type: application/json" --data '{"url":"http://127.0.0.1:8080/asset-bank/rest/assets/2"}' -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/users/1/lightboxes/1/contents
```

Response:
```
201 Created
Location: http://127.0.0.1:8080/asset-bank/rest/users/1/lightboxes/1/contents/2
```

Asset In Lightbox Resource
## GET
Returns links to the Asset Instance Resource and Lightbox Instance Resource

Example:
```
curl -X GET http://127.0.0.1:8080/asset-bank/rest/users/1/lightboxes/1/contents/2
 -H "Accept: application/json"
 ```

Response:
```
200 OK

{
"assetInstanceUrl": "http://127.0.0.1:8080/asset-bank/rest/assets/2",
 	"lightboxInstanceUrl": "http://127.0.0.1:8080/asset-bank/rest/users/1/lightboxes/1"
}
```

## DELETE
Removes an asset from a lightbox
Example:
```
curl -X DELETE http://127.0.0.1:8080/asset-bank/rest/users/1/lightboxes/1/contents/2
 -H "Accept: application/json"
 ```

Response:
```
204 No Content
```

Note: the status code is 204 not 200 because http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html states that the response should be "204 (No Content) if the action has been enacted but the response does not include an entity"
