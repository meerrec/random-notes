## React - passing a value with onClick


```js
<button onClick={handler.bind(this, 'reject')}>
    Reject
</button>

handler(message, e) {
    console.log(message); //should be 'reject'
}
```

