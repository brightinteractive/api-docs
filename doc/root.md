# API Root Resource
## GET
The Root of Asset Bank's Jersey-based RESTful API. A GET request on this resource returns a dictionary containing versioned links to the various sub-components of the API.

This resource does not directly link to paremeterised resources, to get to them you must follow the links provided there. For example to find the URL of a publishing action resource you need to POST the publishing action ID to the publishing actions base resource (listed here in the root resource under "publishingActionsUrl") - see the documentation for the publishing actions base resource for details.
Example:

Note that some of the links provided here are to, internal-use-only resources that may be removed at any time. Before using a resource please make sure that it is included in the REST API documentation and not marked as internal use only.

Example:

```curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/```

Response:

```javascript
{
    "api_name":"AssetBank RESTful API",

    "api_version_1_1":
    {
        "checkoutUrl": "http://127.0.0.1:8080/asset-bank/rest/checkout",
        "lightboxesUrl": "http://127.0.0.1:8080/asset-bank/rest/v1.1/lightboxes",
        "assetsUrl": "http://127.0.0.1:8080/asset-bank/rest/v1.2/assets",
        "signingUrl": "http://127.0.0.1:8080/asset-bank/rest/sign-url"
    },

    "api_version_1_2":
    {
        "checkoutUrl": "http://127.0.0.1:8080/asset-bank/rest/checkout",
        "lightboxesUrl": "http://127.0.0.1:8080/asset-bank/rest/lightboxes",
        "assetsUrl": "http://127.0.0.1:8080/asset-bank/rest/v1.2/assets",
        "usersUrl": "http://127.0.0.1:8080/asset-bank/rest/users",
        "userSearchUrl": "http://127.0.0.1:8080/asset-bank/rest/user-search",
        "attributesUrl": "http://127.0.0.1:8080/asset-bank/rest/attributes",
        "categorySearchUrl": "http://127.0.0.1:8080/asset-bank/rest/category-search",
        "accessLevelSearchUrl": "http://127.0.0.1:8080/asset-bank/rest/access-level-search",
        "signingUrl": "http://127.0.0.1:8080/asset-bank/rest/sign-url",
        "assetSearchUrl": "http://127.0.0.1:8080/asset-bank/rest/asset-search",
        "publishingActionsUrl": "http://127.0.0.1:8080/asset-bank/rest/publishing-actions"
    },
    "api_version_1_3": {
        "accessLevelSearchUrl": "http://127.0.0.1:8080/asset-bank/rest/access-level-search", 
        "assetSearchUrl": "http://127.0.0.1:8080/asset-bank/rest/asset-search", 
        "assetsUrl": "http://127.0.0.1:8080/asset-bank/rest/assets", 
        "attributesUrl": "http://127.0.0.1:8080/asset-bank/rest/attributes", 
        "categorySearchUrl": "http://127.0.0.1:8080/asset-bank/rest/category-search", 
        "checkoutUrl": "http://127.0.0.1:8080/asset-bank/rest/checkout", 
        "displayAttributeGroupUrl": "http://127.0.0.1:8080/asset-bank/rest/display-attribute-groups", 
        "editorDependenciesUrl": "http://127.0.0.1:8080/asset-bank/rest/editor-dependencies", 
        "lightboxesUrl": "http://127.0.0.1:8080/asset-bank/rest/lightboxes", 
        "publishingActionsUrl": "http://127.0.0.1:8080/asset-bank/rest/publishing-actions", 
        "signingUrl": "http://127.0.0.1:8080/asset-bank/rest/sign-url", 
        "userSearchUrl": "http://127.0.0.1:8080/asset-bank/rest/user-search", 
        "usersUrl": "http://127.0.0.1:8080/asset-bank/rest/users"
    }
}
```



