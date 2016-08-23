## How to communicate between pure React components without flux

The data flow inside a React App is one of the most important part to take care of, and there has been a very popular concept 'Flux' was invented by Facebook to handle the this around the JS world.

Flux is the application architecture that Facebook uses for building client-side web applications. It complements React's composable view components by utilizing a unidirectional data flow. It's more of a pattern rather than a formal framework, and you can start using Flux immediately without a lot of new code.

However, for some of the small scale projects or site, there is no need to add the complexity of Flux. The pure React can basically handle two types of data flow, or two types of communication itself.

-----

### Parent to Child Communicaton
#### What is the parent-child relationship
```js
// in Parent.js
export default React.createClass({
    render() {
        return (
            <div>
                <Child1 />
                <Child2 />
            </div>
        ); 
    }
});
```
In the code above, `<Child1>` and `<Child2>` are considered as the children of `<Parent>`.

#### Pass data to children
In the parent, you can just pass data in a very similar way of the `HTML` attribute. You can choose the attribute name what ever you want.

```js
// in Parent.js
export default React.createClass({
    render() {
        return (
            <div>
                <Child1 text="Hello World"/>
                <Child2 numberArray=[1, 2, 3, 4, 5]/>
            </div>
        ); 
    }
});
```
In the child, you can access the data from the parent simply by `this.props`. For example, in `Child1`, `{this.props.text}` should be the string 'Hello World'.

```js
// in Child1.js
export default React.createClass({
    render() {
        return (
            <div>
                <p>{this.props.text}</p>
            </div>
        ); 
    }
});
```

#### When child's content will update

When there is a change for the value of the props passed from the parent, the `render()`function in child will be called to re-render the components. Props can change when the parent renders the component again with different properties. 

For instance, the `Parent` has a text field in its state, and passes it to `Child` thats displays this text. Its render method is just return `<Child text={this.state.text} />`. When the `Parent` calls `this.setState{text: this.state.text + "new content"}`, the Child is re-rendered with the new value for text. 

#### Note

One disavantage of this technique is if you want to pass down a prop to a grandson (you have a hierarchy of components): the son has to handle it first, then pass it to the grandson. So with a more complex hierarchy, it’s going to be impossible to maintain. 

A solution exists to avoid that and automatically have the parent talking to its grandson without the child to pass properties manually, the [context](https://facebook.github.io/react/docs/context.html).

-----

### Child to parent 

For the opposite way, if the `Child` wants to send data back to the `Parent`, or just tell the `Parent` when there is an change or update, we do this in the `Parent` render method by passing a new callback (handleChildClick) into the `Child`, binding it to some events of the `Child`. Whenever the events are triggered, the callback will be invoked.

```js
// in Parent.js
export default React.createClass({
    getInitialState() {
        return {number: 1}
    },

    handelChildClick(number) {
        console.log('From Parent');
        this.setState({number: this.state.number + number});
    },

    render() {
        return (
            <div>
                <Child number={this.state.number} handleChildClick={this.handleChildClick}}/>
            </div>
        ); 
    }
});
```

```js
// in Child.js
export default React.createClass({
    buttonHandler() {
        console.log('From Child');
        this.props.handleChildClick(1);
    },

    render() {
        return (
            <div>
                <p>{this.props.number}</p>
                <button onClick={buttonHandler}>ADD ONE</button>
            </div>
        ); 
    }
});
```

When the `button` in `Child` is clicked, the `buttonHandler` will be invoked first, and then the `handleChildClick` function in `Parent` will be called with the parameter '1'. It will change the state in the `Parent` and then the props `number` passed to `Child` will be updated. Now you should see the new value of `number` in the `Child`.

-----

### Notes about the communication between components that are not related (Use Flux)

For the communication between two components that are not related, currently there is no good way to deal with the data flow just within pure React, which means you have to use the Flux to achieve this. Some of the good Flux implementations includes:
* [Flux Comparision](https://github.com/voronianski/flux-comparison)
* [Redux](https://github.com/gaearon/redux)
* [RefluxJS](https://github.com/spoike/refluxjs)
* [Fluxxor](https://github.com/BinaryMuse/fluxxor)
* [Marty](https://github.com/martyjs/marty)
* [McFly](https://github.com/kenwheeler/mcfly)
* [Alt](https://github.com/goatslacker/alt)
* [DeLorean](https://github.com/deloreanjs/delorean)
* [Fluxible](https://github.com/yahoo/fluxible)
* [Dispatchr](https://github.com/yahoo/dispatchr)
* [Fetchr](https://github.com/yahoo/fetchr)
* [NuclearJS](https://github.com/optimizely/nuclear-js)
* [WTFlux](https://github.com/staltz/wtf)