# CSS Media Queries

## Overview

In This lesson we will look at using CSS3 Media Queries to detect viewport sizes and adjust CSS styles accordingly.

## Objectives

1. The purpose of media queries.
2. Media Query syntax.
3. Accepted Devices.
4. Min and max conditions.
5. Determining breakpoints based on your unique content.

## Writing Media Queries

<iframe width="640" height="480" src="//www.youtube.com/embed/MYOT5FDG8gk?rel=0&modestbranding=1" frameborder="0" allowfullscreen></iframe>

*Note: Slides for this lecture video are provided in the resources at the bottom of this lesson.*

### What are Media Queries

Media Queries allow us to measure the device viewport (screen) size and then adjust our CSS layout and content accordingly so it best suits each size device.

### Syntax

Below is the syntax for writing a media query statement within our CSS code,

```css
@media [not|only] type [and] (expr) [,] … {
    rules
}
```

We start by using the `@media` keyword followed by the condition statements that will trigger the media query on or off. The logical keywords not or only can optionally be provided to trigger queries for specific devices using `only` or for every device except a particular kind of device using the `not` keyword. These logical keywrds are followed by the device type. At the time of writing this the only currently well supposted device types are: screen, print, or all (meaning all devices). We can use `and` and `,` to separate conditions. Using `and` require sthat both conditions on each side of the and are both true in order for the query to trigger on. The `,` stands for "or" meaning that only one of the conditions on either side of the comma has to be true for the query to trigger on. We use condition expressions surrounded by `()` parenthesis to set up a constion that must be true in order for the query to trigger on and that will be false for the query to not be triggered. This is followed by a set of `{}` curly braces that enclose the CSS selectors and rules that will be applied when the media query is triggered.

To give better context, let's create a media query that will change a paragraphs text from red to green when the screen size falls below 800px,

```css
/* initial style */
p { color: red; }

/* media query */
@media only screen and (max-width: 800px) {
  p { color: green; }
}
```

...

## Summary

- ...

## Resources

- [Presentation Slides](https://docs.google.com/presentation/d/1j_i5pGPB5lHbgr4fpdUDheRBv2kAeOk_yhfd1Uc2f3s/edit?usp=sharing)
- [MDN - CSS - Media Queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)
- [CSS Tricks - Media Queries](https://css-tricks.com/css-media-queries/)

<p data-visibility='hidden'>View <a href='https://learn.co/lessons/media-queries' title='Media Queries'>Media Queries</a> on Learn.co and start learning to code for free.</p>