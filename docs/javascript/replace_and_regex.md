# Javascript String.replace and regex

* In regex, `()` is used to group the regex between them. They capture the text matched by the regex inside them into a numbered group that can be reused with a numbered backreference. They allow you to apply regex operators to the entire grouped regex. 

* For example, `/(abc){3}/` matches `abcabcabc`. First group matches `abc`.

* Here is the task: 

Replace everything matching the pattern "word_outside&lt;words inside&gt;" with "words inside". if word is 'abc&lt;a.b.c&gt;', the result should be a.b.c.

```js
// text = abc<a.b.c>
text.replace(/(\S+)\s*<\s*([^><]+)\s*>/g, function(match, p1, p2) {
    // here match = abc<a.b.c>
    //      p1 = abc
    //      p2 = a.b.c
    //      see the '()' in the regex
    return p2;
});

```