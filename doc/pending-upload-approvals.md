# Pending Upload Approvals Resource
This Resource is for internal use only, and must not be used by regular API clients.
## GET
Returns a list of all assets awaiting upload approval. Each item in the list contains the instance resource URL for the unapproved asset and the approval URL for the unapproved asset (POSTing to this approves the upload)

Example:
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/pending-upload-approvals > pending-upload-approvals.json
```

Response (contents of "pending-upload-approvals.json" file):
```
[
	{
"assetInstanceUrl" : "http://127.0.0.1:8080/asset-bank/rest/assets/1",
"assetApprovalUrl" : "http://127.0.0.1:8080/asset-bank/rest/assets/1/approve"}
},
{
"assetInstanceUrl" : "http://127.0.0.1:8080/asset-bank/rest/assets/2",
"assetApprovalUrl" : "http://127.0.0.1:8080/asset-bank/rest/assets/2/approve"}
}
]
```

Parameters
userId (optional): Asset Bank id of the user to retrieve pending approvals for. Only asset uploads the user can approve will be returned. If omitted, the pending approvals for the currently authenticated user will be returned (if using OAuth2), or all unapproved uploads will be returned (if using IP restrictions).
