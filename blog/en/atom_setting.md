## Setting Atom for Web Development

If you are trying to figure our what is the best editor among vim, emacs, sublime, atom, webstorm, this might not be the right thing for you. If you think you love atom, or even want to have a try, this might be helpful.

Basically this is the article about my Atom's setting for HTML, CSS, JS, React, Node.js, and all other front end related stuff.

This is how my Atom looks:

![Alt text](/images/atom_setting.png)

-----

#### UI Theme
[atom-material-ui](https://atom.io/themes/atom-material-ui)

I have been using this for a long time for both my Sublime and Atom, it's the best in my mind so far.

-----

#### Syntax Theme
[oceanic-next-dark](https://atom.io/themes/oceanic-next-dark)

Although a lot of people prefer using  [atom-material-syntax](https://atom.io/packages/atom-material-syntax) with [atom-material-ui](https://atom.io/themes/atom-material-ui), I think somehow the contrast is too high for me.

In [oceanic-next-dark](https://atom.io/themes/oceanic-next-dark), I did the following customization:

```
@syntax-cursor-color: #FFCC00;
@syntax-selection-color: #474747;
@syntax-background-color: #1C1C1C;
```

Note: I use vim and block cursor in Atom, so the cursor color is kind of important to me :)

-----

#### Keymap

So far I only have one customized keymap:

```
'ctrl-e': 'tree-view:toggle'
```

This is a matching for vim's [nerdtree](https://github.com/scrooloose/nerdtree).

#### Packages

* [atom-beautify](https://atom.io/packages/atom-beautify): Beautify HTML, CSS, JavaScript, PHP, Python, Ruby, Java, C, C++, C#, Objective-C, CoffeeScript, TypeScript, Coldfusion, and SQL in Atom
* [atom-ternjs](https://atom.io/packages/atom-ternjs): JavaScript code intelligence for atom with Tern. Adds support for ES5, ES6 (JavaScript 2015), Node.js, jQuery & Angular. Extendable via plugins. Uses suggestion provider by autocomplete-plus.
* [autocomplete-modules](https://atom.io/packages/autocomplete-modules): Autocomplete for require/import statements.
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

#### Interesting Stuff from Facebook

* [nuclide](http://nuclide.io/)
* [flow](http://flowtype.org/): A STATIC TYPE CHECKER FOR JAVASCRIPT

Personally I always ignore those two for the slowness, but in some way I will speed the development.

-----

#### Other
* Font Family: monaco
* Font Size: 12
* [auto-update-packages](https://atom.io/packages/auto-update-packages): If you want to update your packages automatically
* [file-icons](https://atom.io/packages/file-icons): If you need fancy icons for different files in the tree view
