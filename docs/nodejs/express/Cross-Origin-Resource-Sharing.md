# `cors`

CORS is a node.js package for providing a [Connect](http://www.senchalabs.org/connect/)/[Express](http://expressjs.com/) middleware that can be used to enable [CORS](http://en.wikipedia.org/wiki/Cross-origin_resource_sharing) with various options. In this way you can use AJAX to call the APIs.

## Usage

### Simple Usage (Enable *All* CORS Requests)

```javascript
var express = require('express')
  , cors = require('cors')
  , app = express();

app.use(cors());

app.get('/products/:id', function(req, res, next){
  res.json({msg: 'This is CORS-enabled for all origins!'});
});

app.listen(80, function(){
  console.log('CORS-enabled web server listening on port 80');
});
```

### Enable CORS for a Single Route

```javascript
var express = require('express')
  , cors = require('cors')
  , app = express();

app.get('/products/:id', cors(), function(req, res, next){
  res.json({msg: 'This is CORS-enabled for all origins!'});
});

app.listen(80, function(){
  console.log('CORS-enabled web server listening on port 80');
});
```