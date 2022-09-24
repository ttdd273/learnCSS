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
  - Contained within a `style` attributev
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

## How CSS works?

We will consider how the browser takes CSS and HTML and turns it into a webpage.

### How does CSS actually work?

- The browser must combine the document's content with its styling information

Below is a very simplified version of what actually happens in the background:

1. The browser loads HTML (e.g. receives from the network)
2. Converts the HTML into a DOM (Document Object Model). The DOM represents the document in the computer's memory.
3. The browser fetches most of the resources that are linked to by the HTML document, such as embedded images, videos, and even linked CSS, but JavaScript is handled a bit later.
4. The browser parses the fetched CSS, and sorts the different rules by their selector types into different "buckets", e.g. element, class, ID, and so on. Based on the selectors it finds, it works out which rules should be applied to which nodes in the DOM, and attaches style to them as required (this intermediate step is called a render tree).
5. The render tree is laid out in the structure it should appear in after the rules have been applied to it.
6. The visual display of the page is shown on the screen (this stage is called painting).

![Rendering](/assets/rendering.png)

### About the DOM

- DOM has a tree like structure. Each element, attribute, and piece of text in the markup language becomes a DOM node in the tree structure. The nodes are defined by their relationship to other DOM nodes. Some elements are parents of child nodes, and child nodes have siblings.
- The DOM is where your CSS and the document's content meet up.
- When you start working with browser DevTools you will be navigating the DOM as you select items in order to see which rules apply.

### A real DOM representation

- This is an example that converts HTML to a DOM representation

```
<p>
  Let's use:
  <span>Cascading</span>
  <span>Style</span>
  <span>Sheets</span>
</p>
```

- In the DOM, the node corresponding to `<p>` is the parent, and the children are a text node and three nodes corresponding to `<span>` element

```
P
├─ "Let's use:"
├─ SPAN
|  └─ "Cascading"
├─ SPAN
|  └─ "Style"
└─ SPAN
    └─ "Sheets"
```

### Applying CSS to the DOM

- Looking at the same HTML as above, and we want to apply the following CSS to the document

```
span {
  border: 1px solid black;
  background-color: lime;
}
```

- The browser parses the HTML and creates a DOM from it, then it parses the CSS
- Since the only rule available in the CSS has a span selector, the browser sorts the CSS very quickly! It applies that rule to each one of the three <span>s, then paints the final visual representation to the screen

### What happens if a browser encounters CSS it doesn't understand?

- The answer is that it does nothing and simply moves onto the next declaration
- Similarly, if a browser encounters a selector that it doesn't understand, it will just ignore the whole rule and move on to the next one.
- In the following example, the word color is spelled with British spelling, but only that specific line will marked as invalid

```
p {
  font-weight: bold;
  colour: blue; /* incorrect spelling of the color property */
  font-size: 200%;
}
```

- This behavior is very useful. It means that you can use new CSS as an enhancement, knowing that no error will occur if it is not understood — the browser will either get the new feature or not. This enables basic fallback styling.

- This is a good example with `calc()` function, which some browsers do not understand, and this works particularly well when you want to use a value that is quite new and not supported everywhere.
- For example, some older browsers do not support calc() as a value. I might give a fallback width for a box in pixels, then go on to give a width with a calc() value of 100% - 50px. Old browsers will use the pixel version, ignoring the line about calc() as they don't understand it. New browsers will interpret the line using pixels, but then override it with the line using calc() as that line appears later in the cascade.

```
.box {
  width: 500px;
  width: calc(100% - 50px);
}
```

### Assessment: Styling a Biography Page

-Make the level one heading pink, using the CSS color keyword hotpink.
-Give the heading a 10px dotted border-bottom which uses the CSS color keyword purple.
-Make the level 2 heading italic.
-Give the ul used for the contact details a background-color of #eeeeee, and a 5px solid purple border. Use some padding to push the content away from the border.
-Make the links green on hover.

# CSS Building Blocks

We will look at cacscade and inheritance, all the selector types that are available, units, sizing, styling backgrounds and borders, debugging, and more.

## Cascade and Inheritance

This controls how CSS is applied to HTML and how conflicts between style declarations are resolved.

### Conflicting Rules

- CSS stands for Cascading Style Sheets, and cascading is really important to understand
- Oftentimes when CSS is not working, it's probably because you've written a rule that overwrote one of the rules
- **Casacde** and **specificity** are mechanisms that control which rule applies when there is such a conflict. The rule that's styling your element may not be the one you expect, so you need to understand how these mechanisms work.
- Also important is the concept of **inheritance**, where elements might take the default values from its parent, but some other elements might not

### Cascade

- Stylesheets **cascade** — at a very simple level, this means that the origin, the cascade layer, and the order of CSS rules matter.
- As an example:

