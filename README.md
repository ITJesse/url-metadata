# [wip] url-metadata
Request an http url and scrape its metadata. Many of the metadata fields returned are [Open Graph Protocol (og:)](http://ogp.me/) so far.

## Usage

### Install via npm to use in Node.js project
`npm install url-metadata --save`

Then in your project:
```
const urlMetadata = require('urlMetadata')
urlMetadata('http://bit.ly/2ePIrDy', options).then(
  function (metadata) { // success handler
    console.log(metadata)
  },
  function (error) { // failure handler
    console.log(error)
  })
```

### Options
Defaults to values below:
```
{
  userAgent: 'LevelBot', // name the bot that will make url request
  fromEmail: 'vision@levelnews.org', // your email
  maxRedirects: 8,
  encoding: 'utf8',
  timeout: 10000, // 10 seconds
  descriptionLength: 750, // number of chars to truncate description to
  ensureSecureImageRequest: true,
  encodeFields: false
}
```

### Returns
Returns a promise that gets resolved with the following url metadata if the url request response returns successfully:
```
{
  'url'                  : '',
  'title'                : '',
  'image'                : '',
  'author'               : '',
  'description'          : '',
  'source'               : '',
  'og:url'               : '',
  'og:locale'            : '',
  'og:locale:alternate'  : '',
  'og:title'             : '',
  'og:type'              : '',
  'og:description'       : '',
  'description'          : '',
  'og:determiner'        : '',
  'og:site_name'         : '',
  'og:image'             : '',
  'og:image:secure_url'  : '',
  'og:image:type'        : '',
  'og:image:width'       : '',
  'og:image:height'      : ''
}
```

Additional fields are also returned if the url has an `og:type` set to `article`. These fields are:
```
'article' : {
  'article:published_time'     : '',
  'article:modified_time'      : '',
  'article:expiration_time'    : '',
  'article:author'             : '',
  'article:section'            : '',
  'article:tag'                : '',
  'og:article:published_time'  : '',
  'og:article:modified_time'   : '',
  'og:article:expiration_time' : '',
  'og:article:author'          : '',
  'og:article:section'         : '',
  'og:article:tag'             : ''
}
```
