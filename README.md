API Docs
========

All endpoints available are documented below, although some are intended for internal use only.

There is a [Postman](https://www.getpostman.com/) collection available [here](https://github.com/brightinteractive/api-docs/tree/master/postman) which is gradually being expanded.


Authentication
--------------

API requests should be authenticated using an OAuth 2.0 Bearer token in the **Authorization** header. To see a sample app that obtains the OAuth token and uses it to call the API, click [here](https://github.com/brightinteractive/sample-oauth-app).

How to ....
-----------

[Upload a new asset](doc/how-to-upload.md)

Endpoints
---------

| URL Name | Methods allowed |
| ------------- | -----:|
| [rootUrl](doc/root.md) | GET |
| [/access-levels/{id}/image](doc/access-level-image.md) | GET, PUT, DELETE |
| [/access-level-search](doc/access-level-search.md) | GET |
| [/access-levels](doc/access-levels.md) | GET, POST, PUT, DELETE |
| [/checkout](doc/checkout.md) | GET, PUT |
| [/assets/{id}/content](doc/content.md) | GET, PUT |
| [/assets/{id}/conversion](doc/conversion.md) | GET |
| [/asset-search](doc/asset-search.md) | GET |
| [/assets](doc/assets.md) | POST |
| [/assets/{id}](doc/asset.md) | GET, PUT, DELETE |
| [/asset-types](doc/asset-types.md) | GET |
| [/asset-types/{id}](doc/asset-type.md) | GET |
| [/assets/{id}/approve](doc/approve.md) | POST |
| [/attributes](doc/attributes.md) | GET |
| [/list-attribute-values](doc/list-attribute-values.md) | GET, POST |
| [/list-attribute-values/{id}](doc/list-attribute-value.md) | GET |
| [/authenticated-user](doc/authenticated-user.md) | GET |
| [/categories](doc/categories.md) | GET |
| [/categories/{id}](doc/category.md) | GET |
| [/category-search](doc/category-search.md) | GET |
| [/display-attribute-group](doc/display-attribute-groups.md) | GET |
| [/display-attribute-group/{id}](doc/display-attribute-group.md) | GET |
| [/assets/{id}/editor-dependencies](doc/editor-dependencies.md) | GET |
| [/embedded-data-mappings](doc/embedded-data-mappings.md) | GET |
| [/embedded-data-mappings/{id}](doc/embedded-data-mapping.md) | GET |
| [/keywords](doc/keywords.md) | GET |
| [/keywords/{id}](doc/keyword.md) | GET |
| [/users/{id}/lightboxes](doc/lightboxes.md) | GET, POST |
| [/users/{id}/lightboxes/{id}](doc/lightbox.md) | GET, POST, DELETE |
| [/pending-upload-approvals](doc/pending-upload-approvals.md) | GET |
| [/assets/{id}/content-save-status](doc/content-save-status.md) | GET |
| [/publishing-actions](doc/publishing-actions.md) | POST |
| [/publishing-actions/{id}](doc/publishing-action.md) | GET |
| [/publishing-actions/{id}/log](doc/publishing-actions-log.md) | GET |
| [/temp-chunked-files](doc/temp-chunked-files.md) | POST |
| [/temp-chunked-files/{id}](doc/temp-chunked-file.md) | GET, DELETE |
| [/temp-chunked-files/{id}/{number}](doc/temp-chunk.md) | PUT |
| [/sign-url](doc/sign-url.md) | POST |
| [/user-search](doc/user-search.md) | GET |
| [/users](doc/users.md) | GET, POST, DELETE |
| [/users/{id}](doc/user.md) | GET, PUT |
