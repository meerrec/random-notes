## SETUP A NEW MAC FOR FRONT END DEVELOPMENT

Welcome to 2016! This documentation describes how I set my front-end development environment on a new Mac OSX system. If you ever have a chance to do the setup, you may find something helpful here.

Note: I do not have the details and usage of all the stuff I mentioned in the list below. Please google it/them to get more information.

## Google Chrome
It's a must have browser for every front-end guy, download from here: [https://www.google.com/chrome](https://www.google.com/chrome).

Some of the useful plugins:
- [JSON Formatter](https://chrome.google.com/webstore/detail/json-formatter/pblpfhfcojodgcifojnofommahgbaple?utm_source=chrome-ntp-icon)
- [Postman](https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop?utm_source=chrome-ntp-icon)
- [React Dev Tools](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?utm_source=chrome-ntp-icon)
- [Page load time](https://chrome.google.com/webstore/detail/page-load-time/fploionmjgeclbkemipmkogoaohcdbig?utm_source=chrome-ntp-icon)

## iTerm2
Best terminal app in OSX.

##### Two of my favorite themes
- [tomorrow](https://github.com/chriskempson/tomorrow-theme)
- [dracula-theme](https://github.com/zenorocha/dracula-theme)

##### Font
I'm using `12pt Monaco`.


## Homebrew
As the words from it's official website: it is the missing packege manager for OSX.
##### Installation 
```
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

##### Common Usage
- Update homebrew's directory of formulas: `brew update`
- Update a package: `brew upgrate <package name>`
- Install a package: `brew install <package name>`
- Link/unlink a package: `brew link/unlink <package name>`

## Oh My Zsh
Oh-My-Zsh is an open source, community-driven framework for managing your ZSH configuration. It comes bundled with a ton of helpful functions, helpers, plugins and themes.

##### Installation
```
$ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

```
##### Setting
You can find the setting file in `~/.zshrc`, and you can find my setting in [my zsh setting](https://github.com/haochuan/random-notes/blob/master/dot-files/.zshrc).

## Vim
If you are not a vim guy, please skip this.
##### Installation
Although vim is a pre-installed software for Mac OSX, in order to get the latest version for some of the fatanstic plugins, you probably need a newer version.

```
brew install vim
brew link vim
```

##### Setting: spf13-vim
[spf13-vim](https://github.com/spf13/spf13-vim) is a distribution of vim plugins and resources for Vim, Gvim and MacVim including:
- Vundle
- NERDTree
- Neocomplcache
- Syntastic
- Fugitive
- Tagbar

###### Installation (git required)
```
curl https://j.mp/spf13-vim3 -L > spf13-vim.sh && sh spf13-vim.sh
```

## Sublime Text 3

You can download sublime text 3 [here](http://www.sublimetext.com/3).

##### Package Control
First install the [package control](https://packagecontrol.io/):
```
import urllib.request,os,hashlib; h = '2915d1851351e5ee549c20394736b442' + '8bc59f460fa1548d1514676163dafc88'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```

##### Good Packages
- General
    - [Side​Bar​Enhancements](https://packagecontrol.io/packages/SideBarEnhancements)
        - More advanced sublime text sidebar
    - [Alignment](https://packagecontrol.io/packages/Alignment)
        - Aligning multi-line and multi selection
    - [Doc​Blockr](https://packagecontrol.io/packages/DocBlockr)
        - Simplifies writing DocBlock comments in Javascript, PHP, CoffeeScript, Actionscript, C & C++
    - [Comment-Snippets](https://packagecontrol.io/packages/Comment-Snippets)
        - Several snippets to create some fancy comments
    - [Vintageous](https://packagecontrol.io/packages/Vintageous)
        - Better Vi/Vim emulation for Sublime Text 3
    - [Block Cursor Everywhere](https://packagecontrol.io/packages/Block%20Cursor%20Everywhere)
        - Sublime Text plugin to display a block cursor in Vintage and Vintageous command mode
- Front End
    - [Emmet](https://packagecontrol.io/packages/Emmet)
        -  A more convinient way to write HTML and CSS
    - [Color​Picker](https://packagecontrol.io/packages/ColorPicker)
        - A multi-platform color picker plugin
    - [Color Highlighter](https://packagecontrol.io/packages/Color%20Highlighter)
        - a plugin for the Sublime text 2 and 3, which underlays selected hexadecimal colorcodes (like "#FFFFFF", "rgb(255,255,255)", "white", etc.) with their real color. Also, plugin adds color picker to easily modify colors.
- Other
    - [Markdown Preview](https://packagecontrol.io/packages/Markdown%20Preview)
        - markdown preview and build plugin for sublime text 2/3
- Theme and Color
    - [Tomorrow Color Schemes](https://packagecontrol.io/packages/Tomorrow%20Color%20Schemes)
    - [Afterglow](https://packagecontrol.io/packages/Theme%20-%20Afterglow)
    - [Oceanic Next Color Scheme](https://packagecontrol.io/packages/Oceanic%20Next%20Color%20Scheme)

##### How to sync sublime text settings using Dropbox

To properly sync your installed packages across different machines, you actually do not want to sync the whole Packages/ and Installed Packages/ folders. The reason for this is that some packages have different versions for different operating systems. By syncing the actual package contents across operating systems, you will possibly run into broken packages.

The proper solution is to install Package Control on all machines and then to sync only the Packages/User/ folder. This folder contains the Package Control.sublime-settings file, which includes a list of all installed packages. If this file is copied to another machine, the next time Sublime Text is started, Package Control will install the correct version of any missing packages.

- First Machine
```
cd ~/Library/Application\ Support/Sublime\ Text\ 3/Packages/
mkdir ~/Dropbox/Sublime
mv User ~/Dropbox/Sublime/
ln -s ~/Dropbox/Sublime/User
```

- Other Machine
```
cd ~/Library/Application\ Support/Sublime\ Text\ 3/Packages/
rm -r User
ln -s ~/Dropbox/Sublime/User
```

## Dev Tools
* [git](https://git-scm.com/)
```
brew install git
```

* [Node.js and Npm](https://nodejs.org)

Just Download the installation file on the website, OR
```
brew install node
```

* [SASS](http://sass-lang.com/)
```
gem install sass
```

* [Nodemon](https://github.com/remy/nodemon) and [pm2](https://github.com/Unitech/pm2)

Node development tool and deploy tool
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

## Mac OSX Apps

- [Dropbox](https://www.dropbox.com/)
    - Get to all your files from anywhere, on any device, and share them with anyone.
- [Alfred 2](https://www.alfredapp.com/)
    - Alfred is an award-winning app for Mac OS X which boosts your efficiency with hotkeys and keywords. Search your Mac and the web effortlessly, and control your Mac using customised actions with the Powerpack.
- [Bartender 2](http://www.macbartender.com/)
    -  Organize your menu bar apps
- [SizeUp](http://www.irradiatedsoftware.com/sizeup/)
    - SizeUp allows you to quickly resize and position your windows with keyboard shortcuts or a handy menu bar icon.
- [iStat Menus](https://bjango.com/mac/istatmenus/)
    - An advantage Mac system monitor for your menubar

-----
##### Can't remember more at this moment, but will update soon.

##### With the list of some of the random wonderful stuff in my mind:

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





