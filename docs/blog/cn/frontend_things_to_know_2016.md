## 前端技术栈之榜上有名-2016年3月

前端的一大特点和一大难点，就是跟上时俱进的各种技术和库的发展。无论你是不知道到底学React好还是Angular好的初学者，还是总是在纠结Grunt还是Gulp的老鸟，总是会面临这样那样的各种在前端领域中的选择。以下文字是本人关于现在在工作以及自己项目中最喜欢用的最顺手也觉得是目前来说最有前途的前端开发工具，希望能对相关的朋友们有所帮助。

| 基础库 |  架构 |    语言   |      格式     | 包管理 |   打包  |         测试         |  服务器  | Http/https请求 |    ORM    |  Promise |  桌面应用 |  其他  |
|:------:|:-----:|:---------:|:-------------:|:------:|:-------:|:--------------------:|:--------:|:--------------:|:---------:|:--------:|:--------:|:------:|
|  React | Redux | ES6/Babel | ESLint/AirBnb |   npm  | webpack | Mocha + Chai + Sinon | Sails.js |      Fetch     | Bookshelf | Bluebird | Electron | lodash |

一下是关于每个工具上榜的理由，一些众所周知的理由这里就不重复了。

### 基础库：React
1. 组件化的UI方便开发，测试以及管理
2. JSX的语法能够在写html的时候最大程度上利用JS的优势
3. 强大的开发comminity
4. 摆脱了繁琐的two-way-binding
5. 方便的server side rendering

### 架构：Redux
1. 目前为止公认最好的flux implementation
2. 语法简洁
3. 丰富的文章，教程以及第三方工具(thunk, logger, dev-tool等等)
4. Middleware大赞

### 语言：ES6/Babel
1. ES6的时代正在来临，跟上节奏
2. 前端的职位基本都已经把ES6放在了基本要求里
3. 跟ES5相比有很多好用的新东西

### 格式：ESLint/AirBnb
半强制的让你写出所谓优雅的代码哈哈，没什么好说的，硅谷各大小公司前端通用规范

### 包管理：npm
没什么好说的，基本没有竞争者。这里有一点要强调下：请好好利用npm script

### 打包：webpack
1. 组件化的管理
2. 基本上可以load所有东西
3. 只load你需要的东西
4. 大规模项目必备，谁用谁知道

关于组件化管理：比如一个button组件，文件结构如下：


index.js和index.css只包含关于这个button的东西.

index.js

import './index.css';
...
...
render() {
    return (
        <button className='app-button'>Click me</button>
    );
}



index.css

.app-button {
    color: black;
}

### 测试：Mocha + Chai + Sinon
没什么好说的，基本已成为行业标准

### 服务器：Sails.js
1. MVC + Realtime
2. 强大的预设和扩展性
3. REST API自动生成
4. 任务流水线

注意：Sail.js自带的ORM是waterline，自带的任务运行和打包工具是grunt。如果有需求的话自己花一两天研究下可以改成bookshelf和webpack

### http/https请求: fetch
1. Firefox和chrome原生API，现在请用isomorphic-fetch来获得所有浏览器的支持
2. 前后端通用
3. Promise

### ORM：bookshelf
后台与数据库交互的必备神器

### Promise：Bluebird
如果你不想被callback搞得生活不能自理：

function isUserTooYoung(id, callback) {
    openDatabase(function(db) {
        getCollection(db, 'users', function(col) {
            find(col, {'id': id},function(result) {
                result.filter(function(user) {
                    callback(user.age < cutoffAge)
                })
            })
        })
    })
}

请用promise

function isUserTooYoung(id) {
    return openDatabase(db)
        .then(getCollection)
        .then(find.bind(null, {'id': id}))
        .then(function(user) {
            return user.age < cutoffAge;
        });
}

### 桌面应用：Electron
没什么好说的，这些软件都是用前端的技术和Electron写出来的
1. https://atom.io/
2. https://slack.com/
3. https://code.visualstudio.com/

### 其他（此处我在英文版里写的是utilities, 不知道中文到底应该翻成什么。。）
必备Lodash，除此之外貌似没有这么刚需的

最后想讲的是，需求驱使技术，技术提升需求。可以为了练习用这个东西来用这个东西，但是绝对不要为了用这个东西而用这个东西。永远把你的需求摆在第一位。对于连需求都没有的朋友们，希望先找到你们的需求。

我是新手，我现在的目标是学习javascript - 那就先别考虑什么react/meteor/vue
我需要做一个单页面应用 - 那就别把时间花在redux上，react自带的state可以满足你的所有需求
我的web app需要一个数据库，但是我从来没用过也不了解数据库 - 那就网上花半小时看看mongoose，别纠结那些mysql语法什么的




