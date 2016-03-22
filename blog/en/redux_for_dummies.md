## Redux For Dummies

We are all talking about React these days, while a large number of React developers has been addicted to one the most popular Flux implementation - Redux.

Here is the official definition of Flux from Facebook:

Flux is the application architecture that Facebook uses for building client-side web applications. It complements React's composable view components by utilizing a unidirectional data flow. It's more of a pattern rather than a formal framework, and you can start using Flux immediately without a lot of new code.

Recently a friend of mine asked me a question: 'I know React is kind of a way to write web views as components, but what the hell is Redux?'

Here is the story. 

After graduating from college, you rent a small apartment in the towndown while working as a front-end developer in a small startup. Here is the map view of your living room.

One Saturday you invite your friend David to your apartment. David finds that the position of your furniture in the living room is kind of wired. Here every single furniture is a React component, and a number of components is what your living room looks like.

David and you ordered a pizza dilivery and you plan to eat together at home with a recent popular movie. However, you both find it seems hard to sit, eat and watch TV at the same time, which is caused by the interaction with the furniture.

So here comes your plan, you want to rearrange your furniture like this:

You ask David to move the TV first, then the table.

All done. Now pizza and movie time!

End.

First let think about the dummy story again.
 
You find the positions of your TV and table are not reasonable
Draw the blueprint
Ask David to do the certain jobs
Furniture rearranged 

Then let's take a look for the core concepts of Redux (including React here)

View(React): What your living room looks like
Store: the coordinates of your furniture (which affects the view)
Action: the tasks asked by You (move the TV, table)
Reducer: the actual job of the task, like moving the table 10 meters to the right, which will change the store

So from a Redux perspective, the whole story should be:
view ---> action ---> reducer ---> store(state) ---> view

That exactly what this tricky Flux diagram means:

Here is the code for the whole story.
https://github.com/haochuan/redux-practice/tree/master/Redux-For-Dummies/src
And you can see the online demo here.
http://haochuan.github.io/redux-practice/Redux-For-Dummies/

If you want to know about the settings for react and redux project with webpack and hot loading, please see here.

https://github.com/haochuan/startreact





