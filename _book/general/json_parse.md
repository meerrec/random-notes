```js
connection1.query("SELECT * FROM users WHERE id = ?", [userID], function(err, rows) {
    if (err) throw err;
    var oldTranscription = JSON.parse(rows[0].score);
    ...
```

Some times when there is a bad connection or the json string is too large, it will have the error like this:

```js
/Users/haochuan/Projects/logging-labeling-system/node_modules/mysql/lib/protocol/Parser.js:82
        throw err;
              ^
SyntaxError: Unexpected end of input
    at Object.parse (native)
    at /Users/haochuan/Projects/logging-labeling-system/routes/admin.js:35:47
```
means that the json has not been fully got before starting the parsing process.

### Solution

```js
var object = undefined;
    try
    {
        object = JSON.parse(jsonString);
    }
    catch (e)
    {
        // If an error occurs while parsing the JSON string reset object
        // and emit the error
        object = undefined;
        this.emit('error', e);
    }

    // If object is undefined return without emitting any events.
    if (object === undefined) return;
```

