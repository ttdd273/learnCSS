# CSS styling text

With the basics of the CSS language covered, the next CSS topic for you to concentrate on is styling text — one of the most common things you'll do with CSS. Here we look at text styling fundamentals including setting font, boldness, italics, line and letter spacing, drop shadows, and other text features. We round off the module by looking at applying custom fonts to your page, and styling lists and links.

# Fundamental text and font styling

We'll go through all the basic fundamentals of text/font styling in detail, including setting font weight, family and style, font shorthand, text alignment and other effects, and line and letter spacing.

## What is involved in styling text in CSS?

- Text inside an element is laid out inside the element's content box.
- It starts at the top left of the content area (or the top right, in the case of RTL language content), and flows towards the end of the line.
- Once it reaches the end, it goes down to the next line and flows to the end again. This pattern repeats until all the content has been placed in the box.
- Text content effectively behaves like a series of inline elements, being laid out on lines adjacent to one another, and not creating line breaks until the end of the line is reached, or unless you force a line break manually using the `<br>` element.
- The CSS properties used to style text generally fall into two categories:
  - **Font styles**: Properties that affect a text's font, e.g., which font gets applied, its size, and whether it's bold, italic, etc.
  - **Text layout styles**: Properties that affect the spacing and other layout features of the text, allowing manipulation of, for example, the space between lines and letters, and how the text is aligned within the content box.
- Note: Bear in mind that the text inside an element is all affected as one single entity. You can't select and style subsections of text unless you wrap them in an appropriate element (such as a `<span>` or `<strong>`), or use a text-specific pseudo-element like `::first-letter` (selects the first letter of an element's text), `::first-line` (selects the first line of an element's text), or `::selection` (selects the text currently highlighted by the cursor).

## Fonts

- We will apply some CSS properties to the following HTML:

```
<h1>Tommy the cat</h1>

<p>Well I remember it as though it were a meal ago…</p>

<p>
  Said Tommy the Cat as he reeled back to clear whatever foreign matter may have
  nestled its way into his mighty throat. Many a fat alley rat had met its
  demise while staring point blank down the cavernous barrel of this awesome
  prowling machine. Truly a wonder of nature this urban predator — Tommy the cat
  had many a story to tell. But it was a rare occasion such as this that he did.
</p>
```

### Color

- The `color` property sets the color of the foreground content of the selected elements, which is usually the text, but can also include a couple of other things, such as an underline or overline placed on text using the `text-decoration` property.

- `color` can accept any CSS color unit, for example:

```
p {
  color: red;
}
```

### Font families

- To set a different font for your text, you use the `font-family` property: this allows you to specify a font (or list of fonts) for the browser to apply to the selected elements. The browser will only apply a font if it is available on the machine the website is being accessed on; if not, it will just use a browser default font. A simple example looks like so:

```
p {
  font-family: arial;
}
```

- This would make all paragraphs on a page adopt the arial font, which is found on any computer.

#### Web safe fonts

- Speaking of font availability, there are only a certain number of fonts that are generally available across all systems and can therefore be used without much worry. These are the so-called **web safe fonts**.

- Most of the time, as web developers we want to have more specific control over the fonts used to display our text content. The problem is to find a way to know which font is available on the computer used to see our web pages. There is no way to know this in every case, but the web safe fonts are known to be available on nearly all instances of the most used operating systems (Windows, macOS, the most common Linux distributions, Android, and iOS).

- The list of actual web safe fonts will change as operating systems evolve, but it's reasonable to consider the following fonts web safe, at least for now (many of them have been popularized thanks to the Microsoft Core fonts for the Web initiative in the late 90s and early 2000s):

| Name            | Generic type | Notes                                                                                                                                                                                                                                     |
| --------------- | ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Arial           | sans-serif   | It's often considered best practice to also add Helvetica as a preferred alternative to Arial as, although their font faces are almost identical, Helvetica is considered to have a nicer shape, even if Arial is more broadly available. |
| Courier New     | monospace    | Some OSes have an alternative (possibly older) version of the Courier New font called Courier. It's considered best practice to use both with Courier New as the preferred alternative.                                                   |
| Georgia         | serif        |                                                                                                                                                                                                                                           |
| Times New Roman | serif        | Some OSes have an alternative (possibly older) version of the Times New Roman font called Times. It's considered best practice to use both with Times New Roman as the preferred alternative.                                             |
| Trebuchet MS    | sans-serif   | You should be careful with using this font — it isn't widely available on mobile OSes.                                                                                                                                                    |
| Verdana         | sans-serif   |                                                                                                                                                                                                                                           |

### Default fonts

- CSS defines five generic names for fonts: `serif`, `sans-serif`, `monospace`, `cursive`, and `fantasy`. These are very generic and the exact font face used from these generic names can vary between each browser and each operating system that they are displayed on. It represents a worst case scenario where the browser will try its best to provide a font that looks appropriate. `serif`, `sans-serif`, and `monospace` are quite predictable and should provide something reasonable. On the other hand, `cursive` and `fantasy` are less predictable and we recommend using them very carefully, testing as you go.

| Term       | Definition                                                                                                            |
| ---------- | --------------------------------------------------------------------------------------------------------------------- |
| serif      | Fonts that have serifs (the flourishes and other small details you see at the ends of the strokes in some typefaces). |
| sans-serif | Fonts that don't have serifs.                                                                                         |
| monospace  | Fonts where every character has the same width, typically used in code listings.                                      |
| cursive    | Fonts that are intended to emulate handwriting, with flowing, connected strokes.                                      |
| fantasy    | Fonts that are intended to be decorative.                                                                             |

### Font stacks

- Since you can't guarantee the availability of the fonts you want to use on your webpages (even a web font could fail for some reason), you can supply a **font stack** so that the browser has multiple fonts it can choose from. This involves a `font-family` value consisting of multiple font names separated by commas, e.g.,

```
p {
  font-family: "Trebuchet MS", Verdana, sans-serif;
}
```

- In such a case, the browser starts at the beginning of the list and looks to see if that font is available on the machine. If it is, it applies that font to the selected elements. If not, it moves on to the next font, and so on.
- It is a good idea to provide a suitable generic font name at the end of the stack so that if none of the listed fonts are available, the browser can at least provide something approximately suitable. To emphasize this point, paragraphs are given the browser's default serif font if no other option is available — which is usually Times New Roman — this is no good for a sans-serif font!

### A font-family example

```
p {
  color: red;
  font-family: Helvetica, Arial, sans-serif;
}
```

- Applying this to the previous example, you will claerly see the difference between `serif` and `sans-serif`

### Font size

- Font size (set with the `font-size` property) can take values measured in most of these units (and others, such as percentages); however, the most common units you'll use to size text are:
  - `px` (pixels): The number of pixels high you want the text to be. This is an absolute unit — it results in the same final computed value for the font on the page in pretty much any situation.
  - `ems`: 1 `em` is equal to the font size set on the parent element of the current element we are styling (more specifically, the width of a capital letter M contained inside the parent element). This can become tricky to work out if you have a lot of nested elements with different font sizes set, but it is doable, as you'll see below. Why bother? It is quite natural once you get used to it, and you can use em to size everything, not just text. You can have an entire website sized using `em`, which makes maintenance easy.
  - `rems`: These work just like `em`, except that 1 `rem` is equal to the font size set on the root element of the document (i.e. `<html>`), not the parent element. This makes doing the maths to work out your font sizes much easier, although if you want to support really old browsers, you might struggle — `rem` is not supported in Internet Explorer 8 and below.
- The `font-size` of an element is inherited from that element's parent element. This all starts with the root element of the entire document — `<html>` — the standard `font-size` of which is set to 16px across browsers. Any paragraph (or another element that doesn't have a different size set by the browser) inside the root element will have a final size of 16 px. Other elements may have different default sizes. For example, an `<h1>` element has a size of 2 `em` set by default, so it will have a final size of 32 `px`.
- Things become more tricky when you start altering the font size of nested elements. For example, if you had an `<article>` element in your page, and set its `font-size` to 1.5 `em` (which would compute to 24 `px` final size), and then wanted the paragraphs inside the `<article>` elements to have a computed font size of 20 `px`, what `em` value would you use?
  - It should be $\frac{20}{24} = \frac{5}{6}$ `em` units

