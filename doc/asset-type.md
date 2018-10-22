# Asset Type Instance Resource
## GET
Lists the details for the given asset type.

Example:
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/asset-types/2 > asset-types.json
```

Response (contents of "asset-types.json" file):
```
{
    "allowChildren": true,
    "allowPeers": false,
    "allowableAttributes": [
        {
            "attributeUrl": "http://127.0.0.1:8080/asset-bank/rest/attributes/1",
            "valueIfNotVisible": "",
            "visibleOnAdd": true
        },
        {
            "attributeUrl": "http://127.0.0.1:8080/asset-bank/rest/attributes/2",
            "valueIfNotVisible": "",
            "visibleOnAdd": true
        }        
    ],
    "allowableMediaTypes": [
        "File",
        "Image",
        "Video",
        "Audio"
    ],
    "canCopyAssets": false,
    "canDownloadChildrenFromParent": false,
    "categoryExtension": false,
    "childRelationshipFromName": "",
    "childRelationshipFromNamePlural": "",
    "childRelationshipToName": "child",
    "childRelationshipToNamePlural": "children",
    "childRelationships": [
        {
            "defaultRelationshipCategoryId": 0,
            "includeChildrenInDownload": false,
            "relatesToAssetTypeUrl": "http://127.0.0.1:8080/asset-bank/rest/asset-types/3",
            "relationshipDescriptionLabel": ""
        }
    ],
    "defaultCategoryId": 0,
    "excludedFileFormats": "",
    "id": 2,
    "includedFileFormats": "",
    "isArticle": false,
    "isQuickSearchable": false,
    "isSearchable": true,
    "matchOnAttributeUrl": null,
    "mustHaveParent": false,
    "name": "Digital Asset",
    "onlyAllowDefaultCategory": false,
    "peerRelationshipToName": "",
    "peerRelationshipToNamePlural": "",
    "peerRelationships": [],
    "restrictedAgreementId": 0,
    "rootCategoryId": 0,
    "showAttributeLabels": true,
    "showOnDescendantCategories": false,
    "termForSibling": "",
    "termForSiblings": "",
    "unrestrictedAgreementId": 0,
    "url": "http://127.0.0.1:8080/asset-bank/rest/asset-types/2"
}
```
