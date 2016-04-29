基于个人的经历和理解，下面内容列出了我认为对于一个软件工程师最重要的六个方面，然后对于每个方面我给出了解释和例子。如果你对这个话题有兴趣，请在评论写下你的观点和看法，谢谢！





## 计算机科学的基础

如果你在日常的工作中从来没有认识到一些基本的数据结构，算法知识，以及设计模式对一个软件工程师来讲是必不可少的，那么我就有理由对你是不是一个合格的软件工程师而产生怀疑。这里我说计算机科学的基础知识，是因为作为一个软件工程师而不是一个计算机科学家，我们完全没有必要去深入的研究探索某个概念或者更某个算法。我们仅仅只需要知道一些比较基础的原理，和用代码实现这些原理的方法。



### 例子 1
现在你的任务是编写一个英语听力测验的软件，假设你有100个英语句子和它们的录音，你将会让用户听这些录音并且写下来录音里的内容，然后去和原始的句子比对看看区别有多大，你应该怎么做来比对这两个句子？

##### 好
你瞬间就能意识到你应该用edit distance, 然后你能在10分钟以内完成代码实现。

##### 中
你隐约记得有种方法是专门用来计算两个字符串的相似/相同，你花了15分钟在网上找到了这个东西叫edit distance, 然后你又花了15分钟找到了实现方法然后贴在你的代码里。

##### 差
完全不知道怎么办

### 例子 2

你现在要在一个软件的输入框里添加撤销/恢复的功能。

##### 好
两个栈(stack): undoStack [] 和 redoStack [].
- 输入 a, push a 到 undoStack, undoStack = [a]， redoStack = [], input = a
- 输入 b, push b 到 undoStack, undoStack = [a, b]， redoStack = [], input = ab
- 输入 c, push c 到 undoStack, undoStack = [a, b, c]， redoStack = [], input = abc
- 撤销, undoStack 出栈一个元素, push 这个出栈的元素到 redoStack, undoStack = [a, b] and redoStack = [c], input = ab
- 撤销, undoStack 出栈一个元素, push 这个出栈的元素到 redoStack, undoStack = [a] and redoStack = [c, b], input = a
- 恢复, redoStack 出栈一个元素, push 这个出栈的元素到 undoStack, undoStack = [a, b] and redoStack = [c], input = ab


##### 差
完全不知道怎么办


### 例子 3
你听见有人在谈论斐波那契（Fibonacci）

##### 好
首先想到的是递归(recursion).

##### 中
首先想到的是1 1 2 3 5 8.


##### 差
什么都没想到

## 某种语言的代码能力和解决问题的能力

大家都知道软件工程师写代码，所以不需要太多语言来解释为什么代码能力很重要。关于不同语言的选择问题，在某种方面看来，所以的语言都是一样的，它们都是一种工具来让计算机做我们想做的事情。每种语言都有它们各自的特点，优点以及缺点，作为一个软件工程师你必须要至少掌握其中一种语言。

对于一种语言语法以及内建库/函数的熟悉是代码能力中很重要的一个方面。但是在刚开始学习这门语言的时候，死记硬背这些东西貌似并不是一个明智的选择。经常查文档来获取这些还没有那么熟悉的东西的这种行为绝对不是代码能力不够的体现。

注：以下的例子都是Javascript


##### 例子 1

一个很常见的问题就是我们需要把URL里的参数提出来并且转化为一个Javascript的Object。假设这个URL是：`http://helloworld.com?user=haochuan&param1=aaa&param2=bbb`，我们应该怎么样将它转化为以下的Object：

```js
{
    user: "haochuan",
    param1: "aaa",
    param2: "bbb"
}
```

##### 好
正则表达式

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

##### 中
`URL.split('?')` -> `split('&')` -> `split('=')`, 然后构建这个Object。


##### 差
完全不知道怎么办


##### 例子 2
你的同事让你帮他写个函数，交换两个整数, 不能用任何临时变量。


