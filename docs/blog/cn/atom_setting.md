## Atom编辑器的Web开发设置

如果你正在纠结到底在vim, emacs, sublime text, atom, webstorm中，哪个是‘最好’的编辑器，那么请忽略这篇文章。如果你觉得自己喜欢atom，或者你对atom有兴趣想尝试一下，那么这篇文章可能会对你有所帮助。

以下的内容主要是关于我自己atom的设置，主要针对于HTML，CSS，JS，React，Node.js等web前端的开发。

下图是我的Atom的截图：


![Alt text](/images/atom_setting.png)

-----

#### UI Theme
[atom-material-ui](https://atom.io/themes/atom-material-ui)

material是目前我最喜欢的Theme，我在atom和sublime里都在用。

-----

#### Syntax Theme
[oceanic-next-dark](https://atom.io/themes/oceanic-next-dark)

很多人喜欢用[atom-material-syntax](https://atom.io/packages/atom-material-syntax) 来配合 [atom-material-ui](https://atom.io/themes/atom-material-ui)一起，但是我觉得这个Syntax Theme的对比度对我来说有点伤眼睛。

在[oceanic-next-dark](https://atom.io/themes/oceanic-next-dark)里，我做了如下的修改（光标颜色，选中内容颜色，背景颜色）：


```
@syntax-cursor-color: #FFCC00; 
@syntax-selection-color: #474747;
@syntax-background-color: #1C1C1C;
```

注：因为我是重度vim用户，所以合适的光标颜色对我很重要:)

-----

#### Keymap

目前为止我现在只有一个自定义的keymap：

```
'ctrl-e': 'tree-view:toggle'
```

这是在vim里的[nerdtree](https://github.com/scrooloose/nerdtree)的对应。

#### Packages

* [atom-beautify](https://atom.io/packages/atom-beautify): 格式美化 HTML, CSS, JavaScript, PHP, Python, Ruby, Java, C, C++, C#, Objective-C, CoffeeScript, TypeScript, Coldfusion, and SQL in Atom
* [atom-ternjs](https://atom.io/packages/atom-ternjs): ES5, ES6 (JavaScript 2015), Node.js, jQuery & Angular 格式补全
* [autocomplete-modules](https://atom.io/packages/autocomplete-modules): require/import 自动补全
* [color-picker](https://atom.io/packages/color-picker): Right click or press CMD-SHIFT-C/CTRL-ALT-C to open it
* [docblockr](https://atom.io/packages/docblockr): A helper package for writing documentation
* [emmet](https://atom.io/packages/emmet): the essential tool for web developers
* [language-babel](https://atom.io/packages/language-babel): Babel JavaScript ES201x, React JSX & Flow Grammar & Transpiler
* [linter](https://atom.io/packages/linter): A Base Linter with Cow Powers
* [pigments](https://atom.io/packages/pigments): A package to display colors in project and files.
* [react](https://atom.io/packages/react): React.js (JSX) language support, indentation, snippets, auto completion, reformatting
* [term3](https://atom.io/packages/term3): A terminal emulator for Atom. You can run shell sessions, Vim, Emacs, htop, etc.
* [todo-show](https://atom.io/packages/todo-show): Finds all the TODOs, FIXMEs, CHANGEDs, etc. in your project.
* [vim-mode](https://atom.io/packages/vim-mode)

-----

#### 来自Facebook的两个有趣的插件包

* [nuclide](http://nuclide.io/) 
* [flow](http://flowtype.org/): 

一般情况下这两个包都是被我禁用的，因为太慢了。。

-----

#### 其他
* Font Family: monaco
* Font Size: 12
* [auto-update-packages](https://atom.io/packages/auto-update-packages): 如果你想让你的各种插件自动更新
* [file-icons](https://atom.io/packages/file-icons): 如果喜欢针对不同文件类型的不同图标
