# Browser Editor
In-browser quick text for simple notes

This is a snippet to turn a (non-mobile, in most cases) browser window into a very simple editor

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
data:text/html;charset=UTF-8,<html contenteditable class="fc"><style>*{line-height:1.6}.fc:before{content:'Start typing'}html{font:600 1rem sans-serif;color:DimGray;background:Seashell;padding:1rem}</style><script>const listen=(tg,ev,fn,ca)=>{const ve=ev.split(',').map(e =>e.trim()),ln=ve.length;ca=ca||false;for(let i=0;i<ln;i++){tg.addEventListener(ve[i],fn,ca);}};const find=(se,el,nl)=>{el=el||document;const qr=el.querySelectorAll(se);if(nl&&qr.length){return qr[0];}return qr;};const atr=(e,a,v)=>{e.setAttribute(a,v);};const has=(e,c)=>{return e.classList.contains(c);};const spec=(e)=>{if(e.ctrlKey||e.metaKey){return String.fromCharCode(e.which).toLowerCase();}return '';};const make=(t)=>{let u=URL.createObjectURL(new Blob([t],{type:'text/plain'})),a=document.createElement('a');atr(a,'href',u);atr(a,'download', 'editor.txt');a.click();document.body.removeChild(a);};let ht=find('html')[0];listen(ht,'focus',(e)=>{if(has(ht,'fc'))ht.classList.remove('fc');},true);listen(window,'keydown',(e)=>{let k=spec(e);if(k=='s'){e.preventDefault();make(find('body')[0].innerText);}},true);</script></html>
```

Fancy version in dark-mode
```
data:text/html;charset=UTF-8,<html contenteditable class="fc"><style>*{line-height:1.6}.fc:before{content:'Start typing'}html{font:600 1rem sans-serif;color:Gainsboro;background:DarkSlateGray;padding:1rem}</style><script>const listen=(tg,ev,fn,ca)=>{const ve=ev.split(',').map(e =>e.trim()),ln=ve.length;ca=ca||false;for(let i=0;i<ln;i++){tg.addEventListener(ve[i],fn,ca);}};const find=(se,el,nl)=>{el=el||document;const qr=el.querySelectorAll(se);if(nl&&qr.length){return qr[0];}return qr;};const atr=(e,a,v)=>{e.setAttribute(a,v);};const has=(e,c)=>{return e.classList.contains(c);};const spec=(e)=>{if(e.ctrlKey||e.metaKey){return String.fromCharCode(e.which).toLowerCase();}return '';};const make=(t)=>{let u=URL.createObjectURL(new Blob([t],{type:'text/plain'})),a=document.createElement('a');atr(a,'href',u);atr(a,'download', 'editor.txt');a.click();document.body.removeChild(a);};let ht=find('html')[0];listen(ht,'focus',(e)=>{if(has(ht,'fc'))ht.classList.remove('fc');},true);listen(window,'keydown',(e)=>{let k=spec(e);if(k=='s'){e.preventDefault();make(find('body')[0].innerText);}},true);</script></html>
```

## Expanded to readable form
This is the simple styling used
```
/* Gives everything an easy to read 1.6 line height */
* {
	line-height:1.6
}

/* Simple placeholder text */
.fc:before{
	content:'Start typing'
}

/*
Main document styling 
The dark-mode simply uses DarkSlateGray and Gainsboro as the background and foreground colors respectively
*/
html {
	font: 600 1rem sans-serif;
	color: DimGray;
	background: Seashell;
	padding: 1rem
}
```

JavaScript code
```
/**
 * Helper functions
 */

// Attach an event listener
const listen = ( tg, ev, fn, ca ) => {
	const 
	ve	= ev.split( ',' ).map( e => e.trim() ),
	ln	= ve.length;
	
	ca	= ca || false;
	
	for ( let i = 0; i < ln; i++ ) {
		tg.addEventListener( ve[i] , fn, ca );
	}
};

// Find a tag by name or attribute
const find = ( se, el, nl ) => {
	el		= el || document;
	const qr	= el.querySelectorAll( se );
	
	if( nl && qr.length ) {
		return qr[0];
	}
	return qr;
};

// Set element attribute
const atr = ( e, a, v ) => {
	e.setAttribute( a, v );
};

// Find if an element has an attribute in its class list
const has = ( e, c ) => {
	return e.classList.contains( c );
};

// Find the special function sent ( E.G. return "s" if "ctrl + s" was used )
const spec = ( e ) => {
	// Control/Command or alt key?
	if ( e.ctrlKey || e.metaKey ) {
		// Send back the character code in lowercase
		return String.fromCharCode(e.which).toLowerCase();
	}
	
	// Or send blank if not a command key
	return '';
};

// Prepare the content as a text file and enable download
const make = ( t ) => {
	
	let
	// Create a DOMString out of blob object
	u =	URL.createObjectURL( new Blob( [t], { type:'text/plain' } ) ),
	// Create a temporary anchor to force download
	a =	document.createElement('a');
	
	// Set the link href as the DOMString
	atr(a,'href',u);
	
	// File name as 'editor.txt'
	atr(a,'download', 'editor.txt');
	
	// Force download
	a.click();
	
	// Cleanup
	document.body.removeChild(a);
};


/**
 * Core functionality
 */


// Find the primary contenteditable HTML element 
let ht = find('html')[0];

// Remove the placeholder text if this is the first time
listen( ht, 'focus', ( e ) => {
	// Make sure if the class is still there to be removed
	if( has( ht,'fc') ) {
		ht.classList.remove('fc');
	}
}, true );

// Intercept Ctrl + S to save contents as a text file
listen( window,'keydown',( e ) => {
	// Is this a save command?
	let k=spec(e);if(k=='s'){
		// Prevent browser saving
		e.preventDefault();
		
		// ...and move on to text file saving
		make( find( 'body' )[0].innerText );
	}
}, true );

```
