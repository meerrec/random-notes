- In `reducer`, use ES6 spread instead of `Array.push()`

```
... 

// bad and does not work
case "ADD"
    return state.push(newItem);

// Good
case "ADD"
    return [
        ...state,
        newItem
    ];

- In `reducer`, use `Array.slice' instead of `Array.splice`

```
... 

// bad and does not work
case "DELETE"
    return state.splice(index, 1);

// Good
case "DELETE"
    return state.slice(0, index).concat(state.slice(index + 1));