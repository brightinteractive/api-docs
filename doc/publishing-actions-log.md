# Publishing Action Log Resource
## GET
A GET request to this resource returns the Ids of all the assets that have had files published or unpublished by the specified Publishing Action since the last time the resource was called (by a particular caller) for that Publishing Action. A token called startSequence is used to keep track of the information that has already been returned by previous calls.

As well as the asset Ids, the resource will return a startSequence that should be passed the next time it is called for the specified Publishing Action. The first time that the resource is called for a particular action a startSequence with a value of 0 should be passed. This will cause the resource to return the entire log for that Publishing Action.

The token startSequence is used instead of dates and times to avoid problems if the clocks of the Asset Bank server and the client are not synchronised.


Example:
```
curl -X GET -H "Accept: application/json" http://127.0.0.1:8080/asset-bank/rest/publishing-actions/5/log?startSequence=4567000
```

Response:
```
{
        "events": [
                {
                        "assetId": 123,
                        "type": "PUBLISH"
                },
                {
                        "assetId": 456,
                        "type": "UNPUBLISH"
                }
        ],
        "nextStartSequence": 4567890
}
```
