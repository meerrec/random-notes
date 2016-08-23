#### Original Code Block

```
var myString = 'Hello World''
console.log(myString)
``` 

#### New Code Block

```js
var myString = 'Hello World''
console.log(myString)
``` 

---

#### How?

- Choose the language and theme and download the `css` and `js` file on [prismjs](http://prismjs.com/)
- Put the `js` and `css` file into right places
    - prism.js: `/content/themes/[theme name]/assets/js/`
    - prism.css: `/content/themes/[theme name]/assets/css/`
- Add the files in `/content/themes/[theme name]/default.hbs`

---
> prism.js

```handlebars
<script type="text/javascript"  
        src="{{asset "js/prism.js"}}"></script> 
{{! The main JavaScript file for [theme name] }}
<script type="text/javascript"  
        src="{{asset "js/main.js"}}"></script>  
```
---

> prism.css

```handlebars
<link rel="stylesheet" type="text/css"  
      href="{{asset "css/[theme name].css"}}" />
<link rel="stylesheet" type="text/css"  
      href="{{asset "css/prism.css"}}" />   
```
   - Ready to go! Add those in a post to test the highlighting.

```js
var myString = 'Hello World''
console.log(myString)
``` 