```
<!-- document base font-size is 16px -->
<article>
  <!-- If my font-size is 1.5em -->
  <p>My paragraph</p>
  <!-- How do I compute to 20px font-size? -->
</article>
```

- The maths can be complicated, so you need to be careful about how you style things. It is best to use `rem` where you can to keep things simple, and avoid setting the `font-size` of container elements where possible.

### Font style, font weight, text transform, and text decoration

- CSS provides four common properties to alter the visual weight/emphasis of text:
  - `font-style`: Used to turn italic text on or off. Possible values are as follows (you'll rarely use this, unless you want to turn some italic styling off for some reason):
    - `normal`: Sets the text to the normal font (turns existing italics off).
    - `italic`: Sets the text to use the italic version of the font, if available; if not, it will simulate italics with oblique instead.
    - `oblique`: Sets the text to use a simulated version of an italic font, created by slanting the normal version.
  - `font-weight`: Sets how bold the text is. This has many values available in case you have many font variants available (such as -light, -normal, -bold, -extrabold, -black, etc.), but realistically you'll rarely use any of them except for `normal` and `bold`:
    - `normal`, `bold`: Normal and bold font weight.
    - `lighter`, `bolder`: Sets the current element's boldness to be one step lighter or heavier than its **parent** element's boldness.
    - `100`–`900`: Numeric boldness values that provide finer grained control than the above keywords, if needed.
  - `text-transform`: Allows you to set your font to be transformed. Values include:
    - `none`: Prevents any transformation.
    - `uppercase`: Transforms all text to capitals.
    - `lowercase`: Transforms all text to lower case.
    - `capitalize`: Transforms all words to have the first letter capitalized.
    - `full-width`: Transforms all glyphs to be written inside a fixed-width square, similar to a monospace font, allowing aligning of, e.g., Latin characters along with Asian language glyphs (like Chinese, Japanese, Korean).
  - `text-decoration`: Sets/unsets text decorations on fonts (you'll mainly use this to unset the default underline on links when styling them). Available values are:
    - `none`: Unsets any text decorations already present.
    - `underline`: Underlines the text.
    - `overline`: Gives the text an overline.
    - `line-through`: Puts a strikethrough over the text.
- You should note that `text-decoration` can accept multiple values at once if you want to add multiple decorations simultaneously, for example, `text-decoration: underline overline`.
- Also note that `text-decoration` is a shorthand property for `text-decoration-line`, `text-decoration-style`, and `text-decoration-color`. You can use combinations of these property values to create interesting effects, for example: `text-decoration: line-through red wavy`.

```
html {
  font-size: 10px;
}

h1 {
  font-size: 5rem;
  text-transform: capitalize;
}

h1 + p {
  font-weight: bold;
}

p {
  font-size: 1.5rem;
  color: red;
  font-family: Helvetica, Arial, sans-serif;
}
```

### Text drop shadows

- You can apply drop shadows to your text using the `text-shadow` property. This takes up to four values, as shown in the example below:

```
text-shadow: 4px 4px 5px red;
```

- The four properties are as follows:
  1. The horizontal offset of the shadow from the original text — this can take most available CSS length and size units, but you'll most commonly use `px`; positive values move the shadow right, and negative values left. This value has to be included.
  2. The vertical offset of the shadow from the original text. This behaves similarly to the horizontal offset, except that it moves the shadow up/down, not left/right. This value has to be included.
  3. The blur radius: a higher value means the shadow is dispersed more widely. If this value is not included, it defaults to 0, which means no blur. This can take most available CSS length and size units.
  4. The base color of the shadow, which can take any CSS color unit. If not included, it defaults to `currentcolor`, i.e. the shadow's color is taken from the element's `color` property.

#### Multiple shadows

- You can apply multiple shadows to the same text by including multiple shadow values separated by commas, for example:

```
h1 {
  text-shadow: 1px 1px 1px red, 2px 2px 1px red;
}
```

## Text layout

- With basic font properties out of the way, let's have a look at properties we can use to affect text layout.

### Text alignment

- The `text-align` property is used to control how text is aligned within its containing content box. The available values are listed below. They work in pretty much the same way as they do in a regular word processor application:
  - `left`: Left-justifies the text.
  - `right`: Right-justifies the text.
  - `center`: Centers the text.
  - `justify`: Makes the text spread out, varying the gaps in between the words so that all lines of text are the same width. You need to use this carefully — it can look terrible, especially when applied to a paragraph with lots of long words in it. If you are going to use this, you should also think about using something else along with it, such as `hyphens`, to break some of the longer words across lines.
- Example: (Tommy the cat is now centered)

```
html {
  font-size: 10px;
}

h1 {
  font-size: 5rem;
  text-transform: capitalize;
  text-shadow: 1px 1px 1px red, 2px 2px 1px red;
  text-align: center;
}

h1 + p {
  font-weight: bold;
}

p {
  font-size: 1.5rem;
  color: red;
  font-family: Helvetica, Arial, sans-serif;
}
```

### Line height

- The line-height property sets the height of each line of text.
- This property can not only take most length and size units, but can also take a unitless value, which acts as a multiplier and is generally considered the best option.
- With a unitless value, the font-size gets multiplied and results in the line-height.
- Body text generally looks nicer and is easier to read when the lines are spaced apart. The recommended line height is around 1.5 – 2 (double spaced). To set our lines of text to 1.6 times the height of the font, we'd use:

```
p {
  line-height: 1.6;
}
```

### Letter and word spacing

- The `letter-spacing` and `word-spacing` properties allow you to set the spacing between letters and words in your text. You won't use these very often, but might find a use for them to obtain a specific look, or to improve the legibility of a particularly dense font. They can take most length and size units.
- To illustrate, we could apply some word- and letter-spacing to the first line of each `<p>` element in our HTML sample with:

```
p::first-line {
  letter-spacing: 4px;
  word-spacing: 4px;
}
```

### Other properties worth looking at

- Font styles:
  - `font-variant`: Switch between small caps and normal font alternatives.
  - `font-kerning`: Switch font kerning options on and off.
  - `font-feature-settings`: Switch various OpenType font features on and off.
  - `font-variant-alternates`: Control the use of alternate glyphs for a given font-face.
  - `font-variant-caps`: Control the use of alternate capital glyphs.
  - `font-variant-east`-asian: Control the usage of alternate glyphs for East Asian scripts, like Japanese and Chinese.
  - `font-variant-ligatures`: Control which ligatures and contextual forms are used in text.
  - `font-variant-numeric`: Control the usage of alternate glyphs for numbers, fractions, and ordinal markers.
  - `font-variant-position`: Control the usage of alternate glyphs of smaller sizes positioned as superscript or subscript.
  - `font-size-adjust`: Adjust the visual size of the font independently of its actual font size.
  - `font-stretch`: Switch between possible alternative stretched versions of a given font.
  - `text-underline-position`: Specify the position of underlines set using the text-decoration-line property underline value.
  - `text-rendering`: Try to perform some text rendering optimization.
- Text layout styles:
  - `text-indent`: Specify how much horizontal space should be left before the beginning of the first line of the text content.
  - `text-overflow`: Define how overflowed content that is not displayed is signaled to users.
  - `white-space`: Define how whitespace and associated line breaks inside the element are handled.
  - `word-break`: Specify whether to break lines within words.
  - `direction`: Define the text direction. (This depends on the language and usually it's better to let HTML handle that part as it is tied to the text content.)
  - `hyphens`: Switch on and off hyphenation for supported languages.
  - `line-break`: Relax or strengthen line breaking for Asian languages.
  - `text-align-last`: Define how the last line of a block or a line, right before a forced line break, is aligned.
  - `text-orientation`: Define the orientation of the text in a line.
  - `overflow-wrap`: Specify whether or not the browser may break lines within words in order to prevent overflow.

## Font shorthand

- Many font properties can also be set through the shorthand property `font`. These are written in the following order: `font-style`, `font-variant`, `font-weight`, `font-stretch`, `font-size`, `line-height`, and `font-family`.
- Among all those properties, only `font-size` and `font-family` are required when using the `font` shorthand property.
- A forward slash has to be put in between the `font-size` and `line-height` properties.

```
font: italic normal bold normal 3em/1.5 Helvetica, Arial, sans-serif;
```

# Styling lists

- Lists behave like any other text for the most part, but there are some CSS properties specific to lists that you need to know about, as well as some best practices to consider.

## A simple list example

- We'll look at unordered, ordered, and description lists — all have styling features that are similar, as well as some that are particular to themselves.

```
<h2>Shopping (unordered) list</h2>

<p>
  Paragraph for reference, paragraph for reference, paragraph for reference,
  paragraph for reference, paragraph for reference, paragraph for reference.
</p>

<ul>
  <li>Hummus</li>
  <li>Pita</li>
  <li>Green salad</li>
  <li>Halloumi</li>
</ul>

<h2>Recipe (ordered) list</h2>

<p>
  Paragraph for reference, paragraph for reference, paragraph for reference,
  paragraph for reference, paragraph for reference, paragraph for reference.
</p>

<ol>
  <li>Toast pita, leave to cool, then slice down the edge.</li>
  <li>
    Fry the halloumi in a shallow, non-stick pan, until browned on both sides.
  </li>
  <li>Wash and chop the salad.</li>
  <li>Fill pita with salad, hummus, and fried halloumi.</li>
</ol>

<h2>Ingredient description list</h2>

<p>
  Paragraph for reference, paragraph for reference, paragraph for reference,
  paragraph for reference, paragraph for reference, paragraph for reference.
</p>

<dl>
  <dt>Hummus</dt>
  <dd>
    A thick dip/sauce generally made from chick peas blended with tahini, lemon
    juice, salt, garlic, and other ingredients.
  </dd>
  <dt>Pita</dt>
  <dd>A soft, slightly leavened flatbread.</dd>
  <dt>Halloumi</dt>
  <dd>
    A semi-hard, unripened, brined cheese with a higher-than-usual melting
    point, usually made from goat/sheep milk.
  </dd>
  <dt>Green salad</dt>
  <dd>That green healthy stuff that many of us just use to garnish kebabs.</dd>
</dl>
```

- Using the developer web tools, we can see that:
  - The `<ul>` and `<ol>` elements have a top and bottom margin of 16px (1em) and a padding-left of 40px (2.5em).
  - The list items (`<li>` elements) have no set defaults for spacing.
  - The `<dl>` element has a top and bottom margin of 16px (1em), but no padding set.
  - The `<dd>` elements have margin-left of 40px (2.5em).
  - The `<p>` elements we've included for reference have a top and bottom margin of 16px (1em) — the same as the different list types.

## Handling list spacing

- When styling lists, you need to adjust their styles so they keep the same vertical spacing as their surrounding elements (such as paragraphs and images; sometimes called vertical rhythm), and the same horizontal spacing as each other.

```
/* General styles */

html {
  font-family: Helvetica, Arial, sans-serif;
  font-size: 10px;
}

h2 {
  font-size: 2rem;
}

ul,
ol,
dl,
p {
  font-size: 1.5rem;
}

li,
p {
  line-height: 1.5;
}

/* Description list styles */

dd,
dt {
  line-height: 1.5;
}

dt {
  font-weight: bold;
}
```

- The first rule sets a sitewide font and a baseline font size of 10px. These are inherited by everything on the page.
- Rules 2 and 3 set relative font sizes for the headings, different list types (the children of the list elements inherit these), and paragraphs. This means that each paragraph and list will have the same font size and top and bottom spacing, helping to keep the vertical rhythm consistent.
- Rule 4 sets the same `line-height` on the paragraphs and list items — so the paragraphs and each individual list item will have the same spacing between lines. This will also help to keep the vertical rhythm consistent.
- Rules 5 and 6 apply to the description list. We set the same `line-height` on the description list terms and descriptions as we did with the paragraphs and list items. Again, consistency is good! We also make the description terms have bold font, so they visually stand out easier.

### List specific styles

- Now that we've looked at general spacing techniques for lists, let's explore some list-specific properties. There are three properties you should know about to start with, which can be set on `<ul>` or `<ol>` elements:
  - `list-style-type`: Sets the type of bullets to use for the list, for example, square or circle bullets for an unordered list, or numbers, letters, or roman numerals for an ordered list.
  - `list-style-position`: Sets whether the bullets, at the start of each item, appear inside or outside the lists.
  - `list-style-image`: Allows you to use a custom image for the bullet, rather than a simple square or circle.

#### Bullet styles

- Here's an example that uses Roman numerals:

```
ol {
  list-style-type: upper-roman;
}
```

- More options can be found in the `list-style-type` reference page.

#### Bullet position

- The `list-style-position` property sets whether the bullets appear inside the list items, or outside them before the start of each item. The default value is outside, which causes the bullets to sit outside the list items.
- If you set the value to inside, the bullets will sit inside the lines:
  - It will appear as if the bullets are part of the same line.

```
ol {
  list-style-type: upper-roman;
  list-style-position: inside;
}
```

#### Using a custom bullet image

```
ul {
  list-style-image: url(star.svg);
}
```

- However, this property is a bit limited in terms of controlling the position, size, etc. of the bullets. You are better off using the `background` family of properties, which you've learned in the Backgrounds and borders article. For now, here's a taster!
- Here's an example:

```
ul {
  padding-left: 2rem;
  list-style-type: none;
}

ul li {
  padding-left: 2rem;
  background-image: url(star.svg);
  background-position: 0 0;
  background-size: 1.6rem 1.6rem;
  background-repeat: no-repeat;
}
```

- Set the `padding-left` of the `<ul>` down from the default `40px` to `20px`, then set the same amount on the list items. This is so that, overall, the list items are still lined up with the order list items and the description list descriptions, but the list items have some padding for the background images to sit inside. If we didn't do this, the background images would overlap with the list item text, which would look messy.
- Set the `list-style-type` to `none`, so that no bullet appears by default. We're going to use `background` properties to handle the bullets instead.
- Inserted a bullet onto each unordered list item. The relevant properties are as follows:
  - `background-image`: This references the path to the image file you want to use as the bullet.
  - `background-position`: This defines where in the background of the selected element the image will appear — in this case we are saying `0 0`, which means the bullet will appear in the very top left of each list item.
  - `background-size`: This sets the size of the background image. We ideally want the bullets to be the same size as the list items (or very slightly smaller or larger). We are using a size of `1.6rem` (`16px`), which fits very nicely with the `20px` padding we've allowed for the bullet to sit inside — `16px` plus `4px` of space between the bullet and the list item text works well.
  - `background-repeat`: By default, background images repeat until they fill up the available background space. We only want one copy of the image inserted in each case, so we set this to a value of `no-repeat`.

#### list-style shorthand

- The three properties mentioned above can all be set using a single shorthand property, `list-style`. For example, the following CSS:

```
ul {
  list-style-type: square;
  list-style-image: url(example.png);
  list-style-position: inside;
}
```

- Could be replaced by:

```
ul {
  list-style: square url(example.png) inside;
}
```

- The values can be listed in any order, and you can use one, two, or all three (the default values used for the properties that are not included are `disc`, `none`, and `outside`). If both a `type` and an `image` are specified, the type is used as a fallback if the image can't be loaded for some reason.

### Controlling list counting

- Sometimes you might want to count differently on an ordered list — e.g., starting from a number other than 1, or counting backwards, or counting in steps of more than 1. HTML and CSS have some tools to help you here.

#### start

- The `start` attribute allows you to start the list counting from a number other than 1. The following example:

```
<ol start="4">
  <li>Toast pita, leave to cool, then slice down the edge.</li>
  <li>
    Fry the halloumi in a shallow, non-stick pan, until browned on both sides.
  </li>
  <li>Wash and chop the salad.</li>
  <li>Fill pita with salad, hummus, and fried halloumi.</li>
</ol>
```

- Will give you 4, 5, 6, 7.

#### reversed

- The `reversed` attribute will start the list counting down instead of up. The following example:

```
<ol start="4" reversed>
  <li>Toast pita, leave to cool, then slice down the edge.</li>
  <li>
    Fry the halloumi in a shallow, non-stick pan, until browned on both sides.
  </li>
  <li>Wash and chop the salad.</li>
  <li>Fill pita with salad, hummus, and fried halloumi.</li>
</ol>
```

- Will give you 4, 3, 2, 1.

#### value

- The `value` attribute allows you to set your list items to specific numerical values. The following example:

```
<ol>
  <li value="2">Toast pita, leave to cool, then slice down the edge.</li>
  <li value="4">
    Fry the halloumi in a shallow, non-stick pan, until browned on both sides.
  </li>
  <li value="6">Wash and chop the salad.</li>
  <li value="8">Fill pita with salad, hummus, and fried halloumi.</li>
</ol>
```

# Styling Links

- When styling links, it's important to understand how to make use of pseudo-classes to style their states effectively. It's also important to know how to style links for use in common interface features whose content varies, such as navigation menus and tabs. We'll look at both these topics in this article.

## Let's look at some links

### Link states

- The first thing to understand is the concept of link states — different states that links can exist in. These can be styled using different pseudo-classes:
  - `Link`: A link that has a destination (i.e., not just a named anchor), styled using the `:link` pseudo class.
  - `Visited`: A link that has already been visited (exists in the browser's history), styled using the `:visited` pseudo class.
  - `Hover`: A link that is hovered over by a user's mouse pointer, styled using the `:hover` pseudo class.
  - `Focus`: A link that is focused (e.g., moved to by a keyboard user using the `Tab` key or something similar, or programmatically focused using `HTMLElement.focus()`) — this is styled using the `:focus` pseudo class.
  - `Active`: A link that is activated (e.g., clicked on), styled using the `:active` pseudo class.

### Default styles

- The following example illustrates what a link will behave like by default (the CSS is enlarging and centering the text to make it stand out more).

```
<p><a href="#">A simple link</a></p>
```

```
p {
  font-size: 2rem;
  text-align: center;
}
```

- You'll notice a few things as you explore the default styles:

  - Links are underlined.
  - Unvisited links are blue.
  - Visited links are purple.
  - Hovering a link makes the mouse pointer change to a little hand icon.
  - Focused links have an outline around them — you should be able to focus on the links on this page with the keyboard by pressing the tab key. (On Mac, you'll need to use option + tab , or enable the Full Keyboard Access: All controls option by pressing Ctrl + F7 .)
  - Active links are red. Try holding down the mouse button on the link as you click it

- Interestingly enough, these default styles are nearly the same as they were back in the early days of browsers in the mid-1990s.
- This is because users know and have come to expect this behavior — if links were styled differently, it would confuse a lot of people.
- This doesn't mean that you shouldn't style links at all. It just means that you shouldn't stray too far from the expected behavior.
- You should at least:

  - Use underlining for links, but not for other things. If you don't want to underline links, at least highlight them in some other way.
  - Make them react in some way when hovered/focused, and in a slightly different way when activated.

- The default styles can be turned off/changed using the following CSS properties:
  - `color` for the text color.
  - `cursor` for the mouse pointer style — you shouldn't turn this off unless you've got a very good reason.
  - `outline` for the text outline. An outline is similar to a border. The only difference is that a border takes up space in the box and an outline doesn't; it just sits over the top of the background. The outline is a useful accessibility aid, so should not be removed without adding another method of indicating the focused link.

### Styling some links

- To start off with, we'll write out our empty rulesets:

```
a {
}

a:link {
}

a:visited {
}

a:focus {
}

a:hover {
}

a:active {
}
```

- This order is important because link styles build on one another.

  - For example, the styles in the first rule will apply to all the subsequent ones. When a link is activated, it's usually also hovered over.
  - If you put these in the wrong order, and you're changing the same properties in each ruleset, things won't work as you expect.
  - To remember the order, you could try using a mnemonic like **L**o**V**e **F**ears **HA**te.

- Now let's add some more information to get this styled properly:

```
body {
  width: 300px;
  margin: 0 auto;
  font-size: 1.2rem;
  font-family: sans-serif;
}

p {
  line-height: 1.4;
}

a {
  outline: none;
  text-decoration: none;
  padding: 2px 1px 0;
}

a:link {
  color: #265301;
}

a:visited {
  color: #437a16;
}

a:focus {
  border-bottom: 1px solid;
  background: #bae498;
}

a:hover {
  border-bottom: 1px solid;
  background: #cdfeaa;
}

a:active {
  background: #265301;
  color: #cdfeaa;
}
```

- We'll also provide some sample HTML to apply the CSS to:

```
<p>
  There are several browsers available, such as <a href="#">Mozilla Firefox</a>,
  <a href="#">Google Chrome</a>, and <a href="#">Microsoft Edge</a>.
</p>
```

- This certainly looks different to the default styling, but it still provides a familiar enough experience for users to know what's going on:
  - The first two rules are not that interesting to this discussion.
  - The third rule uses the `a` selector to get rid of the default text underline and focus outline (which varies across browsers anyway), and adds a tiny amount of padding to each link — all of this will become clear later on.
  - Next, we use the `a:link` and `a:visited` selectors to set a couple of color variations on unvisited and visited links, so they are distinct.
  - The next two rules use `a:focus` and `a:hover` to set focused and hovered links to have different background colors, plus an underline to make the link stand out even more. Two points to note here are:
    - The underline has been created using `border-bottom`, not `text-decoration` — some people prefer this because the former has better styling options than the latter. It's also drawn a bit lower so it doesn't cut across the descenders of the word being underlined (e.g., the tails on g and y).
    - The `border-bottom` value has been set as `1px solid`, with no color specified. Doing this makes the border adopt the same color as the element's text, which is useful in cases like this where the text is a different color in each case.
  - Finally, `a:active` is used to give the links an inverted color scheme while they are being activated, to make it clear something important is happening!

## Including icons on links

- A common practice is to include icons on links to provide more of an indicator as to what kind of content the link points to.
- Let's look at a really simple example that adds an icon to external links (links that lead to other sites).
- Such an icon usually looks like a little arrow pointing out of a box.
- For this example, we'll use this great example from icons8.com.
- The HTML we are applying the styling to:

```
<p>
  For more information on the weather, visit our <a href="#">weather page</a>,
  look at <a href="https://en.wikipedia.org/">weather on Wikipedia</a>, or check
  out
  <a href="https://www.nationalgeographic.org/topics/resource-library-weather/">
    weather on National Geographic
  </a>.
</p>
```

- The CSS:

```
body {
  width: 300px;
  margin: 0 auto;
  font-family: sans-serif;
}

p {
  line-height: 1.4;
}

a {
  outline: none;
  text-decoration: none;
  padding: 2px 1px 0;
}

a:link {
  color: blue;
}

a:visited {
  color: purple;
}

a:focus,
a:hover {
  border-bottom: 1px solid;
}

a:active {
  color: red;
}

a[href^="http"] {
  background: url("external-link-52.png") no-repeat 100% 0;
  background-size: 16px 16px;
  padding-right: 19px;
}
```

- We'll skip over most of the CSS, as it's just the same information you've looked at before.
- The last rule, however, is interesting: we're inserting a custom background image on external links in a similar manner to how we handled custom bullets on list items in the last article.
- This time, however, we're using the `background` shorthand instead of the individual properties.
  - We set the path to the image we want to insert, specify `no-repeat` so we only get one copy inserted, and then specify the position as 100% of the way to the right of the text content, and 0 pixels from the top.
- We also use `background-size` to specify the size we want the background image to be shown at.
  - It's useful to have a larger icon and then resize it like this as needed for responsive web design purposes.
  - This does, however, only work with IE 9 and later. So if you need to support older browsers, you'll just have to resize the image and insert it as is.
- Finally, we set some `padding-right` on the links to make space for the background image to appear in, so we aren't overlapping it with the text.
- A final word: how did we select just external links?
  - Well, if you are writing your HTML links properly, you should only be using absolute URLs for external links — it is more efficient to use relative links to link to other parts of your own site (as with the first link).
  - The text "http" should therefore only appear in external links (like the second and third ones), and we can select this with an attribute selector: `a[href^="http"]` selects `<a>` elements, but only if they have an `href` attribute with a value that begins with "http".

## Styling links as buttons

- The tools you've explored so far in this article can also be used in other ways.
  - For example, states like hover can be used to style many different elements, not just links — you might want to style the hover state of paragraphs, list items, or other things.
- In addition, links are quite commonly styled to look and behave like buttons in certain circumstances. A website navigation menu can be marked up as a set of links, and this can be styled to look like a set of control buttons or tabs that provide the user with access to other parts of the site. Let's explore how.
- The HTML for the navigation bar:

```
<nav class="container">
  <a href="#">Home</a>
  <a href="#">Pizza</a>
  <a href="#">Music</a>
  <a href="#">Wombats</a>
  <a href="#">Finland</a>
</nav>
```

- The CSS:

```
body,
html {
  margin: 0;
  font-family: sans-serif;
}

.container {
  display: flex;
  gap: 0.625%;
}

a {
  flex: 1;
  text-decoration: none;
  outline: none;
  text-align: center;
  line-height: 3;
  color: black;
}

a:link,
a:visited,
a:focus {
  background: yellow;
}

a:hover {
  background: orange;
}

a:active {
  background: red;
  color: white;
}
```

- The HTML defines a `<nav>` element with a `"container"` class. The `<nav>` contains our links.

- The second rule says:
  - The container is a flexbox. The items it contains — the links, in this case — will be _flex_ items.
  - The gap between the flex items will be `0.625%` of the container's width.
- The third rule styles the links:
  - The first declaration, `flex: 1`, means that the widths of the items will be adjusted so they use all the available space in the container.
  - Next, we turn off the default `text-decoration` and `outline` — we don't want those spoiling our look.
  - The last three declarations are to center the text inside each link, set the `line-height` to 3 to give the buttons some height (which also has the advantage of centering the text vertically), and set the text color to black.

# Web fonts

- We'll see how to use custom fonts with your web page to allow for more varied, custom text styling.

## Font families recap

- As we looked at in Fundamental text and font styling, the fonts applied to your HTML can be controlled using the `font-family` property. This takes one or more font family names. When displaying a webpage, a browser will travel down a list of font-family values until it finds a font available on the system it is running on:

```
p {
  font-family: Helvetica, "Trebuchet MS", Verdana, sans-serif;
}
```

- This system works well, but traditionally web developers' font choices were limited.
- There are only a handful of fonts that you can guarantee to be available across all common systems — the so-called Web-safe fonts.
- You can use the font stack to specify preferred fonts, followed by web-safe alternatives, followed by the default system font.
- However, this increases your workload because of the testing required to make sure that your designs work with each font.

## Web fonts

- But there is an alternative that works very well. (It's even supported by such older browsers as IE version 6.)
- CSS allows you to specify font files, available on the web, to be downloaded along with your website as it's accessed.
- This means that any browser supporting this CSS feature can display the fonts you've specifically chosen.
- Amazing! The syntax required looks something like this:
  - First of all, you have a `@font-face` ruleset at the start of the CSS, which specifies the font file(s) to download:

```
@font-face {
  font-family: "myFont";
  src: url("myFont.woff2");
}
```

- Below this you use the font family name specified inside `@font-face` to apply your custom font to anything you like, as normal:

```
html {
  font-family: "myFont", "Bitstream Vera Serif", serif;
}
```

- Here are some important things to bear in mind about web fonts:

  - Fonts generally aren't free to use. You have to pay for them and/or follow other license conditions, such as crediting the font creator in your code (or on your site). You shouldn't steal fonts and use them without giving proper credit.
  - All major browsers support WOFF/WOFF2 (Web Open Font Format versions 1 and 2). Even older browsers such as IE9 (released in 2011) support the WOFF format.
  - WOFF2 supports the entirety of the TrueType and OpenType specifications, including variable fonts, chromatic fonts, and font collections.
  - The order in which you list font files is important. If you provide the browser with a list of multiple font files to download, the browser will choose the first font file it's able to use. That's why the format you list first should be the preferred format — that is, WOFF2 — with the older formats listed after that. Browsers that don't understand one format will then fall back to the next format in the list.
  - If you need to work with legacy browsers, you should provide EOT (Embedded Open Type), TTF (TrueType Font), and SVG web fonts for download. This article explains how to use the Fontsquirrel Webfont Generator to generate the required files.
  - Note: Web fonts as a technology have been supported in Internet Explorer since version 4!

- Using the FireFox WebDev tools can allow you to see ta ist of fonts that are used, and where they are used, etc.
  - There are also variable fonts that has a continuous slider for the font weight: `v-fonts`

## Active learning example

### Finding fonts

- For this example, we'll use two web fonts: one for the headings and one for the body text.
- To start with, we need to find the font files that contain the fonts.
- Fonts are created by font foundries and are stored in different file formats. There are generally three types of sites where you can obtain fonts:

  - A free font distributor: This is a site that makes free fonts available for download (there may still be some license conditions, such as crediting the font creator). Examples include Font Squirrel, dafont, and Everything Fonts.
  - A paid font distributor: This is a site that makes fonts available for a charge, such as fonts.com or myfonts.com. You can also buy fonts directly from font foundries, for example Linotype, Monotype, or Exljbris.
  - An online font service: This is a site that stores and serves the fonts for you, making the whole process easier. See the Using an online font service section for more details.

- Choose two fonts, one for the heading, and one for the paragraph, it doesn't matter whether they are True Type Fonts or Open Type Fonts.

### Generating the required code

- Now you'll need to generate the required code (and font formats). For each font, follow these steps:

- Make sure you have satisfied any licensing requirement if you are going to use this in a commercial and/or Web project.

  1. Go to the Fontsquirrel Webfont Generator.
  2. Upload your two font files using the Upload Fonts button.
  3. Check the checkbox labeled "Yes, the fonts I'm uploading are legally eligible for web embedding."
  4. Click Download your kit.
  5. After the generator has finished processing, you should get a ZIP file to download. Save it in the same directory as your HTML and CSS.

- If you need to support legacy browsers, select the "Expert" mode in the Fontsquirrel Webfont Generator, select SVG, EOT, and TTF formats before downloading your kit.

- Web services for font generation typically limit file sizes. In such a case, consider using tools such as:
- sfnt2woff-zopfli for converting ttf to woff
- fontforge for converting from ttf to svg
- batik ttf2svf for converting from ttf to svg
- woff2 for converting from ttf to woff

### Implementing the code in your demo

- At this point, unzip the webfont kit you just generated. Inside the unzipped directory you'll see some useful items:

  - Two versions of each font: the `.woff`, `.woff2` files.
  - A demo HTML file for each font — load these in your browser to see what the font will look like in different usage contexts.
  - A `stylesheet.css` file, which contains the generated @font-face code you'll need.

- To implement these fonts in your demo, follow these steps:
  - Rename the unzipped directory to something easy and simple, like `fonts`.
  - Open up the `stylesheet.css` file and copy the two `@font-face` rulesets into your `web-font-start.css` file — you need to put them at the very top, before any of your CSS, as the fonts need to be imported before you can use them on your site.
  - Each of the `url()` functions points to a font file that we want to import into our CSS. We need to make sure the paths to the files are correct, so add `fonts/` to the start of each path (adjust as necessary).
  - Now you can use these fonts in your font stacks, just like any web safe or default system font. For example:

```
@font-face {
  font-family: "zantrokeregular";
  src: url("fonts/zantroke-webfont.woff2") format("woff2"), url("fonts/zantroke-webfont.woff")
      format("woff");
  font-weight: normal;
  font-style: normal;
}
```

```
font-family: "zantrokeregular", serif;
```

## Using an online font service

- Online font services generally store and serve fonts for you so you don't have to worry about writing the `@font-face` code.
- Instead, you generally just need to insert a simple line or two of code into your site to make everything work.
- Examples include Adobe Fonts and Cloud.typography. Most of these services are subscription-based, with the notable exception of Google Fonts, a useful free service, especially for rapid testing work and writing demos.
- Here's how to use Google fonts:
  1. Go to Google Fonts.
  2. Search for your favorite fonts or use the filters at the top of the page to display the kinds of fonts you want to choose and select a couple of fonts that you like.
  3. To select a font family, click on the font preview and press the ⊕ button alongside the font.
  4. When you've chosen the font families, press the View your selected families button in the top right corner of the page.
  5. In the resulting screen, you first need to copy the line of HTML code shown and paste it into the head of your HTML file. Put it above the existing <link> element, so that the font is imported before you try to use it in your CSS.
  6. You then need to copy the CSS declarations listed into your CSS as appropriate, to apply the custom fonts to your HTML.

## @font-face in more detail

- Let's explore that @font-face syntax generated for you by Fontsquirrel. This is what one of the rulesets looks like:

```
@font-face {
  font-family: "zantrokeregular";
  src: url("zantroke-webfont.woff2") format("woff2"), url("zantroke-webfont.woff")
      format("woff");
  font-weight: normal;
  font-style: normal;
}
```

- Let's go through to see what it does:

  - `font-family`: This line specifies the name you want to refer to the font as. This can be anything you like as long as you use it consistently throughout your CSS.
  - `src`: These lines specify the paths to the font files to be imported into your CSS (the `url` part), and the format of each font file (the `format` part). The latter part in each case is optional, but is useful to declare because it allows browsers to more quickly determine which font they can use. Multiple declarations can be listed, separated by commas. Because the browser will search through them according to the rules of the cascade, it's best to state your preferred formats, like WOFF2, at the beginning.
  - `font-weight`/`font-style`: These lines specify what weight the font has and whether it is italic or not. If you are importing multiple weights of the same font, you can specify what their weight/style is and then use different values of `font-weight`/`font-style` to choose between them, rather than having to call all the different members of the font family different names.
  - @font-face tip: define font-weight and font-style to keep your CSS simple by Roger Johansson shows what to do in more detail.

- Instead of:

```
@font-face {
	font-family: 'DroidSerifRegular';
	src: url('DroidSerif-Regular-webfont.ttf') format('truetype');
	font-weight: normal;
	font-style: normal;
}
@font-face {
	font-family: 'DroidSerifItalic';
	src: url('DroidSerif-Italic-webfont.ttf') format('truetype');
	font-weight: normal;
	font-style: normal;
}
@font-face {
	font-family: 'DroidSerifBold';
	src: url('DroidSerif-Bold-webfont.ttf') format('truetype');
	font-weight: normal;
	font-style: normal;
}
@font-face {
	font-family: 'DroidSerifBoldItalic';
	src: url('DroidSerif-BoldItalic-webfont.ttf') format('truetype');
	font-weight: normal;
	font-style: normal;
}
```

- Use:

```
@font-face {
	font-family: 'DroidSerif';
	src: url('DroidSerif-Regular-webfont.ttf') format('truetype');
	font-weight: normal;
	font-style: normal;
}
@font-face {
	font-family: 'DroidSerif';
	src: url('DroidSerif-Italic-webfont.ttf') format('truetype');
	font-weight: normal;
	font-style: italic;
}
@font-face {
	font-family: 'DroidSerif';
	src: url('DroidSerif-Bold-webfont.ttf') format('truetype');
	font-weight: bold;
	font-style: normal;
}
@font-face {
	font-family: 'DroidSerif';
	src: url('DroidSerif-BoldItalic-webfont.ttf') format('truetype');
	font-weight: bold;
	font-style: italic;
}
```

## Variable fonts

- There is a newer font technology available in browsers called variable fonts. These are fonts that allow many different variations of a typeface to be incorporated into a single file, rather than having a separate font file for every width, weight, or style.
- They are somewhat advanced for our beginner's course, but if you fancy stretching yourself and looking into them, read our Variable fonts guide.
