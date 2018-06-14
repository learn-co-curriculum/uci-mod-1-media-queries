# CSS Media Queries

## Problem Statement

The key to designing and building responsive layouts is being mindful
of the wide variety of screen sizes. In the past, "breakpoints" were used
to create styles for specific devices with certain screen sizes. As the market
of web-connected electronics has grown, these techniques have evolved to be more
inclusive of the vast number of new sizes and aspect ratios. These techniques are
media queries. What are media queries, and how can they be taken advantage of in
building page layouts?

## Objectives

1. What are breakpoints
2. What is the purpose of media queries
3. What is the media query syntax
4. Where should break points be created

## What is the Purpose of Media Queries?

Media queries are a feature of CSS. Media queries are sets of styles that are 
triggered by specific conditions. Media queries are most used for measuring 
the device viewport (screen) size and then adjust our CSS layout and content 
accordingly so it best suits each size device. The points at which the layout
adjusts based on screen size is called a "breakpoint".

## What is the Media Query Syntax?

Below are a few examples of syntax for writing a media query statement within 
our CSS code:

```css
@media (max-width: 992px) {
  body {
    background-color: blue;
  }
}
```
Below are more specific and complete examples of the media query syntax:

```css
@media screen and (max-width: 992px) {
  body {
    background-color: blue;
  }
}

```

```css
@media only screen and (max-width: 992px) {
  body {
    background-color: blue;
  }
}
```

When defining a media query, we use the `@media` keyword followed by conditional
statements that will trigger the media query on or off. Below we will break down
each property available in media queries:

#### `not`, `only`

The logical keywords "not" or "only" can be used optionally to include or
exclude specific media types or screen sizes. For instance, we may want to
specify that a navigation bar should extend across the width of our page, but
_only_ on screens larger than 800px in height. It might also be the case that
you want a CSS rule to apply to all devices, but _not_ screens smaller than
400px wide.

```css
@media [not|only] screen and (max-width: 992px) {
  body {
    background-color: blue;
  }
}
```

#### `mediatype`

Currently, the only well supported media types are: screen, print, or all
(meaning all devices). Mobile, tablet, and desktop devices all fall within the
_screen_ mediatype, while _print_ is used for displaying content in a 'print
preview' mode. Most commonly we are concerned only with _screen_.

```css
@media [screen|print|all] and (max-width: 992px) {
  body {
    background-color: blue;
  }
}
```

#### `and`, `,`

We can use `and` and `,` to separate conditions.

* Using `and` requires that both
conditions on each side of the `and` are true in order for the query to trigger.
* Using `,` stands for _or_, meaning that only one
of the conditions on either side of the comma has to be true for the query to
trigger.

```css
@media screen and (min-width: 992px) and (max-width: 1136px) {
  body {
    background-color: blue;
  }
}
```


```css
@media screen and (min-width: 992px), (max-width: 1136px) {
  body {
    background-color: blue;
  }
}

#### (expression)

We define conditional expressions by writing the criteria and wrapping it in
parentheses. The expression must evaluate to true in order for the query to
trigger unless using a `,`. These expressions are followed by a set of `{}`
curly braces that enclose the CSS selectors and rules that will be applied when
the media query is triggered.

```css
@media (max-width: 992px) {
  body {
    background-color: blue;
  }
}
```

### Usage

To give better context, let's create a media query that will change a
paragraph's text from red to green when the screen size falls below 800px:

```css
/* initial style */
p {
    color: red;
}

/* media query */
@media only screen and (max-width: 800px) {
  p {
    color: green;
  }
}
```

On the second line we provide some initial style that will be applied _unless_
our media query triggers. We have set our paragraph to have red text. On line 5,
we create a media query using `@media` and set it to `only` trigger for `screen`
devices that have a `max-width` of `800px`.

In other words, the style will only be applied on screens that are less than
801px wide. Following the condition are a pair of curly braces (`{}`) that
enclose the style(s) to be applied when the condition is met. In our case, on
screens that are `800px` wide or less, we change the text color of paragraphs to
green instead of red.

For our size conditions we can use the properties `min-width`, `max-width`,
`min-height`, and `max-height`, all referring to the size of the device's
viewport (i.e., the screen size). Above, we looked at `max-width`; now let's
explore `min-width`:

```css
/* initial style */
p {
  color: red;
}

/* media query */
@media only screen and (min-width: 400px) {
  p {
    color: green;
  }
}
```

On line 2, we set the default color of paragraphs to red again. On line 5, we
set the terms of our media query — namely, that the width of the `screen` device
must be `400px` or more.

So, `max-width` triggers when a screen is smaller than the specified size, and
`min-width` triggers when a screen is larger than a certain size.

As mentioned before, we can use the `and` keyword to chain multiple conditions
together. Let's look at an example of that:

```css
/* initial style */
p {
  color: red;
}

/* media query */
@media only screen and (min-width: 400px) and (max-width: 800px) {
   p {
     color: green;
   }
}
```

Here we are changing the text color to green only on screens that are between
400px and 800px.

One nice thing about media queries is that they automatically inherit all of the
styles written outside of their `{}` braces. So inside the media query we only
need to write the CSS for the properties we wish to change. With a set of
different media queries, it is possible to have specific styling for mobile and
desktop screen sizes, along with tablet screen sizes in between.

## Where Should Break Points Be Created?

Let your content determine where break points should fall. Use Developer Tools
and Emulators to discover where your content starts to break down. Then create
an appropriate break point (media query at that width) to solve the issue. This
will ensure that your content looks good on any and all devices not just the
popular ones.

Advanced layout techniques, such as grid, allow us to keep media query break
points to a minimum. You can, for instance, set a media query for `max-width:
414px`, the width of the iPhone 6+, which will affect basically all mobile
phones, but allow CSS grid to dynamically adjust the width of web page elements
for smaller phones.

## Conclusion

CSS Media Queries provide us a way to alter our CSS at specific screen
sizes by setting _breakpoints_ at different screen widths. Using the 
`max-width` condition expressions to trigger styles below  a certain
size and the `min-width` condition expressions to trigger styles above
a certain size can help you build powerful, flexible interfaces for various
screen sizes and devices. Instead of trying to target specific device sizes,
use the in-browser dev tools for experimentation, and allow your unique content
to determine at which sizes to write media query break points. Write media
queries as you need them at whatever size your content starts to become unsightly.

## Resources

- [MDN - CSS - Media
- Queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)
- [CSS Tricks - Media Queries](https://css-tricks.com/css-media-queries/)

<p data-visibility='hidden'>View <a
href='https://learn.co/lessons/media-queries' title='Media Queries'>Media
Queries</a> on Learn.co and start learning to code for free.</p>
