# Asset Search Resource
## GET
Searches for assets based on criteria passed in request parameters. Some search parameters must be passed - the behaviour if no request parameters are passed is undefined and should not be relied upon (e.g. a 500 server error may be returned).
This is mostly a wrapper around Asset Bank's front-end search, i.e. the request parameters are similar. This means that the interface of this resource (e.g. the parameters it takes) is more likely to change than the interface of the other API resources.

To perform a search using the API you GET this resource’s URL with the required search parameters. The search parameters that can be passed are similar to those passed to the search action in Asset Bank so that is often a good place to start when identifying the parameters that you need to provide the API request.


### Attributes

```
attribute_{id}
```
Searching for assets with a particular attribute value is a case of providing a parameter with the name attribute_<id> and a value specifying what you want to search for (<id> needs to be replaced with the id of the attribute you want to search).
	
e.g.
```
http://127.0.0.1:8080/asset-bank/rest/asset-search?attribute_3=bridge
```

#### Advanced
For _text_ attributes, many of the search tips described on our [help centre article](https://support.assetbank.co.uk/hc/en-gb/articles/115005221048-Search-Tips) can be used here.

e.g.
```
http://127.0.0.1:8080/asset-bank/rest/asset-search?attribute_3=bridge+NOT+river
http://127.0.0.1:8080/asset-bank/rest/asset-search?attribute_3=bridge+OR+river
http://127.0.0.1:8080/asset-bank/rest/asset-search?attribute_3=bri*
http://127.0.0.1:8080/asset-bank/rest/asset-search?attribute_3=isempty
http://localhost:8080/asset-bank/rest/asset-search?attribute_3=*+NOT+isempty
```

### Other Criteria

<table class="standard-table">
  <thead>
    <tr>
      <th>Parameter</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>keywords</td>
      <td>Specifies one or more keywords to search for in attributes that have been marked as keyword searchable by an Asset Bank administrator. You can use the special search terms detailed in the above help centre article to construct compleex keyword searches (i.e. "red OR green OR blue")</td>
    </tr>
    <tr>
      <td>dateAddedLower</td>
      <td>ISO 8601 Date Time</td>
    </tr>
    <tr>
      <td>dateAddedUpper</td>
      <td>ISO 8601 Date Time</td>
    </tr>
    <tr>
      <td>dateModLower</td>
      <td>ISO 8601 Date Time</td>
    </tr>
    <tr>
      <td>dateModUpper</td>
      <td>ISO 8601 Date Time</td>
    </tr>
    <tr>
      <td>dateDownloadedLower</td>
      <td>ISO 8601 Date Time</td>
    </tr>
    <tr>
      <td>dateDownloadedUpper</td>
      <td>ISO 8601 Date Time</td>
    </tr>
    <tr>
      <td>sortAttributeId</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>sortDescending</td>
      <td>either true or false (false by default)</td>
    </tr>
    <tr>
      <td>assetIds</td>
      <td>either a single asset ID or a range of asset IDs (e.g. ‘1-10’ for ‘1 to 10’).
	    Valid values: {2-3}, {1}, 1, 2-3
	    Comma separated is not valid</td>
    </tr>
    <tr>
      <td>assetTypeId</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>filename</td>
      <td>&nbsp;</td>
    </tr>
    <tr>
      <td>orientation</td>
      <td>integer constant representing the desired orientation (1 = landscape, 2 = portrait, 3 = square, 0 = any)</td>
    </tr>
    <tr>
      <td>descriptiveCategoryForm.categoryIds</td>
      <td>ID of the category an asset must be in. To search across multiple categories provide multiple instances of the parameter e.g. descriptiveCategoryForm.categoryIds=1&amp;descriptiveCategoryForm.categoryIds=2. Please note specifying multiple parameter values will return all assets in one or more of the specified categories (i.e. an asset does not need to be in all of the specified categories to be included in the results).</td>
    </tr>
    <tr>
      <td>permissionCategoryForm.categoryIds</td>
      <td>ID of the access level an asset must be in. To search across multiple access levels provide multiple instances of the parameter e.g. permissionCategoryForm.categoryIds=1&amp;permissionCategoryForm.categoryIds=2. Please note specifying multiple parameter values will return all assets in one or more of the specified access levels. (i.e. an asset does not need to be in all of the specified access levels to be included in the results).</td>
    </tr>
    <tr>
      <td>includeImplicitCategoryMembers</td>
      <td>true or false indicating whether sub category members should be returned</td>
    </tr>
    <tr>
      <td>promoted</td>
      <td>true, false or both</td>
    </tr>
    <tr>
      <td>approvalStatuses</td>
      <td>if ‘full’ only fully approved assets will be returned, if ‘none’ then only assets which have not been approved will be returned and if omitted then assets in any approval state will be returned</td>
    </tr>
    <tr>
      <td>unsubmitted</td>
      <td>if true, only assets which have not been submitted for approval will be returned, if false only assets which have either been submitted and are awaiting approval or have been submitted and approved will be returned. If omitted assets in any submission state will be returned.</td>
    </tr>
    <tr>
      <td>userId or username</td>
      <td>specifies a user to constrain the search results to (i.e. returned results will be ones that the user in question has permission to see). If omitted, the results will be constrained by the permissions of the currently authenticated user (if using OAuth2), or the application user (otherwise).</td>
    </tr>
    <tr>
      <td>parentIds</td>
      <td>an id or list of ids to return locate child assets</td>
    </tr>
    <tr>
      <td>attributeQueryConjunction</td>
      <td>AND or OR. This controls how multiple attribute searches are combined. Determines whether an asset has to have all the selected attribute search values or any of them.  Defaults to AND.</td>
    </tr>
  </tbody>
</table>

The datetime fields should be url encoded using ISO 8601 Date Time.

Example

```
2018-09-24T10:56:55%2B01:00
```

By default the results are paged in batches of 100. A lower page size can be specified by supplying a pageSize parameter (pageSize=[requiredPageSize]). To select a particular page provide a page=[pagenumber] parameter.

Summary information about each asset is returned, not the full asset details (the reason for this is so that the data can be loaded exclusively from the search index, rather than having to load full asset data from the database). The attributes included are the same ones that are included in search results within the application; these can be changed in Admin -> Attributes -> Display Attributes -> Searching -> API Search results.

If an attribute is listed in the API Search results for the application, but is not being included in the response, you may need to run an online reindex of all assets (Admin -> Reindex Existing Assets). Please contact Asset Bank Support if the attribute continues to be excluded from the response following a reindex.

Note: The ‘approved’ field returned in the assets shown in the search results doesn’t support partial approval status resulting from assets being in multiple workflows. Assets approved in one workflow and unapproved in another will be shown as unapproved in the API.


Example:
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/asset-search?assetIds=14943
```


Response:
```
[
	{
		"id": 14943,
		"originalFilename":"filename.jpg",
		"fullAssetUrl": "http://127.0.0.1:8080/asset-bank/rest/assets/14943",
		"dateLastModifiedTimestamp": 1505483678000
		"approved": true,
		"previewUrl": "http://127.0.0.1:8080/asset-bank/servlet/display?
				file=8874ee565b95cb952d.jpg",
		"thumbnailUrl":"http://127.0.0.1:8080/asset-bank/servlet/display?
				file=95cb952d8874ee565b.jpg",
		"typeId": 1,
		"typeName": "Asset type name",
		"accessLevelIds": "1,2",
		"displayAttributes": [
			{
				"label":"Drawing Title",
				"value":"Test title"
			},
			{
				"label":"Description",
				"value":"Test description"
			}
		]
	}
]
```
