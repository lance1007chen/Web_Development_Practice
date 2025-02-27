## CSS - Lemming Article

### Normalizing
```html
<link href="https://cdnjs.cloudflare.com/ajax/libs/normalize/8.0.1/normalize.min.css" rel="stylesheet">
```
This normalizes the way pages look across different browsers, since each browser has its own built in style sheet.

One of the things the normalized script does is it removes the padding from the body element on the page.

Before normalizing:
![9](https://live.staticflickr.com/65535/53827325345_24dab24565_o.jpg)

After normalizing:
![10](https://live.staticflickr.com/65535/53825971532_bb9d0133a6_o.jpg)

### Centering
```css
article {
	width: 700px;
	margin: auto;
}
```

`margin: auto` centers the whole page.

![11](https://live.staticflickr.com/65535/53825971527_0869527606_o.jpg)

### Color, Size, Font Family, and Line Height
```css
body {
	color: #545454;
	font-size: 1.5em;
	font-family: Georgia, 'Times New Roman', Times, serif;
}

p {
	line-height: 1.5em;
}
```

![12](https://live.staticflickr.com/65535/53827127863_67fd2237d9_o.jpg)

### Background Color
Background color on whole page:
```css
body {
	background-color: #d0d64c;
}
```

![13](https://live.staticflickr.com/65535/53827213179_8805a0ba1f_o.jpg)

Background color on article:
```css
article {
	background-color: white;
}
```

![14](https://live.staticflickr.com/65535/53827213164_81f327da89_o.jpg)

Padding on article:
```css
article {
	background-color: white;
	padding: 20px;
}
```

![15](https://live.staticflickr.com/65535/53825971497_8818e48a5a_o.jpg)

### Style on Headings
```css
h1, h2 {
	text-transform: uppercase;
	font-family: Arial;
	background-color: #575c04;
	color: #f4f5d6;
	padding: 10px;
}

h1 {
	text-align: center;
}
```

Comma means to apply this to both `h1` and `h2`.

This is taking advantage of the cascade on `h1`.

![16](https://live.staticflickr.com/65535/53827127838_15401cefaf_o.jpg)

### Style on Navigation
#### Unordered List Styling
Getting rid of bullet points:
```css
nav ul {
	list-style: none;
}
```

![17](https://live.staticflickr.com/65535/53825971467_96b0b3464a_o.jpg)

![18](https://live.staticflickr.com/65535/53827213129_62492d40d2_o.jpg)

Notice that in Inspect, by default the unordered list has margine (orange) and padding (green). To get rid of the padding:
```css!
nav ul {
	margin: 0;
	padding: 0;
}
```

![19](https://live.staticflickr.com/65535/53826888241_07f609edf3_o.jpg)

#### Anchor Tags Styling
```css
nav ul li a {
	display: block;
	text-decoration: none;
	background-color: brown;
	color: white;
	font-family: Arial;
	font-weight: bold;
	padding: 20px;
	border: 5px solid #510808;
	margin-bottom: 5px;
}
```

`display: block` makes the entire anchor tag clickable rather than just the text.

`text-decoration: none` gets rid of the underlines.

![20](https://live.staticflickr.com/65535/53827213114_a6c824231b_o.jpg)

#### Smooth Scroll
As for now, clicking on the navigation links jumps right to the section. To make the transition scroll smoother, add this to the stylesheet:

```css
html {
	scroll-behavior: smooth;
}
```