```
<h1>This is my heading.</h1>
```

The CSS are:

```
h1 {
    color: red;
}
h1 {
    color: blue;
}

```

- We have two rules that both apply to the `h1` element, but it ends up being colored blue, because both rules are from the same source, have an identical element selector, and therefore carries the same specificity, but the last one in the source order wins.

### Specificity

- **Specificity** is the algorithm that the browser uses to decide which property value is applied to an element.
- If multiple style blocks have different selectors that configure the same property with different values and target the same values, specificity decides the property value that gets applied to the element
- Basically a measure of how the selector's selection will be :
  - An element selector is less specific; it will select all elements of that type that appear on a page, so it has less weight.
  - A class selector is more specific; it will select only the elements on a page that have a specific class attribute value, so it has more weight.
- As an example:

```
.main-heading {
    color: red;
}

h1 {
    color: blue;
}
```

```
<h1 class="main-heading">This is my heading.</h1>
```

- The `h1` will be colored red because the class selector is more specific than an element selector, despite the element selector being lower than the class selector

### Inheritance

- This is important to understand because some CSS property values set on parent elements are inherited by their child elements, and some aren't.
- For example, if you set `color` attribute on `font-family` of an element, every element inside it will also be styled with that color and font, unless you've applied different color and font values directly to them
- Ex:

```
body {
    color: blue;
}

span {
    color: black;
}
```

```
<p>As the body has been set to have a color of blue this is inherited through the descendants.</p>
<p>We can change the color by targeting the element with a selector, such as this <span>span</span>.</p>
```

- Some values don't inherit, such as `width`. If you set `width` to 50%, all of its descendants don't get a width of 50%
- You will need to check each property's `Formal Definition` to check if it's inherited or not

### Understanding how the concepts work together

- You can use the browser's web tools to inspect a page's specificity, cascade, and more
- Firefox's DevTools are pretty similar to the ones in Chrome, the HTML is basically the DOM structure
- The rules panel is where you see these inheritance rules, etc.
- Cascade works by giving every selector and property a weight, and the weight in combination is what we call specificity
- The first is usually inline styles, which is applied directly to the element
- Then we have the selector block, which has less weight
- If there's a conflict, the one higher up on the list will override the ones lower in the list
- The `id` selector is also more specific than `class` selectors, so they are higher up in the selector
- There are also inherited styles a little lower
  - Main appears before HTML
  - These inherited values will be in the order of distance
- We can also see the browser styles that can be applied, go to settings to enable that, aka _user agent_ styles
- You can also turn on different states like hover, or add additional classes and add it through there
- There's also the computed tab
  - Just the properties that are applied, and for each property, where it came from, and what they are set to

### Understanding inheritance

- We will analyze the following example, the `color` property is an inherited property, so it is applied to direct children as well as indirect children
- Properties like `width`, `margin`, `padding`, and `border` are not inherited, and the reason is because if we increase the border for one element, then every single list and list item will also gain a border, which is definitely not intended

```
.main {
    color: rebeccapurple;
    border: 2px solid #ccc;
    padding: 1em;
}

.special {
    color: black;
    font-weight: bold;
}
```

```
<ul class="main">
    <li>Item One</li>
    <li>Item Two
        <ul>
            <li>2.1</li>
            <li>2.2</li>
        </ul>
    </li>
    <li>Item Three
        <ul class="special">
            <li>3.1
                <ul>
                    <li>3.1.1</li>
                    <li>3.1.2</li>
                </ul>
            </li>
            <li>3.2</li>
        </ul>
    </li>
</ul>

```

#### Controlling inheritance

- `inherit`: Sets the property value applied to a selected element to be the same as that of its parent element. Effectively, this "turns on inheritance".
- `initial`: Sets the property value applied to a selected element to the initial value of that property.
- `revert`: Resets the property value applied to a selected element to the browser's default styling rather than the defaults applied to that property. This value acts like unset in many cases.
- `revert-layer`: Resets the property value applied to a selected element to the value established in a previous cascade layer.
- `unset`: Resets the property to its natural value, which means that if the property is naturally inherited it acts like inherit, otherwise it acts like initial.

#### Resetting all property values

- The CSS shorthand property `all` can be used to apply one of these inheritance values to (almost) all properties at once. Its value can be any one of the inheritance values (`inherit`, `initial`, `revert`, `revert-layer`, or `unset`). It's a convenient way to undo changes made to styles so that you can get back to a known starting point before beginning new changes.

### Understanding the cascade

- We will now look at how cascade defines which CSS rules apply when more than one style block apply the same propety, but with different values, to the same element.
- There are three elements to soncider
  1. Source Order
  2. Specificity
  3. Importance

#### Source Order

