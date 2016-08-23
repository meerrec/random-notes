## 在Mac OSX下设置前端开发环境

新年快乐！
以下内容将会详细介绍本人在MAC OSX下关于前端开发环境的安装和设置，如果您是前端开发人员，并且手上有个全新的或者重新安装过系统的mac，你可能会在以下内容里发现你所需要的东西。

## Google Chrome
几乎是每个前端开发者必备的浏览器，下载地址: [https://www.google.com/chrome](https://www.google.com/chrome).

一些常用到得Chrome插件:
- [JSON Formatter（显示格式化过得JSON文件）](https://chrome.google.com/webstore/detail/json-formatter/pblpfhfcojodgcifojnofommahgbaple?utm_source=chrome-ntp-icon)
- [Postman（发送request）](https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop?utm_source=chrome-ntp-icon)
- [React Dev Tools（React测试工具）](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?utm_source=chrome-ntp-icon)
- [Page load time（计算网页load时间）](https://chrome.google.com/webstore/detail/page-load-time/fploionmjgeclbkemipmkogoaohcdbig?utm_source=chrome-ntp-icon)

## iTerm2
MAC OSC下最好的terminal app，没有之一。

##### 两个我常用的主题
- [tomorrow](https://github.com/chriskempson/tomorrow-theme)
- [dracula-theme](https://github.com/zenorocha/dracula-theme)

##### 字体
我在用 `12pt Monaco`.


## Homebrew
就像它的官网说的，它是MAC OSC下失传已久的包管理器
##### 安装
```
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

##### 常用命令
- Update homebrew's directory of formulas: `brew update`
- Update a package: `brew upgrate <package name>`
- Install a package: `brew install <package name>`
- Link/unlink a package: `brew link/unlink <package name>`

## Oh My Zsh
Terminal里bash的最佳替代品，强大的自动补全功能，能自动补全命令、参数、文件名、进程、用户名、变量、权限符等， 以及各种插件以及主题的支持。


##### 安装
```
$ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

```
##### 设置
设置文件的路径为 `~/.zshrc`, 你可以在下面地址找到我的设置文件 [my zsh setting](https://github.com/haochuan/random-notes/blob/master/dot-files/.zshrc).

## Vim
非vim党请跳过此段。
##### 安装
尽管vim在MAC OSX里是内置的，但是为了安装一些强大的插件，你需要下载安装最新版本。

```
brew install vim
brew link vim
```

##### 设置: spf13-vim
[spf13-vim](https://github.com/spf13/spf13-vim) 是一个vim的集成开发环境，内置集成很多常用的插件。
- Vundle
- NERDTree
- Neocomplcache
- Syntastic
- Fugitive
- Tagbar

###### 安装 (要求有git)
```
curl https://j.mp/spf13-vim3 -L > spf13-vim.sh && sh spf13-vim.sh
```

## Sublime Text 3

请在这里下载 [here](http://www.sublimetext.com/3).

##### Package Control
首先安装 [package control](https://packagecontrol.io/):
```
import urllib.request,os,hashlib; h = '2915d1851351e5ee549c20394736b442' + '8bc59f460fa1548d1514676163dafc88'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```

##### 一些常用的包
- General
    - [Side​Bar​Enhancements](https://packagecontrol.io/packages/SideBarEnhancements)
        - 边栏菜单功能的扩充
    - [Alignment](https://packagecontrol.io/packages/Alignment)
        - 多行代码对齐
    - [Doc​Blockr](https://packagecontrol.io/packages/DocBlockr)
        - 代码文档
    - [Comment-Snippets](https://packagecontrol.io/packages/Comment-Snippets)
        - 代码注释snippets
    - [Vintageous](https://packagecontrol.io/packages/Vintageous)
        - 强大的vim模拟
    - [Block Cursor Everywhere](https://packagecontrol.io/packages/Block%20Cursor%20Everywhere)
        - 可以在vim模式里使用块状cursor
- Front End
    - [Emmet](https://packagecontrol.io/packages/Emmet)
        -  快速写html和css利器
    - [Color​Picker](https://packagecontrol.io/packages/ColorPicker)
        - 调用你本机的调色板应用来选取颜色
    - [Color Highlighter](https://packagecontrol.io/packages/Color%20Highlighter)
        - 在编辑器里显示颜色的背景色
- Other
    - [Markdown Preview](https://packagecontrol.io/packages/Markdown%20Preview)
        - 在浏览器里预览markdown
- Theme and Color
    - [Tomorrow Color Schemes](https://packagecontrol.io/packages/Tomorrow%20Color%20Schemes)
    - [Afterglow](https://packagecontrol.io/packages/Theme%20-%20Afterglow)
    - [Oceanic Next Color Scheme](https://packagecontrol.io/packages/Oceanic%20Next%20Color%20Scheme)

##### 怎样用dropbox来同步不同机器里的sublime text设置


- 第一台机器
```
cd ~/Library/Application\ Support/Sublime\ Text\ 3/Packages/
mkdir ~/Dropbox/Sublime
mv User ~/Dropbox/Sublime/
ln -s ~/Dropbox/Sublime/User
```

- 其他机器
```
cd ~/Library/Application\ Support/Sublime\ Text\ 3/Packages/
rm -r User
ln -s ~/Dropbox/Sublime/User
```

## 开发工具
* [git](https://git-scm.com/)
```
brew install git
```

* [Node.js and Npm](https://nodejs.org)

可以直接在官网下载安装包，或者：
```
brew install node
```

* [SASS](http://sass-lang.com/)
```
gem install sass
```

* [Nodemon](https://github.com/remy/nodemon) and [pm2](https://github.com/Unitech/pm2)

Node开发和部署工具
```
npm install nodemon -g
npm install pm2 -g
```

* [Grunt](http://gruntjs.com/), [gulp](http://gulpjs.com/), and [webpack](https://webpack.github.io/)
```
npm install -g grunt-cli
npm install -g gulp
npm install -g webpack
```

* [jshint](http://jshint.com/)

```
npm install -g jshint
```

* [MongoDB](https://www.mongodb.org/)

```
brew update
brew install mongo
```

## Mac OSX 应用

- [Dropbox](https://www.dropbox.com/)
    - 文件同步
- [Alfred 2](https://www.alfredapp.com/)
    - 效率利器
- [Bartender 2](http://www.macbartender.com/)
    -  MAC OSC顶部菜单管理
- [SizeUp](http://www.irradiatedsoftware.com/sizeup/)
    - 快速调整窗口位置和大小
- [iStat Menus](https://bjango.com/mac/istatmenus/)
    - 监控电脑cpu，ram，network，温度

-----
##### 目前只能想起这么多了，之后会随时更新

##### 附上一些个人觉得有趣好用的东西

- [node-notifier](https://github.com/mikaelbr/node-notifier)
    - A Node.js module for sending notifications on native Mac, Windows and Linux (or Growl as fallback)

- [z](https://github.com/rupa/z)
    - Tracks your most used directories, based on 'frecency'.
    - After  a  short  learning  phase, z will take you to the most 'frecent' directory that matches ALL of the regexes given on the command line, in order.
    - For example, z foo bar would match /foo/bar but not /bar/foo.
- [quill](http://quilljs.com/)
    - Fast and lightweight rich text editor
    - Semantic markup
    - Standardized HTML between browsers
    - Cross browser support including Chrome, Firefox, Safari, and IE 9+
- [impress.js](https://github.com/impress/impress.js)
    - It's a presentation framework based on the power of CSS3 transforms and transitions in modern browsers and inspired by the idea behind prezi.com. 
-[mousetrap](https://github.com/ccampbell/mousetrap)
    - Simple library for handling keyboard shortcuts in Javascript
- [jsdoc](https://github.com/jsdoc3/jsdoc)
    - An API documentation generator for JavaScript
- [Moment.js](http://momentjs.com/)
    - Parse, validate, manipulate, and display dates in JavaScript.
- [Ghost](https://ghost.org/)
    - Ghost is a simple, powerful publishing platform that allows you to share your stories with the world.
- [Faker](https://github.com/stympy/faker)
    - A library for generating fake data such as names, addresses, and phone numbers.
- [GitBook](https://github.com/GitbookIO/gitbook)
    - Modern book format and toolchain using Git and Markdown

- [bluebird](https://github.com/petkaantonov/bluebird)
    - Bluebird is a full featured promise library with unmatched performance.
- [tldr](http://tldr-pages.github.io/)
    - tldr is a collection of simplified and community-driven man pages.
- [is.js](https://github.com/arasatasaygin/is.js)
    - Micro check library





