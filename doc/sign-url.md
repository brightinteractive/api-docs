# URL Signing Resource
## POST
Sign a given API URL for use over a given timeframe.  Returns a signed version of that URL which can be handed to a third party client and used to access the Resource without requiring any other authentication. (e.g. IP based authentication.)
You need to provide a URL and an expiry duration (in seconds).  If the expiry duration given is 0, then the URL will always be signed for access, and will never expire.

Returns a 303 response, with the signed URL in the Location header.

```
curl -v -X POST -H "Content-type: application/json" --data '{"url": "http://example.com/asset-bank/rest/assets/17/content", "expirySeconds": 0}' http://example.com/asset-bank/rest/sign-url
```

Response:
```
303 See Other
Location: http://example.com/asset-bank/rest/assets/17/content?timestamp=0&key=211d6...
```
