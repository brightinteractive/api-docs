# Asset Conversion Resource
## GET
This resource serves a converted version of the asset.

Example:
```
curl -X GET -H "Accept: application/octet-stream" http://127.0.0.1:8080/asset-bank/rest/assets/1/conversion > image.jpg
```

The following parameters can be supplied to get a resized or cropped version of the asset.

- width (optional) - defaults to the same width as original
- height (optional) - defaults to the same height as original
- preserveAspectRatio (optional)
- preserveColorSpace (optional)
- cropToFit (optional) - this defaults to true  
- offsetX (optional) - when cropping, select where to crop on X axis - defaults to select the centre of the image
- offsetY (optional) - when cropping, select where to crop on Y axis - defaults to select the centre of the image
- format (optional) - the image format to retrieve (valid values are: jpg, gif or png).
- fillBackground (optional) - fill the background of the bounding box if cropToFit=false
- fillBackgroundColour (optional) - specify the background fill colour in hexadecimal - six characters are required but no hash character, e.g. black would be fillBackgroundColour=000000

Example:
```
curl -X GET -H "Accept: application/octet-stream" http://127.0.0.1:8080/asset-bank/rest/assets/1/conversion?width=100&height=100 > image.jpg
```
