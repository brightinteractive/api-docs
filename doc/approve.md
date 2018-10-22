
# Asset Approval Resource
This Resource is for internal use only, and must not be used by regular API clients.
## POST
Approves the specified asset.
Returns a 200 OK response with no content.
Parameters  
userId (optional): Asset Bank id of the user to approve the asset as. The user must have approval permission on the asset. If omitted the asset will be approved as the application user.


Example:
```
curl -X POST http://127.0.0.1:8080/asset-bank/rest/assets/1/approve
```

Response:
```
200 OK
```
