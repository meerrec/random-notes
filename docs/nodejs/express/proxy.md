Express proxy middleware to forward request to another host and pass response back

[Link](https://github.com/villadora/express-http-proxy)

## Install

```bash
$ npm install express-http-proxy --save
```

## Usage

```js
var proxy = require('express-http-proxy');

var app = require('express')();

app.use('/proxy', proxy('www.google.com', {
  forwardPath: function(req, res) {
    return require('url').parse(req.url).path;
  }
}));

```

If you only want to proxy get request


```js
app.use('/proxy', proxy('www.google.com', {
  filter: function(req, res) {
     return req.method == 'GET';
  },
  forwardPath: function(req, res) {
    return require('url').parse(req.url).path;
  }
}));
```



You can also intercept the response before sending it back to the client, or change the request options before it is sent to the target:

```js
app.use('/proxy', proxy('www.google.com', {
  forwardPath: function(req, res) {
    return require('url').parse(req.url).path;
  },
  intercept: function(rsp, data, req, res, callback) {
       // rsp - original response from the target
       data = JSON.parse(data.toString('utf8'));
       callback(null, JSON.stringify(data));
  },
  decorateRequest: function(req) {
       req.headers['Content-Type'] = '';
       req.method = 'GET';
       req.bodyContent = wrap(req.bodyContent);
       return req;
  }
}));

```
