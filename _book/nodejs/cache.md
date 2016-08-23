# Cache in node server

Sometimes we need to find a place to store some data while there is no need to use a database, sometimes store and read data in memory is much faster than database.

Suppose we have a text file contains tons of words, and somehow we need to check all the words in a given sentence to see if those words are in the text file.

We are using [node-cache](https://github.com/ptarjan/node-cache) here.

* Loading the text file into memory

```js
var cache = require('memory-cache');
var _ = require('underscore');
var readline = require('readline');
var fs = require('fs');
var path = require('path');

module.exports = function() {  
    cacheVocab(path.join(__dirname, './vocab.txt'));
    // we can even schedule to update the data 
    setInterval(function() {
        cacheVocab(path.join(__dirname, '/vocab/20160301_145409_vocab.txt'));
    }, 1800000); // every 30 mins
};

function cacheVocab(filePath) {
    var hashArray = [];
    var boolArray = [];
    var hashMap;

    var rl = readline.createInterface({
        input: fs.createReadStream(filePath)
    });
    console.log("Start loading vocab.");
    rl.on('line', function(line) {
        hashArray.push(line);
        boolArray.push(true);
    }).on('close', function() {
        hashMap = _.object(hashArray, boolArray);
        cache.put('vocab', hashMap);
        console.log("Finish loading vocab.");
    });
}
```
* Check if the word in the memory (in a post request)

```js
var unknowList = [];
if (req.body.transcription.length !== 0) {
    var transcriptionArray = req.body.transcription.split(' ');
    for (var i = 0; i < transcriptionArray.length; i++) {
        if (!cache.get('vocab')[transcriptionArray[i]]) {
            unknowList.push(transcriptionArray[i]);
        } 
    }
    if (unknowList.length === 0) {
        res.send('all pass');
    } else {
        res.send(unknowList);
    }
} else {
    res.send('error. the transcription should not be empty string');
}
```