### Cannot set currentTime on audio elements
---

#### Issue

In HTML, we can use `document.getElementById("myAudio").currentTime = xxx` to set the playback time of an audio. But sometimes when you are tring to set a new value, the `currentTime` will become 0 instead the desired value.

#### Solution

In the endpoint to provide the audio (server side), add a new value in the header: `Accept-Ranges: bytes". 
