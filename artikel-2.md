# You Might Don't Need JavaScript

When I was forced to use as little as possible to no JavaScript, I found that I can actually achieve much more with pure HTML and CSS than I expected. Despite the fact that this method is not suitable for every use case, this approach did inspire me tot think outside-the-box. Besides that, only using CSS has better browser support. You can create cool things with CSS by combining CSS pseudo-classes with pseudo-elements.

### What is a pseudo-class?

A CSS pseudo-class is a keyword added to a selector that specifies a special state of the selected element(s). For example, `:hover` can be used to change a button's color when the user's pointer hovers over it (MDN Web Docs, 2019a)

### What is a pseudo-element?

A CSS pseudo-element is a keyword added to a selector that lets you style a specific part of the selected element(s). For example, `::first-line` can be used to change the font of the first line of a paragraph (MDN Web Docs, 2019c).

## Combining pseudo-classes with pseudo-elements

### `:hover`

You can use this pseudo-class to change the appearance when a user hover's over that element. You probably recognize this one. But there's more! For example, if you use the pseudo-class `:hover` in combination with pseudo-element `::before`, you can create a tool tip. Create an element in HTML and style that element in css like this:

```css
element::after {
  opacity: 0;
  content: "text for tooltip";
  position: absolute;
  top: -80px;
  left: -80px;
  background-color: #2b222a;
  width: 160px;
}

/* gives pseudo-element of element an opacity
of 1 when user hovers over element */

element:hover::after {
  opacity: 1;
}
```

Check this example in action: [Pure CSS Tooltip](https://codepen.io/cristina-silva/pen/XXOpga)

### `:checked`

The pseudo-class `:checked` represents any `<input>` (with `type="checkbox"` or `type="radio"`) element and `<option>` element inside and `<select>` element that is checked or toggled to an `on` state. Users can create this state by checking or selecting an element.

Probably the most common reason developers turn to JavaScript is to toggle the visibility of an element. I recently learned that you can use the `:checked` pseudo-class to change the CSS of an element.

```html
<input type="radio" id="input-pink" />
<h1>Text</h1>
```

```css
#input-pink:checked ~ h1 {
  background-color: pink;
}
```

The `background-color` of the html element `<h1>` turns `pink` as soon as the `<input>` element with id `#input-pink` receives the pseudo class: `checked`. For this I used the: general sibling combinator. The general sibling combinator separates two selectors and matches the second element only if it follows the first element (not necessarily immediately), and both are children of the same parent element. (MDN Web Docs, 2019b)

Check this example in action:

1. [No JS Gallery](https://codepen.io/shaishgandhi/pen/yJzamw?editors=1100)
2. [Pure CSS Off Canvas Menu with animated links](https://codepen.io/amitasaurus/pen/adJGEG)

### `:focus`

The pseudo-class `:focus` represents an elements (such as a form `<input>` element) that has received focus. The focus class is triggered when users click or tab on an element, or when users select an element with the tab key.

By combining the pseudo-class `:focus` with the pseudo-element `:placeholder-shown` you can create floating labels. In my opinion, it really seems that this requires JavaScript. Nothing is less true. It looks like this:

![https://miro.medium.com/max/1200/1*7qYq5Nqtdbb_W42_WiCYWA.gif](https://miro.medium.com/max/1200/1*7qYq5Nqtdbb_W42_WiCYWA.gif)

Source: [https://www.florin-pop.com/blog/2017/08/css3-floating-label/](https://blog.prototypr.io/the-ultimate-guide-for-text-fields-in-ux-part-i-b6e5eb58b0e4)

The `:placeholder-shown` pseudo-class selects the input element itself when placeholder text exists in a form input. This is, in short, how you can create floating labels.

```css
input:placeholder-shown + label {
  /* While the placeholder is visible, we want to hide the label. */
  visibility: hidden;
  z-index: -1;
}

input:not(:placeholder-shown) + label,
input:focus:not(:placeholder-shown) + label {
  /* While the placeholder is not shown - because the input has a value - we want
	to animate the label into the floated position.*/
  visibility: visible;
  z-index: 1;
  opacity: 1;
}
```

See the complete code of this example: [CSS Only Floated Labels](https://codepen.io/callmenick/pen/OxpKNZ)

🚨 The `:placeholder-shown` selector exists since 2018 and is not supported by`:placeholder-show` is not supported in Edge and IE. (Can I Use) For fully you have to use the pseudo-class `:focus` with pseudo-elements `::after` and/or `::before`. You can see an example here: [Pure CSS Floating Label Textfield](https://codepen.io/KtorZ/pen/ZOzdqG)

I hope this article has given you a little more insight into the possibilities of CSS on its own. This approach is not suitable for every case but it's great to see what you can accomplish with CSS on its own.

### Sources

Can I Use. (n.d.). Can I use... Support tables for HTML5, CSS3, etc. Retrieved 19 December 2019, from [https://caniuse.com/#search=%3Aplaceholder-shown](https://caniuse.com/#search=%3Aplaceholder-shown)

MDN Web Docs. (2019a, March 18). Pseudo-classes. Retrieved 20 December 2019, from [https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)

MDN Web Docs. (2019b, March 23). General sibling combinator. Retrieved 19 December 2019, from https://developer.mozilla.org/en-US/docs/Web/CSS/General_sibling_combinator

MDN Web Docs. (2019c, October 17). Pseudo-elements. Retrieved 20 December 2019, from [https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements)
