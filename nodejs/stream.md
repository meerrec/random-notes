#### Basic syntax

```js
a.pipe(b).pipe(c).pipe(d)
```

#### Useful Library

- [through2](https://github.com/rvagg/through2)

    ```js
    // Full example
    var through2 = require('through2');
    var transform = through2(write, end);

    function write(buffer, encoding, callback) {
        this.push(buffer.toString().toUpperCase());
        callback();
    }

    function end(callback) {
        callback();
    }
    process.stdin.pipe(transform).pipe(process.stdout);

    // But write and end are both optional
    // simple way
    var through = require('through2');
    var tr = through(function (buf, _, next) {
        this.push(buf.toString().toUpperCase());
        next();
    });
    process.stdin.pipe(tr).pipe(process.stdout);
    ```
    **Notes:**

    ```js
    process.stdin.push(data);
    ```
- [split](https://github.com/dominictarr/split)

    Break up a stream and reassemble it so that each line is a chunk. matcher may be a `String`, or a `RegExp`

    ```js
    a.pipe(split).pipe(b);
    ```
- [concat-stream](https://github.com/maxogden/concat-stream)

    Writable stream that concatenates strings or binary data and calls a callback with the result. Not a transform stream -- more of a stream sink.

    ```js
    var fs = require('fs');
    var concat = require('concat-stream');

    var readStream = fs.createReadStream('cat.png');
    var concatStream = concat(gotPicture);

    readStream.on('error', handleError);
    readStream.pipe(concatStream);

    function gotPicture(imageBuffer) {
      // imageBuffer is all of `cat.png` as a node.js Buffer
    }

    function handleError(err) {
      // handle your error appropriately here, e.g.:
      console.error(err) // print the error to STDERR
      process.exit(1) // exit program with non-zero exit code
    }
    ```

#### Example

- Pipe req and res

    ```js
    req.pipe(through2(function(buffer, encodeing, next) {
            this.push(buffer.toString().toUpperCase());
            next();
        }, function(done) {
            done();
        })).pipe(res);
    ```
