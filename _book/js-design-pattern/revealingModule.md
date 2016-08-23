### Revealing Module Pattern

```js
var myRevealingModule = (function () {

    var privateCounter = 0;

    function privateFunction() {
        privateCounter++;
    }

    function publicFunction() {
        publicIncrement();
    }

    function publicIncrement() {
        privateFunction();
    }

    function publicGetCount(){
      return privateCounter;
    }

    // Reveal public pointers to
    // private functions and properties

   return {
        start: publicFunction,
        increment: publicIncrement,
        count: publicGetCount
    };

})();

myRevealingModule.start();
```

-	Advantages

	This pattern allows the syntax of our scripts to be more consistent. It also makes it more clear at the end of the module which of our functions and variables may be accessed publicly which eases readability.

