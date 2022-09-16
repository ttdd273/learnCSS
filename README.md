# Learn CSS:

This will be a walkthrough of different CSS concepts and the models within CSS

# Getting Started With CSS

- You should include the line `<link rel="stylesheet" href="styles.css">` within `index.html`
- `<link>` element tells the browser that we have a stylesheet
  - `rel` attribute set to `stylesheet` indicates you have a stylsheet
  - `href` tells you the location of the stylesheet

## Changing the default behavior of elements

- Browsers have an internal stylesheet, but sometimes you might want to change it to your own desired setting
- To do this, you will need to specify your own CSS rules to override them
  - Ex: `li { list-style-type: none; }`

## Adding a Class

- So far, we've styled elements based on their names, but that's only if want all of them to be exactly the same
- Here, we need to add a `class` attribute
- In the CSS, you target the `class` by creating a selector that starts with `.`
- Somtimes, you can chain the selectors:
  - `.li.special {}`
  - This means target any `li` elements that has the class `special`
- Specifying other elements requires you to chain the selectors again:
  - `li.special, span.special {}`

## Styling things based on their location in a document

- For example, in the CSS for this section, we have an `<em>` element within an `li` element
  - To specify that, we can use `li em`
- This is called a **descendant combinator**, and takes the form of a space between two other selectors
- Something else that might also be common is to style a paragraph that comes directly after a heading
  - To do so, use `h1 + p {}`
- This is called an **adjacent sibling combinator**

## Styling things based on state

- Straight-forward example of this is styling links
- Links have different state depending whether it's been visited or not, being hovered over, focused via keyboard, etc.
- You can use CSS to target these different states
- Examples in the CSS file:
  - `a:link`, `a:visited`, `a:hover`

## Combining selectors and combinators

- You can also combine selectors and combinators
- Ex: `article p span {}`, selects any span that's inside a paragraph that's inside an article
- Ex: `h1 + ul + p`, selects any `p` tags that are after a `ul` that's after an `h1`
- `body h1 + p .special {}`, any `.special` classes that's within a `p` tag that follows an `h1` that's within the body.

# How is CSS structured?

## Applying CSS to HTML

There are three ways to apply CSS to HTML:

- External stylesheet
  - Contains CSS in a separate file with `.css` extension
  - Reference an external CSS stylesheet with `<link>` tag
  - Ex: `<link rel="stylesheet" href="styles.css" />`
  - `href` needs to be reference a file on your file system
- Internal stylesheet
  - Resides within an HTML document
  - Place CSS inside `<style>` element contained inside HTML `<head>`
  - Internal CSS might be useful in some circumstances, such as a content management system where you can't access the external CSS files
  - However, for sites with more than one page, it's not a good idea to use internal styling because you will need internal styling for every web page.
- Inline styles
  - CSS declaratons that affect a single element
  - Contained within a `style` attribute
  - **Avoid using CSS in this way, when possible.**
  - Least efficient implementation of CSS for maintenance
  - There are few circumstances where this is common:
    - Ex: HTML email to achieve compatibility with as many clients as possible
    - Ex: CMS only allows you edit the HTML body

### Selectors

Selector targets HTML to apply styles to content. If CSS is not applying the way you expected, then your selector may not match the way you think it should match.

- `h1`
- `a:link`
- `.manythings`
- `#onething`
- `*`
- `.box p`
- `.box p:first-child`
- `h1, h2, .intro`

#### Specificity

- Two selectors might select the same HTML element

```
.special {
  color: red;
}

p {
  color: blue;
}
```

- In our HTML, we have the following element: `<p> class="special">What color am I?</p>`
- We're unsure of whether the paragraph should be blue or red
- CSS language has rules that controls which selector is stronger
  - Called **casacde** and **specificity**
- In the example above, the paragraph will be blue, because the declaration that sets the text to blue appears layer in the stylesheet.
- **Cascading**: Later styles replace conflicting styles that appear earlier in the stylesheet
- **Specificity**: Class is rated as more specific than the element selector, so it cancels the other conflicting style declaration

```
p {
  color: red;
}

p {
  color: blue;
}
```

### Properties and Values

- Properties:
  - Human readable identifiers that indicate which stylistic features you want to modify
  - Ex: `font-size`, `width`, `background-color`
- Values:
  - Each property is assigned a value, this value indicates how to style the property
- When a property is paired with a value, this pairing is called a _CSS declaration_
- _CSS declarations_ are found within _CSS declaration blocks_
- _CSS declaration blocks_ are paired with _selectors_ to produce _CSS rulesets_ or _CSS rules_
- CSS properties and values are case-insensitive, and the pair is separated by a colon (`:`)

#### Functions

- There are some values that take the form of a function
- Ex: `calc()`

HTML:

```
<div class="outer">
 <div class="box">
   The inner box is 90% - 30px.
 </div>
</div>
```

CSS:

```
.outer {
  border: 5px solid black;
}

.box {
  padding: 10px;
  width: calc(90% - 30px);
  background-color: rebeccapurple;
  color: white;
}
```

- Function consists of the function name, and parentheses to enclose the values for the function.
- In the example, it's defined as 90% of the containing block width minus 30 pixels.

#### Transform Functions

- Ex: rotate()

HTML:

```
<div class="box"></div>
```

CSS:

```
.box {
  margin: 30px;
  width: 100px;
  height: 100px;
  background-color: rebeccapurple;
  transform: rotate(0.8turn);
}
```

### @rules

- Pronounced "at-rules", provide instructions for what the CSS should perform or how it should behave.
- Ex: `@import` imports a stylesheet into another CSS stylesheet

  - `@import "styles2.css"`
    One common @rule is `@media`, which is used to create media queries, which use conditional logic for applying CSS styling

- The stylesheet below defines a pink background for the `<body>` element, but the media query defines a blue background if the viewport is wider than 30em

CSS:

```
body {
  background-color: pink;
}

@media (min-width: 30em) {
  body {
    background-color: blue;
  }
}
```

### Shorthands

- Some properties are called **shorthand properties**, because we can set several values in a single line

- Padding and margin, shorthand is applied in the order top, right, bottom, left (clockwise from the top)
- There are also two-value shorthands, which set for top/bottom, left/right
  - Ex: `padding: 10px 15px 15px 5px;`

### Comments

- As with any coding work, it's best practice to write comments along the CSS, begins with `/*` and ends with `*/`

### White space

- White space means actual spaces, tabs, and new lines
- Browsers will ignore white space inside CSS, its value is in improving readability
- Each declaration (and rule start/end) has its own line. This is arguably a good way to write CSS.
- **Property names never have white spaces**