##### 好

```js
function swapNumb(a, b){
  a = a ^ b;
  b = a ^ b;
  a = a ^ b;
}
```

##### 中
```js
function swapNumb(a, b){
  b = b - a;
  a = a + b;
  b = a - b;
}
```


##### 差
没有了临时变量完全不知道怎么办


##### 例子 3 (语言特性)
从1到5每隔一秒打印出一个数字


##### 好

```js
for (var i = 1; i < 6; i++) {
    (function (num) {
        setTimeout(function (){
            console.log(num);
        }, 1000);
    })(i);
}
```


##### 差

```js
for (var i = 1; i < 6; i++) {
    setTimeout(function (){
        console.log(num);
    }, 1000);
}
```

##### 例子 4 (注释和文档)

保证你在五年之后看今天你写的代码的时候能够较快的明白你当时想要干嘛，然后在你的代码里合理的利用`FIXME`, `TODO`, `REMOVEME`等标签



##### 好

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


##### 差

```js
function sum(a, b) {
    return a + b;
}
```


## 开发工具的熟练度
没有必要所有人都要是vim或者emacs的大神，但是你必须能够玩转至少一个你喜欢的编辑器/IDE，包括各种插件，自动化，以及git和常用的命令行命令。


##### 例子 1
假设你有一个3行的Javascript文件，然后每行的末尾都忘记了分号，现在你想把分号加进来，应该怎么做？


```js
const HOST = 'http://host.com'
const API = '/api/getPage'
loadContent(HOST + API)
```


##### 好

- vim

`gg` -> `shift + a` -> `;` -> `Esc` -> `j` -> `.` -> `j` -> `.`

- sublime

自己写插件或者网上找插件来完成这种常用的操作

##### 差

眼睛找 - 鼠标点 - 键盘上点分号键 - 重复三遍

##### 例子 2
假设你有一个3行的Javascript文件，你想要替换第2航和第三行的内容，应该怎么做？

```js
const HOST = 'http://host.com';
loadContent(HOST + API);
const API = '/api/getPage';
```

##### 好

- vim

`3gg` -> `Esc` -> `:m 1` -> `Enter`

- sublime

鼠标单击第三行的任意地方，然后`Command + Control + upArrow`


##### 差

全选 - 复制 - 新建一行 - 粘贴

## 熟悉软件开发的流程和步骤

尽管在有些公司会有人来专门帮你做这些事情，但是如果你对这整个流程比较了解的话，会让你生活轻松点并且节约很多时间。


##### 好

- 知道怎么用git/svn来跟其他人合作
- 知道怎么快速的设置开发环境
- 知道一个产品的开发流程
- 知道怎么部署你的代码
- 知道测试相关的内容

## 学习能力

在我看来强行的要求每个软件工程师都用一样的东西和拥有一样的技术栈是几乎不可能的事情，即使他们有着相同的职位和相同的工作内容，所以在平时的工作中我们有一部分时间花在了学习别人熟悉的技术和任何人都不熟悉的新技术上。让我们回到React刚开始变火的那个时候，是否能在短时间内判断出react到底好不好，是否能在短时间内判断出哪个flux的实现更适合你的项目，是否能在短时间内开始用React来替换你之前的工具，这些就是所谓的学习能力。假设你从来没有用过bootstrap，通过官方的文档和网上的各种资源，你需要多长时间才能把这个新东西用到你自己的项目里，这就是所谓的学习能力。


## 沟通能力

以下我列出了在我的经历中我认为最重要的几点：

- 方法不限，形式不限，能不能用简短的语言和在有限的时间里让其他的工程师理解你写的代码？
- 方法不限，形式不限，能不能在有限的时间里理解其他工程师所写的代码？
- 如果你现在的项目有一个新的工程师加入，你能不能很好的帮助他来快速熟悉项目并且保证他在短时间内就可以对项目有所贡献？
- 你能在开各种会的时候简介明了的表达你的问题和观点么？


