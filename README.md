# CSS Media Queries

## Overview
In this lesson we will look at using CSS3 Media Queries to detect viewport sizes and adjust CSS styles accordingly.

## Objectives
1. The purpose of media queries.
2. Media Query syntax.
3. Accepted Devices.
4. Min and max conditions.
5. Choosing break point sizes.

## Introducing Media Queries
<iframe width="640" height="480" src="//www.youtube.com/embed/MYOT5FDG8gk?rel=0&modestbranding=1" frameborder="0" allowfullscreen></iframe>

*Note: Slides for this lecture video are provided in the resources at the bottom of this lesson.*

### What are Media Queries
Media Queries allow us to measure the device viewport (screen) size and then adjust our CSS layout and content accordingly so it best suits each size device.

### Syntax
Below is the syntax for writing a media query statement within our CSS code:
```css
@media [not|only] type [and] (expr) [,] … {
    rules
}
```

We start by using the `@media` keyword followed by the condition statements that will trigger the media query on or off. The logical keywords "not" or "only" can optionally be provided to trigger queries for specific devices using `only` or for every device except a particular kind of device using the `not` keyword. These logical keywords are followed by the device type. At the time of writing this the only currently well supported device types are: screen, print, or all (meaning all devices). We can use `and` and `,` to separate conditions. Using `and` requires that both conditions on each side of the `and` are both true in order for the query to trigger on. The `,` stands for "or" meaning that only one of the conditions on either side of the comma has to be true for the query to trigger on. We use condition expressions surrounded by `()` parentheses to set up a condition that must be true in order for the query to trigger on and that will be false for the query to not be triggered. This is followed by a set of `{}` curly braces that enclose the CSS selectors and rules that will be applied when the media query is triggered.

To give better context, let's create a media query that will change a paragraph's text from red to green when the screen size falls below 800px:
```css
/* initial style */
p { color: red; }

/* media query */
@media only screen and (max-width: 800px) {
  p { color: green; }
}
```

On the second line we provide some initial style that will be applied _unless_ our media query triggers. We have set our paragraph to have red text. On line 5, we create a media query using `@media` and set it to `only` trigger for `screen` devices that have a `max-width` of `800px`. In other words, the style will only be applied on screens that are less than 801px wide. Following the condition are a pair of curly braces (`{}`) that enclose the style(s) to be applied when the condition is met. In our case, on screens that are `800px` wide or less, we change the text color of paragraphs to green instead of red.

For our size conditions we can use the properties `min-width`, `max-width`, `min-height`, and `max-height`, all referring to the size of the device's viewport (i.e., the screen size). Above, we looked at `max-width`; now let's explore `min-width`:
```css
/* initial style */
p { color: red; }

/* media query */
@media only screen and (min-width: 400px) {
  p { color: green; }
}
```

On line 2, we set the default color of paragraphs to red again. On line 5, we set the terms of our media query — namely, that the width of the `screen` device must be `400px` or more.

So, `max-width` sets a breakpoint that triggers when a screen is smaller than the specified size, and `min-width` triggers when a screen is larger than a certain size.

As mentioned before, we can use the `and` keyword to chain multiple conditions together. Let's look at an example of that:
```css
/* initial style */
p { color: red; }

/* media query */
@media only screen and (min-width: 400px) and (max-width: 800px) {
  p { color: green; }
}
```

Here we are changing the text color to green only on screens that are between 400px and 800px.

One nice thing about media queries is that they automatically inherit all of the styles written outside of their `{}` braces. So inside the media query we only need to write the css for the properties we wish to change. Later on we will look at some practical ways to use media queries in real life situations within our website.

### At What Size Should I Create Break Points?

Let your content determine where break points should fall. Use Developer Tools and Emulators to discover where your content starts to break down. Then create an appropriate break point (media query at that width) to solve the issue. This will ensure that your content looks good on any and all devices not just the popular ones.

## Summary

- CSS Media Queries provide us a way to alter our CSS at a specific screen sizes.
- The syntax is `@media only screen and (max-width: 800px){ ... }`.
- We can use `max-width` condition expressions to trigger styles below a certain size and we can use `min-width` condition expressions to trigger styles above a certain size.
- Allow your unique content to determine at which sizes to write media query break points. Write them as you need them at whatever size your content starts to become awkward looking.

## Resources

- [Presentation Slides](https://docs.google.com/presentation/d/1j_i5pGPB5lHbgr4fpdUDheRBv2kAeOk_yhfd1Uc2f3s/edit?usp=sharing)
- [MDN - CSS - Media Queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)
- [CSS Tricks - Media Queries](https://css-tricks.com/css-media-queries/)

<p data-visibility='hidden'>View <a href='https://learn.co/lessons/media-queries' title='Media Queries'>Media Queries</a> on Learn.co and start learning to code for free.</p>
