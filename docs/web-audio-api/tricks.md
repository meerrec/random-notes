## Tips and Tricks related to Web Audio API

### Resizeble canvas when doing visualization
- HTML

```html
<div id="timeDomainContainer" class='card-panel'>
    <h5>Time Domain</h5>
    <div class="divider"></div>
    <br>
    <br>
    <div id="timeDomain">
        <canvas id="timeDomainCanvas"></canvas>  
    </div>  
</div>
```
- JS

```js
function respondCanvas() {
    var timeDomainCanvas = $('#timeDomainCanvas')
    timeDomainCanvas.attr('width', timeDomainCanvas.parent().width());
    timeDomainCanvas.attr('height', timeDomainCanvas.parent().height());
}

$(document).ready(function() {
    respondCanvas();
    $(window).resize(respondCanvas);
});
```

### How to draw waveform
- Time Domain

```js
function drawTimeDomain() {
    var timeDomainCanvas = document.getElementById('timeDomainCanvas');
    var HEIGHT = timeDomainCanvas.height;
    var WIDTH = timeDomainCanvas.width;
    var timeDomainCanvasContext = timeDomainCanvas.getContext('2d');
    timeDomainCanvasContext.clearRect(0, 0, WIDTH, HEIGHT); // clear the current canvas
    App.analyser.getByteTimeDomainData(App.timeData);
    for (var i = 0; i < App.osc.timeData.length; i++) {
        var value = App.osc.timeData[i];
        var percent = value / 512;
        var height = HEIGHT * percent;
        var offset = HEIGHT - height - 1;
        var barWidth = WIDTH / App.osc.analyser.frequencyBinCount;
        timeDomainCanvasContext.fillStyle = 'black';
        timeDomainCanvasContext.fillRect(i * barWidth, offset, 1, 1);
    }
}
```

- Frequncy Domain

```js
function drawFreqDomain() {
    var freqDomainCanvas = document.getElementById('freqDomainCanvas');
    var HEIGHT = freqDomainCanvas.height;
    var WIDTH = freqDomainCanvas.width;
    var freqDomainCanvasContext = freqDomainCanvas.getContext('2d');
    freqDomainCanvasContext.clearRect(0, 0, WIDTH, HEIGHT); // clear the current canvas
    App.analyser.getByteFrequencyData(App.frequencyData);
    for (var i = 0; i < App.osc.frequencyData.length; i++) {
        var value = App.osc.frequencyData[i];
        var percent = value / 512;
        var height = HEIGHT * percent;
        var offset = HEIGHT - height - 1;
        var barWidth = WIDTH / App.osc.analyser.frequencyBinCount;
        var hue = i / App.osc.analyser.frequencyBinCount * 360;
        freqDomainCanvasContext.fillStyle = 'hsl(' + hue + ', 100%, 50%)';
        freqDomainCanvasContext.fillRect(i * barWidth, offset, barWidth, height);
    }
}
```



