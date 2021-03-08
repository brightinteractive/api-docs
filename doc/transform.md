# Asset Transform Resource
## GET
This resource serves a transformed version of the asset.

Example:
```
curl -X GET -H "Accept: application/octet-stream" http://127.0.0.1:8080/asset-bank/rest/assets/1/transform > image.jpg
```

The following parameters can be supplied to get a converted or resized version of the asset.

- width (optional) - defaults to 1000
- height (optional) - defaults to 1000
- extension (optional) - defaults to webp (valid values are: jpg, png, gif or webp)

The response will be a HTTP 303 redirect to the file.

Example:
```
curl -vLJ -o image.webp -H 'Accept: application/octet-stream' http://127.0.0.1:8080/asset-bank/rest/assets/21/transform?width=200&height=200&extension=webp
```
