# Browser Editor
In-browser quick text for simple notes

This is a snippet to turn a (non-mobile) browser window into a very simple editor

Simply copy > paste the following into the browser URL bar and hit enter
```
data:text/html;charset=UTF-8,<html contenteditable><style>*{line-height:1.6}html:before{content:'Start typing'}html:focus:before{content:''}html{font:600 1rem sans-serif;color:DimGray;background:Seashell;padding:1rem}</style></html>
```

In dark-mode
```
data:text/html;charset=UTF-8,<html contenteditable><style>*{line-height:1.6}html:before{content:'Start typing'}html:focus:before{content:''}html{font:600 1rem sans-serif;color:Gainsboro;background:DarkSlateGray;padding:1rem}</style></html>
```
