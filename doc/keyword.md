# Keyword Instance Resource
## GET
Lists the details for the given keyword

Example:
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/attributes/701/keywords/1 > keywords.json
```

Response (contents of "keywords.json" file):
```
{
	 "url":"http://127.0.0.1:8080/asset-bank/rest/attributes/701/keywords/1",
	 "id":1,
	 "name":"Animals",
	 "synonyms":"Organism",
	 "children":[{
		 "url":"http://127.0.0.1:8080/asset-bank/rest/attributes/701/keywords/2",
		 "id":2,
		 "name":"Cats",
		 "synonyms":"Felines",
		 "parent":"http://127.0.0.1:8080/asset-bank/rest/attributes/701/keywords/1"

}
```
