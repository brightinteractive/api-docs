# Pending Edit Approvals Resource
This Resource is for internal use only, and must not be used by regular API clients.
## GET
Returns a list of all assets awaiting edit approval. Each item in the list contains the instance resource URL for the unapproved asset and the approval URL for the unapproved asset (POSTing to this approves the edit)

Example:
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/pending-edit-approvals > pending-edit-approvals.json
```

Response (contents of "pending-edit-approvals.json" file):
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
userId (optional): Asset Bank id of the user to retrieve pending approvals for. Only asset edits the user can approve will be returned. If omitted all unapproved edits will be returned.
