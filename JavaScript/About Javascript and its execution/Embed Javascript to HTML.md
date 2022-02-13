# Embed JavaScript to HTML
## < script > tag usage (order is matter)
### 1. Use the < script > tag in the < head >
```html
<head>
	<script src="assets/scripts/app.js"></script>
</head>
<body>
	// html code
</body>
```

The script execution in this form will block the loading of the HTML document. Another disadvantage, when the script should reach a DOM element, it will throw an undefined error, because the HTML parsing and the DOM construction are not ready at the moment of the script execution. 


### 2. Use the < script > tag at the top of the < body >
```html
<body>
	<script src="assets/scripts/app.js"></script>
	<div id="root">
		<h2>Title</h2>
		<p>Paragraph</p>
	</div>
</body>
```

When the script tag is used at the beginning of the body tag, the script is still valid but because of the order, the same error occurs just like when using the script in the < head >. 


### 3. Use the < script > tag at the bottom of the < body >
```html
<body>
	<div id="root">
		<h2>Title</h2>
		<p>Paragraph</p>
	</div>
	<script src="assets/scripts/app.js"></script>
</body>
```

When the script tag is used at the bottom of the body tag, the script is still valid and the execution starts after the HTML parsing. In this case, the script can reach the HTML DOM elements without any error.  


### 4. Use the < script > tag in head tag with async
```html
<head>
	<script src="assets/scripts/app.js" async></script>
</head>
<body>
	// html code
</body>
```

When the script tag is used with `async`  the downloading of the script file starts when the parser hits the script tag but the HTML parsing is not blocked, and when the script file is fully downloaded, the script will be executed, no matter that the HTML parsing is finished or not. This could be useful, when the code that we want to run with the script does not rely on HTML content.  
 

### 5. Use the < script > tag in head tag with defer
```html
<head>
	<script src="assets/scripts/app.js" defer></script>
</head>
<body>
	// html code
</body>
```

When the script tag is used with `defer`  the downloading of the script file starts when the parser hits the script tag but the HTML parsing is not blocked, and when the HTML content has been parsed, the script will be executed. 


### 6. Javascript code between script tags without js file download
Of course, if the code injected manually between the script tags, there is not file that should be downloaded, in this case the [[Embed Javascript to HTML#4 Use the script tag in head tag with async|async]] or [[Embed Javascript to HTML#5 Use the script tag in head tag with defer|defer]] is meaningless. This scripts are always executed immediately. 


## < script > tag format 
TL;DR: **Script tag is NOT A SELF CLOSING TAG**

### Why self closing script tag does not work?

HTML5 has [five types of tags](https://html.spec.whatwg.org/multipage/syntax.html#elements-2) and only 'void' and 'foreign' tags are [allowed to be self-closing](https://html.spec.whatwg.org/multipage/syntax.html#syntax-tags).

Because `<script>` is not void (it _may_ have content) and is not foreign (like MathML or SVG), `<script>` **cannot be self-closed**, regardless of how you use it.

But why? Can't they regard it as foreign, make special case, or something?

HTML 5 aims to be [backward-compatible](https://html.spec.whatwg.org/multipage/introduction.html#history-2) with _implementations_ of HTML 4 and XHTML 1. It is not based on SGML or XML; its syntax is mainly concerned with documenting and uniting the implementations. (This is why `<br/>` `<hr/>` etc. are [valid HTML 5](https://html.spec.whatwg.org/multipage/syntax.html#start-tags) despite being invalid HTML4.)

Self-closing `<script>` is one of the tags where implementations used to differ. It [used to work in Chrome, Safari](https://www.webkit.org/blog/1273/the-html5-parsing-algorithm/), [and Opera](http://www.opera.com/docs/changelogs/windows/900b1/); to my knowledge it never worked in Internet Explorer or Firefox.

[This was discussed](http://lists.w3.org/Archives/Public/public-whatwg-archive/2009Aug/0101.html) when HTML 5 was being drafted and got rejected because it [breaks](http://lists.w3.org/Archives/Public/public-whatwg-archive/2009Aug/0104.html) [browser](http://lists.w3.org/Archives/Public/public-whatwg-archive/2009Aug/0117.html) [compatibility](http://lists.w3.org/Archives/Public/public-whatwg-archive/2009Aug/0119.html). Webpages that self-close script tag may not render correctly (if at all) in old browsers. There were [other proposals](http://lists.w3.org/Archives/Public/public-whatwg-archive/2009Aug/0384.html), but they can't solve the compatibility problem either.

After the draft was released, WebKit updated the parser to be in conformance.

**Self-closing `<script>` does not happen in HTML 5 because of backward compatibility to HTML 4 and XHTML 1.**