- If you have more than one rule, all of which have exactly the same weight, then the one that comes last in the CSS will win.
- You can think of this as the rule that is nearer the element itself overwrites the earlier ones until the last one wins and gets to style the element.
- Source order only matters when the specificty weight of the rules is the same

#### Specificity

- You will often run into a situation where you know that a rule comes later in the stylesheet, but an earlier, conflicting rule is applied. This happens because the earlier rule has a **higher specificity** — it is more specific, and therefore, is being chosen by the browser as the one that should style the element.
- Although we are thinking about selectors and the rules that are applied, it isn't the entire rule that's overwritten, only the properties that are declared in multiple places.
- This behavior helps to avoid repetition in your CSS
  - A common practice is to definte generic styles for the basic elements, and then create classes for those that are different.
- As an example, we will `h1` with a generic styling, and then style the others with classes selectors

```
h2 {
    font-size: 2em;
    color: #000;
    font-family: Georgia, 'Times New Roman', Times, serif;
}

.small {
    font-size: 1em;
}

.bright {
    color: rebeccapurple;
}
```

```
<h2>Heading with no class</h2>
<h2 class="small">Heading with class of small</h2>
<h2 class="bright">Heading with class of bright</h2>
```

- How does a browser calculate specificity. Essentially, a value in points is awarded to different types of selectors, and adding these up gives you the weight of that particular selector, which can then be assessed against other potential matches.
- The amount of sepcificity a selector has is measured using three different values (or components), which can thought of as ID, CLASS, and ELEMENT columns in the hundreds, tens, and ones place:
  - **Identifiers**: Score one in this column for each ID selector contained inside the overall selector.
  - **Classes**: Score one in this column for each class selector, attribute selector, or pseudo-class contained inside the overall selector.
  - **Elements**: Score one in this column for each element selector or pseudo-element contained inside the overall selector.

| Selector               | Identifiers | Classes | Elements | Total Specificity |
| ---------------------- | ----------- | ------- | -------- | ----------------- |
| `h1 + p::first-letter` | 0           | 0       | 1        | 0-0-1             |

#### Inline styles

- Inlines styles take precedence over all normal styles, no matter the specificity. Their specificity can be continued as 1-0-0-0.

#### !important

- There's a special piece of CSS that you can use to overrule all of the above calculations, even the inline styles, the `!important` flag.
- You should be careful when using it, it is used to make an individual property and value pair the most specific rule, thereby overriding the normal rules of the cascade.
- The only way to override an important declaration is to include another important declaration with the _same specificity_ later in the source order, or one with higher specificity.
- One use case is when you're working on a CMS where you can't edit the CSS modules.

### The effect of CSS location

- It's possible to set custom stylesheets to override the developer's styles.
- It's also possible to declare developer styles in casacde layers: you can make non-layered styles override styles declared in layers or you can make styles declared in later layers override styles from earlier declared layers.
- As a developer, you may not be able to edit a third-party stylesheet, but you can import the external stylesheet into a cascade layer so that all your styles easily override the imported styles without worrying about third-party selector specificity.

#### Order of overriding declarations

Conflicting declarations will be applied in the following order, which later ones overriding earlier ones:

1. Declarations in user agent style sheets (e.g., the browser's default styles, used when no other styling is set).
2. Normal declarations in user style sheets (custom styles set by a user).
3. Normal declarations in author style sheets (these are the styles set by us, the web developers).
4. Important declarations in author style sheets.
5. Important declarations in user style sheets.
6. Important declarations in user agent style sheets.

- Note that the order of precedence is inverted for styles flagged with `!important`

#### Order of cascade layers

- When you declare CSS in cascade layers, the order of precedence is determined by the order in which the layers are declared.
- CSS styles declared outside of any layer are combined together, in the order in which those styles are declared, into an unnamed layer, as if it were the last declared layer.
- With competing normal styles, layer layers take precedence over earlier defined layers, but `!important` flag reverses the order
- Example:

```
@layer firstLayer, secondLayer;

p { /* 0-0-1 */
  background-color: red;
  color: grey !important;
  border: 5px inset purple;
}
p#addSpecificity { /* 1-0-1 */
  border-style: solid !important;
}

@layer firstLayer {
  #addSpecificity { /* 1-0-0 */
    background-color: blue;
    color: white !important;
    border-width: 5px;
    border-style: dashed !important;
  }
}

@layer secondLayer {
  p#addSpecificity { /* 1-0-1 */
    background-color: green;
    color: orange !important;
    border-width: 10px;
    border-style: dotted !important;
  }
}
```

```
<p id="addSpecificity">
  A paragraph with a border and background
</p>
```

- In here, two layers are defined, `firstLayer` and `secondLayer`
- Even though secondLayer is the highest, no properties from that declarations are used, because non-layered normal styles take precedence over layered normal styles, no matter the specificity, and important layered styles take precedence over important styles declared in layer layers.
-
