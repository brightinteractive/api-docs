# Publishing Actions Base Resource
## POST
POSTing a PublishingActionId to this resource returns a See Other response, referring to a Resource which can be used to get information about a particular publishing action.

Example:
```
curl -v -X POST -H "Content-type: application/json" --data '{"publishingActionId":5}' http://127.0.0.1:8080/asset-bank/rest/publishing-actions
```

Response:
```
HTTP/1.1 303 See Other
Location: http://127.0.0.1:8080/asset-bank/rest/publishing-actions/5
```
