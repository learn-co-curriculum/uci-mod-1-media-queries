# CSS Media Queries

## Learning Goals

- Identify the purpose of media queries
- Describe media query syntax
- Identify where to create "breakpoints"

## Introduction

The key to designing and building responsive layouts is having your content
respond to the size of the device (or "medium"). Your CSS can query the "media"
(plural of "medium") to find out their sizes and proportions. These "media
queries" are the focus of this lesson. By writing "media queries" you can ensure your site looks great on all devices.

## Identify the Purpose of Media Queries

Media queries are a feature of CSS. They are sets of styles that are applied
when the medium satisfies specific conditions. Media queries most frequently
decide whether a group of CSS rules applies based on the device "viewport" (or,
"screen") size. The points at which the layout adjusts, based on some media
property (or properties!), is called a "breakpoint".

## Describe Media Query Syntax

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

When defining a media query, we use the `@media` keyword followed by
conditional statements that will trigger the media query to apply or not. Below
we will break down each property available in media queries:

#### `not`, `only`

The logical keywords "not" or "only" can be used optionally to include or
exclude specific media types or screen sizes. For instance, we may want to
specify that a navigation bar should extend across the width of our page, but
_only_ on screens larger than `800px` in height. It might also be the case that
you want a CSS rule to apply to all devices, but _not_ screens smaller than
`400px` wide.

```css
@media only screen and (max-width: 992px) {
  body {
    background-color: blue;
  }
}
```

```css
@media not screen and (max-width: 992px) {
  body {
    background-color: blue;
  }
}
```

#### `mediatype`

Currently, the only well-supported media types are screen, print, or all
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

We can use `and` and `,` to separate or combine conditions.

* Using `and` requires that both conditions on each side of the `and` are true
  in order for the query to apply.
* Using `,` stands for _or_, meaning that only one of the conditions on either
  side of the comma has to be true for the query to trigger.

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
```
#### (expression)

We define conditional expressions by writing the test and wrapping it in
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
paragraph's text from red to green when the screen size falls below `800px`:

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

On the second line, we provide some initial style that will be applied _unless_
our media query triggers. We have set our paragraph to have red text. On line 5,
we create a media query using `@media` and set it to `only` trigger for `screen`
devices that have a `max-width` of `800px`.

In other words, the style will only be applied to screens that are less than
`801px` wide. Following the condition are a pair of curly braces (`{}`) that
enclose the style(s) to be applied when the condition is met. In our case, on
screens that are `800px` wide or less, we change the text color of paragraphs to
green instead of red.

For our size conditions, we can use the properties `min-width`, `max-width`,
`min-height`, and `max-height`, all referring to the size of the device's
viewport (i.e., screen size). Above, we looked at `max-width`; now let's
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
`400px` and `800px`.

One nice thing about media queries is that they automatically inherit all of the
styles written outside of their `{}` braces. So inside the media query, we only
need to write the CSS for the properties we wish to change. With a set of
different media queries, it is possible to have specific styling for mobile and
desktop screen sizes, along with tablet screen sizes in between.

## Identify Where to Create "breakpoints"

Let your content determine where breakpoints should fall. Use [Developer Tools and Emulators][dte] to discover where your content starts to break down. Then create
an appropriate breakpoint (media query at that width) to solve the issue. This
will ensure that your content looks good on any and all devices, not just the
popular ones.

Advanced layout techniques, such as grid (which will be covered in later
lessons), allow us to keep media query breakpoints to a minimum. You can, for
instance, set a media query for `max-width: 414px`, the width of the iPhone 6+,
which will affect basically all mobile phones, but allow CSS grid to
dynamically adjust the width of web page elements for smaller phones.

## Conclusion

CSS Media Queries provide us a way to alter our CSS at specific screen
sizes by setting _breakpoints_ at different screen widths. Using the
`max-width` condition expressions to trigger styles below a certain
size and the `min-width` condition expressions to trigger styles above
a certain size can help you build powerful, flexible interfaces for various
screen sizes and devices. Instead of trying to target specific device sizes,
use the in-browser dev tools for experimentation, and allow your unique content
to determine at which sizes to write media query breakpoints. Write media
queries as you need them at whatever size your content starts to become unsightly.

## Resources

- [MDN - CSS - Media Queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)
- [CSS Tricks - Media Queries](https://css-tricks.com/css-media-queries/)
- [Simulate Mobile Devices with Device Mode in Google Chrome][dte]

[dte]: https://developers.google.com/web/tools/chrome-devtools/device-mode/
