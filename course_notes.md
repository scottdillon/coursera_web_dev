# Coursera HTML, CSS, javascript for web development

### Lecture 4 - Basie HTML Document Structure
The bare minimum doc must have a `<!doctype html>` tag first, then a `<html>` tag with `<header>` and `<body>` tags in that order. The `<header>` usually has a `<meta>` tag along with a `<title>` tag.

```html
<!DOCTYPE html>
<html lang="en">

	<head>
	    <meta charset="UTF-8">
	    <title>Document</title>
	</head>
	<body>

	</body>
</html>
```
The body tag can have many different tags within it.

### Lecture 5: HTML content models
* Block level elements
* Inline elements

#### Block level elements
Render begins on a new line. May contain inline or other block level elements. Generally fits in the Flow Content category of HTML5 elements.

#### Inline level elements
Renders on the same line. May contain other inline elements.

Links:
[Wc3 Schools HTML Content Model Elements](https://www.w3.org/TR/2011/WD-html5-20110525/content-models.html)

Now instead of block and inline, the categories are Flow Content and Phrasing Content along with 5 other categories.

#### div and span elements
* div element is generic block level elements
* span is most basic inline element.

Cannot put flow content in phrasing content. So
`<span>This is my text <div>new text I like.</div></span>`
would produce an error because we start a div within a span tag.

### Lecture 6: Heading elements
Semantic html element refers to the element having some meaning to the content. Understanding is provided by the tag  to the content within it.

#### Headings
* `<h1>`, `<h2>`, `<h3>`, `<h4>`, `<h5>`, `<h6>`
These elements give structure. Don't use for decoration.
`<h1>` tag should be used for the text that the document is the most important and generalized description of the page.
Good h1 content helps SEO.

Use it and it should contain the wording that conveys the major topic of the page.

#### Other HTML5 Semantic tags
* `<header>` - contains header ifo for the page
* `<nav>` - contains navigation content
* `<h1>` - main header
* `<section>` -
* `<article>` - usually goes inside the article element.
* `<aside>` - related to main content but not directly
* `<footer>` -

These are all block level elements but make it easier to understand what is going on because they convey some meaning.

### Lecture 7: Lists
Groups related content.
* `<ul>` for unordered Lists
* `<ol>` for ordered, numbered Lists

### Lecture 8: HTML Character entity references
* `<` is represented by `&lt;`
* `>` is: `&gt;`
* `&` is: `&amp;`
* `©` is: `&copy;`
* `&nbsp` is a space that doesn't start a new line. Can use this to force text to be rendered together if it won't fit on the previous line. Don't use this for making a space between words.
* `&quot;` is a set of quotes that will be rendered correctly despite the text encoding.


### Lecture 9: Creating Links
Links are in the `<a>` element with the href attribute. href can be an absolute or relative url.

* `<a href="same-directory.html" title="same dir link">Linking to a file in the same directory</a>`
* `<a href="#section1">#section1</a>` where section refers to the `id` of another flow element like `section`, `article`.
* `<a href="same-directory.html" target="_blank">link</a>` forces the link to open another tab instead of leaving the current site.

### Lecture 10: Images
Use the `img` tag. Example:
* `<img src="picture-with-quote.jpg" width="400" height="235" alt="Picture with a quote">`

# Module 2: CSS

### CSS Rules
```css
p {
	color: blue;
}
```
* `p` is the selector
* `color` is the property
* `blue` is the value
* `color: blue;` is the declaration.

### Element, Class, ID selectors
Element selectors are when you specify the element name for the CSS rule. Like `p`, `div`, etc

A class selector is specified with a dot and then the name of the class. So `.header` for example.

```css
.header {
	color: blue;
}
```

An id selector is specified with a hash mark before the
name of the id. Like
```css
#name {
	color: blue;
}
```

### Grouping selectors
Separate different selectors with a comma. Like:

```css
div, .blue {
	color: blue;
}
```
will apply blue font color to all divs and to elements with `class="blue"`

### Lecture 14: Combining selectors
To add css to elements with a given class, you can combine the `p` selector with the `.big` selector like:

```css
p.big {
	font-size: 20px;
}
```

This targets every `p` element with `big` as the class.

#### Child selector

```css
article > p {
	color: blue;
}
```
Applies the blue color to every `p` element that is a child of the `article` element. Only affects direct child elements. So an
```html
<article>
	<div>
		<p>text</p>
	</div>
</article>
```
would not have the text affected.

#### Descendant selector
```css
article p {
	color: blue;
}
```
would affect any `p` that is inside an `article` element at any level.



### Lecture 15: Pseudo Class selectors
Pseudo class selectors are a combination of a selector along with a semicolon and some keyword to denote when teh user interacts with the element.

```css
a:link, a:visited {
	text-decoration: none;
	background-color: green;
	border: 1px solid blue;
	color:black;
	display: block;
	width: 200px;
	text-align: center;
	margin-bottom: 1px;
}
a:hover, a:active {
	background-color: red;
	color:purple;
}

/* targets only the 3rd li in the header */
header li:nth-child(3) {
	font-size: 24px;
}

/* to target every other element*/
section div:nth-child(odd) {
	background-color: gray;
}

/* target the 4th child of the div on hover*/
section div:nth-child(4):hover {
	background-color: green;
}
```

### Lecture 16: Style placement
Place styles in an external CSS file.

### Lecture 17: Conflict resolution
* Origin Precedence: Last declaration wins.
 * The last declaration in the HTML dominates.
* Declarations that do not conflict for the same element will **merge**
* Inheritance: Child elements inherit properties.
* The **most** specific selector combination wins.
  * Most specific is the `style="..."` selector in the html
  * Second is the ID attribute
  * the class, pseudo-class, attribute is third
  * Last is the number of elements used in selector combination.

An exclamation point important `!important` over-rides the specificity rules to apply CSS rules.

### Lecture 18: Styling text
[Here are Web Safe font combinations](https://www.w3schools.com/cssref/css_websafe_fonts.asp)
* `font-family`: "Times New Roman", Times, serif;
* `color` : #000ff; Hexadecimal is RGB corresponding to each pair of characters.
* `font-style`: italic; etc.
* `font-weight`: bold;
* `font-size`: 24px;
* `text-transform`: lowercase, capitalize, etc
* `text-align`: center, right, left justify.

##### Relative font Styling
* Percent - `font-size: 120%;`
* ems - `font-size: 2em;` relative to the font size when it was applied even
if after being increased already.
