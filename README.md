# Learn CSS: This will be a walkthrough of different CSS concepts and the models within CSS

## Getting Started With CSS

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
