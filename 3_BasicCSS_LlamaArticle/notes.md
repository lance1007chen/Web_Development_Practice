## Basic CSS - Llama Article

In this lesson, some simple styling would be applied to this very simple web page.

![1](https://live.staticflickr.com/65535/53827325385_4bece497e8_o.jpg)

The big concepts in CSS (cascading style sheets) would be learnt, and a little syntax of the language would be worked with.

### Introduction to CSS
Add a style attribute to a paragraph.

```html!
<p style="">Llamas have an unusual reproductive cycle for a large animal. Female llamas are induced ovulators. Through the act of mating, the female releases an egg and is often fertilized on the first attempt. Female llamas do not go into estrus ("heat").</p>
```

---

Add a `color` property followed by a colon and a value, followed by a semicolon.

```html!
<p style="color:blue;">Llamas have an unusual reproductive cycle for a large animal. Female llamas are induced ovulators. Through the act of mating, the female releases an egg and is often fertilized on the first attempt. Female llamas do not go into estrus ("heat").</p>
```

<p style="color:blue;">Llamas have an unusual reproductive cycle for a large animal. Female llamas are induced ovulators. Through the act of mating, the female releases an egg and is often fertilized on the first attempt. Female llamas do not go into estrus ("heat").</p>

---

Add a `font-family` property.

```html!
<p style="color:blue; font-family:Times New Roman;">Llamas have an unusual reproductive cycle for a large animal. Female llamas are induced ovulators. Through the act of mating, the female releases an egg and is often fertilized on the first attempt. Female llamas do not go into estrus ("heat").</p>
```

<p style="color:blue; font-family:Times New Roman;">Llamas have an unusual reproductive cycle for a large animal. Female llamas are induced ovulators. Through the act of mating, the female releases an egg and is often fertilized on the first attempt. Female llamas do not go into estrus ("heat").</p>

---

Generally speaking, adding the style attribute is not the best practice, since it is not efficient. Have to put a style tag in each of the paragraph, which would take a long time to style all of the paragraphs. Also, it would muck up the nice, clean semantic HTML.

Instead, a better way would be to add style tags inside the head.

```html!
<head>
    <meta charset="UTF-8">
    <title>Llama Article</title>
    
    <style>
        p { color: blue; }
    </style>

</head>
```

![2](https://live.staticflickr.com/65535/53826888311_a9c7efaef3_o.jpg)

All the paragraphs are now blue.

---

If the inline style for one paragraph is changed to green, only that paragraph will display green. The rest will stay blue.

![3](https://live.staticflickr.com/65535/53827127923_9c00aafeb4_o.jpg)

CSS is made to handle conflicts. If the rules are equal, the one that loads last wins. Since the web page is rendered from top to bottom, the rule telling in to be green wins.

In fact, the Inspector in Chrome shows that `color:blue` is crossed out and `color:green` is applied. The Inspector can see which rules are being applied to each particular element. This is a great tool for troubleshooting the pages.

![4](https://live.staticflickr.com/65535/53826888296_490958b59e_o.png)

### Inheritance in CSS
If want everything to be blue, can do this:
```html!
<head>
    <meta charset="UTF-8">
    <title>Llama Article</title>
    
    <style>
        body { color: blue; }
    </style>

</head>
<body>
    ...
</body>
```

Everything inside the body will be blue, except the inline style for that one paragraph.

![5](https://live.staticflickr.com/65535/53827325370_ce31e01d39_o.jpg)

This is the concept of inheritance. All elements are inheriting styles from the parent `<body>` tag. However, not all styles are inherited. Only those reasonable will. (Can look up which styles are inherited.)

Features like inheritance allow CSS to be cleaner, leaner, and more efficient code.

As a side note, the prevalent way is to format for readability is:
```html!
<head>
    <meta charset="UTF-8">
    <title>Llama Article</title>
    
    <style>
        body {
            color: blue;
            font-family: Arial;
        }
    </style>

</head>
<body>
    ...
</body>
```
Each declaration has its own line.

### CSS Syntax
```html!
selector { declaration; }
```
Declaration consists of two parts:
```html!
selector { property: value; }
```
For example:
```html!
p { color: blue; }
```

Just as HTML is very simple with tags and attributes, CSS is very simple with selectors and declarations.

### Cascade in CSS
```html!
<style>

    body {
        color: blue;
        font-family: Arial;
    }

    p {
        line-height: 2em;
    }

</style>
```

The cascade is when one element is affected by multiple rules. That is, the way an element looks is due to a combination of rules. This combination of different rules to end up with one rendering is the cascade. With more practice, more and more efficient cascading can be acheived.

### Specificity in CSS
```html!
<style>

    .special {
        color: green;
    }

    body {
        color: blue;
        font-family: Arial;
    }

    p {
        line-height: 2em;
    }

</style>
```

```html!
<p class="special">Llamas have an unusual reproductive cycle for a large animal. Female llamas are induced ovulators. Through the act of mating, the female releases an egg and is often fertilized on the first attempt. Female llamas do not go into estrus ("heat").</p>
```

The rule `.special` targets elements with `class="special"`.

Remember that if two rules are equal, the one that loads last wins. Hence, one could think that `body` loads later than `.special`. However, the truth is that the rule `.special` is more specific, therefore it wins. A class selector is more specific than a tag selector.

![6](https://live.staticflickr.com/65535/53827213229_844926626c_o.png)

As seen, the Inspector in Chrome shows that `color: blue` is crossed out and overriden while `color: green` is applied. If a rule is more specific, that is, if it has more specificity, it wins.

---

```html!
<style>

    #extraspecial {
        color: red;
    }

    .special {
        color: green;
    }

    body {
        color: blue;
        font-family: Arial;
    }

    p {
        line-height: 2em;
    }

</style>
```

```html!
<p id="extraspecial" class="special">Llamas have an unusual reproductive cycle for a large animal. Female llamas are induced ovulators. Through the act of mating, the female releases an egg and is often fertilized on the first attempt. Female llamas do not go into estrus ("heat").</p>
```

`#extraspecial` targets `id="extraspecial"`. The dot targets elements with a class attribute, and the pound targets elements with an id attribute. The id attribute is already introduced in linking webpages. The id selector has even more specificity.

![7](https://live.staticflickr.com/65535/53827213214_6ebb6f8846_o.png)

Red is overriding green and blue.

Specificity from low to high is tag < class < id. Class can be used multiple times on a page, while id can only be used once (or else will get error in the validator). Id needs to be unique. Therefore, if want multiple elements to have a certain styling, use class. If want an element to have a unique styling, use id.

Of the three main things in CSS, which are inheritance, cascade, and specificity, when having trouble getting something to render, specificity is usually the culprit. When not expected, there is usually some other rule that is overriding it. To hunt it down, use the inspector to see which rules are being applied to any given element. Mastering specificity helps write more concise CSS. One should not use id on all the elements, which would cause using too many rules. Should use classes appropriately as well.

### Combinator Selectors
Combinator selectors are used when using more than one selector to target elements on a page.

```html!
section p {
    color: orange;
    line-height: normal;
    font-family: Gerogia;
}
```

```html!
<section>
    <h3>Mating</h3>
    <p>Llamas mate with ...</p>

    <h3>Gestation</h3>
    <p>The gestation period ...</p>
</section>
```

Only the paragraphs that are inside sections would apply.

---

The [descendant combinator](https://developer.mozilla.org/en-US/docs/Web/CSS/Descendant_combinator), typically represented by a single space (" ") character, combines two selectors such that elements matched by the second selector are selected if they have an ancestor (parent, parent's parent, parent's parent's parent, etc.) element matching the first selector. Selectors that utilize a descendant combinator are called descendant selectors.

#### Syntax
```html!
selector1 selector2 {
    /* property declarations */
}
```

#### Example
```html!
li {
    list-style-type: disc;
}

li li {
    list-style-type: circle;
}
```

```html!
<ul>
    <li>
        <div>Item 1</div>
        <ul>
            <li>Subitem A</li>
            <li>Subitem B</li>
        </ul>
    </li>
    <li>
        <div>Item 2</div>
        <ul>
            <li>Subitem A</li>
            <li>Subitem B</li>
        </ul>
    </li>
</ul>
```

![8](https://live.staticflickr.com/65535/53827213219_7cd2e72673_o.png)

### Linked Stylesheets
If there are many pages using similar styling, can reuse them for efficiency by putting them in an external linked file.

Add a self-closing link tag in the head tag. The link tag gets two attributes, hypertext reference and relationship attribute:
```html!
<head>
    <meta charset="UTF-8">
    <title>Llama Article</title>
    <link href="styles.css" rel="stylesheet">
</head>
```

Remove all the rules in the style tag and add it to the new file `styles.css`. Do not include the style tags.

The best practice is to put all the styles in a separate linked file to keep the HTMLs clean and semantically readable as possible. When linked to the same style sheet, changes made on the single style sheet can change it everywhere, which is more efficient.

### Key Terms
inheritance, cascade, specificity

rule, selector, declaration (property: value), class, id, compound selector
