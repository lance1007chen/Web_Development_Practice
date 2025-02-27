## Links

* By default, links are phrasing (or inline) elements.
* They must include an `href` attribute (hypertext reference).
* Can link to:
	* An html page on another website.
	* An html page on the same website.
	* A section within the same page.
	* A media file or some other file to be downloaded.
	* Nothing (a link can be empty).
* The content inside a link can be:
	* Text.
	* An image.
	* Another element.

### External Link
```html
<p>Here is an external link to
    <a href="http://google.com">Google</a> website.</p>
```

### Internal Link
#### Link to a Page in the Same Directory
File structure:
```
 |-- index.html
 |-- about.html
```

In `index.html`:
```html
<p>Here is a internal link to <a href="about.html">About Page</a>.</p>
```

#### Link to a Page in a Child Directory
File structure:
```
 |-- index.html
 |-- products
	 |-- cheese.html
```

In `index.html`:
```html
<p>We sell <a href="products/cheese.html">Cheeses</a>.</p>
```

In `products/cheese.html`:
```html
<p>Go back to <a href="../index.html">Home Page</a>.</p>
```

### Link to Nothing
```html
<p>Go to this <a href="#">link</a>.</p>
```
This link doesn't go anywhere. This can be used when a link is needed but the link to link to is not sure yet. Empty quotes won't work because they cause a syntax error.

### Link to Content on the Same Page
```html
<p>Here is a link to <a href="#contact">content on the page</a>.</p>
<section id="contact">
	<p>Here is the contact info.</p>
</section>
```
This links to content on the same page. For this to do something noticeable, there has to be enough content on the page to scroll. Also, by default the section will move to the top of the viewport, but only if there is enough content on the page after the section.
