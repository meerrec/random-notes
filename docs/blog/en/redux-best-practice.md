## Redux Best Practices

Top 10 things I've learned through over 20 redux projects from tiny to large scales.

---

#### Use ES6

Some of the ES6 features will be heavily used in your redux code:
- `import { xx, yy } from zz`
- `return [...state, {value: "new"}]`
- `()=>`
- And more...

---

#### Setup your project properly

Use webpack, hot-loading, react-router, react-redux, enzyme...
[Mern](http://mern.io/) is a very good example about how to setup and structure your project, you probably don't need all the stuff in Mern, just pick things you need and learn the concept.

---

#### Choose the middlewares based on your ways and what you need

There are a lot of redux middlewares online for different purposes. You have to know the basic concept that middlewares will do some thing between dispatching an action, and the moment it reaches the reducer. So middlewares can help you in some common things you will meet such as monitoring state and dealing with async API calls

---

#### [Redux DevTools](https://github.com/gaearon/redux-devtools)

No more words, this is a must have for all redux project.

---

#### Organize the code

For small scale project, you can organize the code by type. But you may consider organizing your code by feature when meet the large scale project. Below are some useful articles about this:

- [How to better organize your React application](https://medium.com/@alexmngn/how-to-better-organize-your-react-applications-2fd3ea1920f1#.y2cfr1u84)
- [ducks-modular-redux](https://github.com/erikras/ducks-modular-redux)

---

#### Make a better use of the stateless (dump) components

In react and redux, we prefer to call the components which knows the state as the smart component or container, while the stateless components as dump component. Read this [article](https://medium.com/@joshblack/stateless-components-in-react-0-14-f9798f8b992d#.tmme8dhe0) for more details.

---

#### Use action creator with thunk/Promise/async/await to handle API calls

It does not make sense for me that any component should know the detail of an action. Instead, components only need to know what actions should be sent based on different cases or interactions. And if you have to deal with nested actions in one action, thunk/Promise/async/await will be your best friend.

---

#### Make your reducer clean

I prefer to do a lot of pre-processing for the raw data in action creators instead of in reducer. The the action parameter in reducer function will always be ready to use.

---

#### The ways to return a new state in reducer

Since the state is immutable, please be careful when you returning a new state in the reducer function. Below is a very common problem:

Suppose you are building a todo list app and the state is an array of list:

```
[
    {value: "list 1"},
    {value: "list 2"},
    {value: "list 3"}
]
```
- Add a new todo

```
// bad and does not work
case "ADD"
    return state.push({value: "list 4"});

// Good
case "ADD"
    return [
        ...state,
        {value: "list 4"}
    ];
```

- Delete a todo

```
// bad and does not work
case "DELETE"
    return state.splice(index, 1);

// Good
case "DELETE"
    return state.slice(0, index).concat(state.slice(index + 1));

```

- Edit a todo

```
// First way
case "EDIT"
    return state.slice(0, index)
                .concat([{value: "newValue"}])
                .slice(index + 1);
// Second way
case "EDIT"
    return state.map((item) => {
        if (item.id === "id") {
            return {
                ...item, 
                value: "newValue"
            }
        } else {
            return item;
        }
    })
```

---

#### Sometimes you really do not need to bring redux or even react in
:)
