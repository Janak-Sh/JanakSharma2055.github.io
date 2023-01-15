---
title: CSS 
date: 2022-06-23 12:00:00
categories: [home, hardware]
tags: [servers,dell]
---
# CSS:MDN

# Getting started

> The below notes are taken from [here](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/Getting_started)
> 

```css
li.special {
  color: orange;
  font-weight: bold;
}
```
Just to test deployment
This syntax means "target any li element that has a class of special". If you were to do this then you would no longer be able to apply the class to a <span> or another element by adding the class to it; you would have to add that element to the list of selectors:

```css
li.special,
span.special {
  color: orange;
  font-weight: bold;
}
```

There are times when you will want something to look different based on where it is in the document. There are a number of selectors that can help you here, but for now we will look at just a couple. In our document, there are two <em> elements — one inside a paragraph and the other inside a list item. To select only an <em> that is nested inside an <li> element I can use a selector called the descendant combinator, which takes the form of a space between two other selectors.

```css
li em {
  color: rebeccapurple;
}
```

This selector will select any <em> element that is inside (a descendant of) an <li>

Something else you might like to try is styling a paragraph when it comes directly after a heading at the same hierarchy level in the HTML. To do so place a + (an adjacent sibling combinator) between the selectors.

```css
h1 + p {
  font-size: 200%;
}
```

It is worth noting that you can combine multiple selectors and combinators together

```css
/* selects any <span> that is inside a <p>, which is inside an <article>  */
article p span { ... }

/* selects any <p> that comes directly after a <ul>, which comes directly after an <h1>  */
h1 + ul + p { ... }
```

```css
body h1 + p .special {
  color: yellow;
  background-color: black;
  padding: 5px;
}
```

This will style any element with a class of special, which is inside a <p>, which comes just after an <h1>, which is inside a <body>. Phew!

# How CSS is structured

> The refrence is [here](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/How_CSS_is_structured)
> 

> Important: If a property is unknown, or if a value is not valid for a given property, the declaration is processed as invalid. It is completely ignored by the browser's CSS engine.
> 

## @rules

CSS @rules (pronounced "at-rules") provide instruction for what CSS should perform or how it should behave. Some @rules are simple with just a keyword and a value. For example, @import imports a stylesheet into another CSS stylesheet:

```jsx
@import 'styles2.css';
```

In the example below, the stylesheet defines a default pink background for the <body> element. However, a media query follows that defines a blue background if the browser viewport is wider than 30em.

```css
body {
  background-color: pink;
}

@media (min-width: 30em) {
  body {
    background-color: blue;
  }
}
```

## Shorthands

```css
background: red url(bg-graphic.png) 10px 10px repeat-x fixed;
//this is equivalent to
background-color: red;
background-image: url(bg-graphic.png);
background-position: 10px 10px;
background-repeat: repeat-x;
background-attachment: fixed;
```

# How css works?

refrence  [here](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/How_CSS_works)

# CSS building blocks

- An element selector is less specific — it will select all elements of that type that appear on a page — so will get a lower score.
- A class selector is more specific — it will select only the elements on a page that have a specific class attribute value — so will get a higher score.
- width,border, padding  property donot inherit i.e if parent is set certain width then it is not carried to it's decendents

## Controlling inheritance

- inherit
    
    Sets the property value applied to a selected element to be the same as that of its parent element. Effectively, this "turns on inheritance".
    
- initial
    
    Sets the property value applied to a selected element to the initial value of that property(default set by browser)
    
- unset
    
    Resets the property to its natural value, which means that if the property is naturally inherited it acts like inherit, otherwise it acts like initial.
    
- revert
    
    Acts like unset in many cases, however will revert the property to the browser's default styling rather than the defaults applied to that property.
    
    The resource link is [here](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance)
    
    I am confused on using above mentioned inheritance properties.
    
    # Css selectors
    
    - When you group selectors in this way, if any selector is invalid the whole rule will be ignored.
    
    In the following example, the invalid class selector rule will be ignored, whereas the h1 would still be styled.
    
    ```css
    h1 {
      color: blue;
    }
    
    ..special {
      color: blue;
    }
    ```
    
    When combined however, neither the h1 nor the class will be styled as the entire rule is deemed invalid.
    
    ```css
    h1, ..special {
      color: blue;
    }
    ```