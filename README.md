# Browser Editor
In-browser quick text for simple notes

This is a snippet to turn a (non-mobile in most cases) browser window into a very simple editor

Simply copy > paste the following into the browser URL bar and hit enter
```
data:text/html;charset=UTF-8,<html contenteditable><style>*{line-height:1.6}html:before{content:'Start typing'}html:focus:before{content:''}html{font:600 1rem sans-serif;color:DimGray;background:Seashell;padding:1rem}</style></html>
```

In dark-mode
```
data:text/html;charset=UTF-8,<html contenteditable><style>*{line-height:1.6}html:before{content:'Start typing'}html:focus:before{content:''}html{font:600 1rem sans-serif;color:Gainsboro;background:DarkSlateGray;padding:1rem}</style></html>
```

Fancier version which lets you save the written contents as a text file (Ctrl + S)
```
data:text/html;charset=UTF-8,<html contenteditable class="fc"><style>*{line-height:1.6}.fc:before{content:'Start typing'}html{line-height:2;font:600 1rem sans-serif;color:DimGray;background:Seashell;padding:1rem}</style><script>const listen=(tg,ev,fn,ca)=>{const ve=ev.split(',').map(e =>e.trim()),ln=ve.length;ca=ca||false;for(let i=0;i<ln;i++){tg.addEventListener(ve[i],fn,ca);}};const find=(se,el,nl)=>{el=el||document;const qr=el.querySelectorAll(se);if(nl&&qr.length){return qr[0];}return qr;};const atr=(e,a,v)=>{e.setAttribute(a,v);};const has=(e,c)=>{return e.classList.contains(c);};const spec=(e)=>{if(e.ctrlKey||e.metaKey){return String.fromCharCode(e.which).toLowerCase();}return '';};const make=(t)=>{let u=URL.createObjectURL(new Blob([t],{type:'text/plain'})),a=document.createElement('a');atr(a,'href',u);atr(a,'download', 'editor.txt');a.click();document.body.removeChild(a);};let ht=find('html')[0];listen(ht,'focus',(e)=>{if(has(ht,'fc'))ht.classList.remove('fc');},true);listen(window,'keydown',(e)=>{let k=spec(e);if(k=='s'){e.preventDefault();make(find('body')[0].innerText);}},true);</script></html>
```

Fancy version in dark-mode
```
data:text/html;charset=UTF-8,<html contenteditable class="fc"><style>*{line-height:1.6}.fc:before{content:'Start typing'}html{line-height:2;font:600 1rem sans-serif;color:Gainsboro;background:DarkSlateGray;padding:1rem}</style><script>const listen=(tg,ev,fn,ca)=>{const ve=ev.split(',').map(e =>e.trim()),ln=ve.length;ca=ca||false;for(let i=0;i<ln;i++){tg.addEventListener(ve[i],fn,ca);}};const find=(se,el,nl)=>{el=el||document;const qr=el.querySelectorAll(se);if(nl&&qr.length){return qr[0];}return qr;};const atr=(e,a,v)=>{e.setAttribute(a,v);};const has=(e,c)=>{return e.classList.contains(c);};const spec=(e)=>{if(e.ctrlKey||e.metaKey){return String.fromCharCode(e.which).toLowerCase();}return '';};const make=(t)=>{let u=URL.createObjectURL(new Blob([t],{type:'text/plain'})),a=document.createElement('a');atr(a,'href',u);atr(a,'download', 'editor.txt');a.click();document.body.removeChild(a);};let ht=find('html')[0];listen(ht,'focus',(e)=>{if(has(ht,'fc'))ht.classList.remove('fc');},true);listen(window,'keydown',(e)=>{let k=spec(e);if(k=='s'){e.preventDefault();make(find('body')[0].innerText);}},true);</script></html>
```

