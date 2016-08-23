Based on my understanding, I listed six of the most important parts as a software engineer, followed by some descriptions or examples. Please leave a comment if you agree/disagree one or some of those, and I’d like to hear your opinions and thoughts!




## Computer science fundamentals 10

If you never feel like the understanding of some basic algorithm, data structure and design pattern is a must-have knowledge during your work, then I have to doubt that if you are considered as en eligible software engineer. Here I say computer science fundamentals because we software engineer are not considered as computer scientist, so there is no need for us to explore the black magic of a specific concept or algorithm. Instead, a software engineer do need to know basic principles of Computer science fundamentals, as well as the ways to solve the most common problems in the software development.


### Example 1
Your task is to build a system for English listening skill test. Suppose that you have 100 English sentences with the audios, you will let the user to write down the sentence they just heard and then compare the difference between the original sentence and the one submitted but users. What should you do?

##### Good
You know that this is a place to use edit distance, and you write all the implementation code within 10 mins.

##### Average
You know there is something called edit distance, which is a way of quantifying how dissimilar two strings are. Then goole edit distance, and find the right implementation within 20 mins.

##### Poor
You have no idea where to start

### Example 2
You are going to add undo/redo feature in a input field in your website.

##### Good
Two stack: undoStack [] and redoStack [].
- Type a, push a to undoStack, undoStack = [a] and redoStack = [], input = a
- Type b, push b to undoStack, undoStack = [a, b] and redoStack = [], input = ab
- Type c, push c to undoStack, undoStack = [a, b, c] and redoStack = [], input = abc
- Undo, pop from undoStack, push pop result to redoStack, undoStack = [a, b] and redoStack = [c], input = ab
- Undo, pop from undoStack, push pop result to redoStack, undoStack = [a] and redoStack = [c, b], input = a
- Redo, pop from redoStack, push pop result to undoStack, undoStack = [a, b] and redoStack = [c], input = ab


##### Poor
You have no idea where to start


### Example 3
You heard someone is talking about fibonacci.

##### Good
The first thing coming your mind is 1 1 2 3 5 8.

##### Average
You don't know what is fibonacci.


##### Poor
You have no idea where to start

## Coding ability with a specific language and problem solving skill 50


Software engineer writes code, so no more word to explain why coding ability matters. Although there is a long history of debating which is the best language, all the programming languages are the same at some points. They are just the tools letting the computer do what you are trying to do in your mind. Every language is different and it has its own advantages and disadvantages, and to be a software engineer, you have to master at least one of the them.

Being familiar with the language syntax and its built-in functions is one of the part of coding ability, but trying to remember those in a hard way at the beginning is not a good idea. Searching for the documentation about the syntax the functions has no relationship with your coding ability, but you will remember those by heart if you use that a lot.

Also in my mind I think problem solving skill should be in the same group with coding ability cause they always tie together.

Note: The examples below are all in Javascript.

##### Example 1
It is a very common problem that we need to know what are the query parameters in a web URL. Suppose the URL is `http://helloworld.com?user=haochuan&param1=aaa&param2=bbb`, how can we convert the query parameters into a JS Object from the string like:

```js
{
    user: "haochuan",
    param1: "aaa",
    param2: "bbb"
}
```

##### Good
Use Regex:

```js
const URL = "http://helloworld.com?user=haochuan&param1=aaa&param2=bbb";
const RE = /(\?|\&)([^=]+)\=([^&]+)/g;
let paramsObject = {};

URL.replace(RE, (match, p1, p2, p3) => {
    paramsObject[p2] = p3;
});

console.log(paramsObject);
// will be { user: 'haochuan', param1: 'aaa', param2: 'bbb' }
```

##### Average
Trying to use `URL.split('?')`, then `split('&')`. then `split('=')`. Then construct the object.


##### Poor
You have no idea where to start


##### Example 2
Your teammate ask you to write a function to swap to integer, no extra variable is allowed.


##### Good

```js
function swapNumb(a, b){
  a = a ^ b;
  b = a ^ b;
  a = a ^ b;
}
```

##### Average
```js
function swapNumb(a, b){
  b = b - a;
  a = a + b;
  b = a - b;
}
```


##### Poor
You have no idea where to start


##### Example 3 (Language feature)
Print a number every second from 1 to 5


##### Good

```js
for (var i = 1; i < 6; i++) {
    (function (num) {
        setTimeout(function (){
            console.log(num);
        }, 1000);
    })(i);
}
```


##### Poor

```js
for (var i = 1; i < 6; i++) {
    setTimeout(function (){
        console.log(num);
    }, 1000);
}
```

##### Example 4 (Comments and documentation)
Make sure your code is fully documentated, and knowing where to add `FIXME`, `TODO`, `REMOVEME` in your code.


##### Good

```js
/**
 * Function to return the sum of two integer
 * @param  {Integer} a first integer
 * @param  {Integer} b second integer
 * @return {Integer}   sum of a and b
 */

// TODO: support float sum in next month
function sum(a, b) {
    return a + b;
}
```


##### Poor

```js
function sum(a, b) {
    return a + b;
}
```


## Mastery in development Tools 5
There is no need for everyone to master vim or emacs as the editor, but you do need to be fluent in at least one code editor/IDE based on your preference, as well as some common used tools such as git and some basic terminal command.

##### Example 1
Suppose you have a 3 line Javascript file, and the semicolon for each line is missing. What will you do if you want to add those missing semicolon?

```js
const HOST = 'http://host.com'
const API = '/api/getPage'
loadContent(HOST + API)
```


##### Good

- vim

`gg` -> `shift + a` -> `;` -> `Esc` -> `j` -> `.` -> `j` -> `.`

- sublime

Write your own plugin for or find a plugin online for those common tasks.

##### Poor

looking for end the line by eyes -> mouse click -> press `;` -> repeat

##### Example 2
Suppose you have a 3 line Javascript file, what you will do if you want to move swap the content in line 2 and line 3?

```js
const HOST = 'http://host.com';
loadContent(HOST + API);
const API = '/api/getPage';
```

##### Good

- vim

`3gg` -> `Esc` -> `:m 1` -> `Enter`

- sublime

Click anywhere in line 3, the `Command + Control + upArrow`

##### Poor

Select -> copy -> paste

## Familiarity with software development methodology and processes 10
Although sometimes you don't need to care more about this, if you do, knowing all these will make your life easier and save you a lot time.

##### Good

- Know how to use git/svn for collaboration
- Know how to setup the development enviroment quickly
- Know how to deploy your code
- Know test related stuff

## Learning Ability 15

It is nearly impossible to require that every software engineer share a common development stack even if they are in the same position and doing the same job, but at least we should have the ability to learn. Let’s go back to the time when React started to become popular, the ability to figure out whether such a new thing is good or bad, the ability to find the most suitable Flux implementation based on your project, the ability to add this new library to your existed project, are the ability of learning. So if my company uses a lot of Angular as the front end framework, I won’t list Angular as the must-have skill when writing the job description for recruiting. Instead, I care more about the learning ability and in my mind, a good software engineer can pick up a new thing and make contribution within 2 weeks.

## Communication 10

Good communication skill is a time saver and will make you happy.

The list below is the skills that are most important in my work about communication:

- How well can you let other engineers understand your code within a limit time?
- How well can you understand other engineers’ code within a limit time?
- If there is a new engineer joining your project recently, how should you help him get started and make contribution?
- Can you describe your problem or question clearly when talking or in a discussion?


