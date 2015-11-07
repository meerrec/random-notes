## Web Audio API Basic

### Initial AudioContext
```js
var audioContext;

try {
    // Fix up for prefixing
    window.AudioContext = window.AudioContext||window.webkitAudioContext;
    audioContext = new AudioContext();
} catch(e) {
    alert('Web Audio API is not supported in this browser');
}
```
### Chaining the input and output
```js
var node1 = someFunction() // first node (input)
var node2 = someFunction(); // second node
var node3 = someFunction(); // another node
node1.connect(node2);
node1.connect(node3);
node2.connect(audioContext.destination); // audioContext.destination is the system output
node3.connect(audioContext.destination); //
/*
node1 ----- node 2
  |           |
  |           |
  |           |          
node3 ----- destination
 */
```
### Oscillator Node
- Don't forget to connect the node to the destination

```js
var osc = audioContext.createOscillator();
osc.type = 'sine'; // sine, square, sawtooth, triangle

// Note that the belows are in the type of AudioParam
osc.frequency.value = 440;
osc.detune.value = 2; // A detuning value (in Cents) which will offset the frequency by the given amount
// be sure to connect the osc node to destination before starting it
osc.start(0);
osc.stop(2);
```
### Load Audio File
- The actual buffer data can be accessed in the callback function

```js
function loadAudio(url, cb) {

    var request = new XMLHttpRequest();
    request.open('GET', url, true);
    request.responseType = 'arraybuffer';

    request.onload = function() {
        audioContext.decodeAudioData(request.response, function(buffer) {
            cb(buffer);
        });
    }
    request.send();
}
```




