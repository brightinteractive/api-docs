# How to respond to file changes in Asset Bank
- Make a request to get all assets modified.
- Store timestamp of last successful response.
- Schedule subsequent requests to get all assets modified since the last successful response.

## At 10:05 get all Assets modified since 10:00 20-12-2021
Example (JSON):
```
curl -X GET -H "Accept: application/json" https://127.0.0.1:8080/asset-bank/rest/asset-search?dateModLower=2020-12-20T10:00:00%2B01:00
```
Response: 
```
[
	{
		"id": 14943,
		"originalFilename":"filename.jpg",
		"fullAssetUrl": "http://127.0.0.1:8080/asset-bank/rest/assets/14943",
		"dateLastModifiedTimestamp": 1505483678000
		...
	},
{
		"id": 14944,
		"originalFilename":"filename.jpg",
		"fullAssetUrl": "http://127.0.0.1:8080/asset-bank/rest/assets/14943",
		"dateLastModifiedTimestamp": 1505483678000
		...
	}
	
]
```
Your application may now refresh any changed files or metadata using the API.

## After 5 minutes at 10:10, get all Assets modified since 10:05
Example (JSON):
```
curl -X GET -H "Accept: application/json" https://127.0.0.1:8080/asset-bank/rest/asset-search?dateModLower=2020-12-20T10:05:00%2B01:00
```
Response: 
```
[
	{
		"id": 14863,
		"originalFilename":"filename.jpg",
		"fullAssetUrl": "http://127.0.0.1:8080/asset-bank/rest/assets/14943",
		"dateLastModifiedTimestamp": 1505483678000
		...
	}	
]
```
Your application may now refresh any changed files or metadata using the API.

