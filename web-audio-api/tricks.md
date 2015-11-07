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

