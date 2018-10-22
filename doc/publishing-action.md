# Publishing Action Instance Resource
## GET
A GET request on this resource returns information about a publishing action.

Example:
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/publishing-actions/1
```

Response:
```
{
    "logUrl": "http://127.0.0.1:8080/asset-bank/rest/publishing-actions/1/log"
}
```
