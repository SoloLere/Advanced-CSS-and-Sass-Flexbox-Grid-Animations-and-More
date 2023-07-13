# Natours Project

This is my own version of the Natour project from [Advanced CSS and Sass Flexbox, Grid, Animations and More!](https://www.udemy.com/course/advanced-css-and-sass/). The project used classic format of floats for page layout.

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
  - [Useful resources](#useful-resources)
- [Author](#author)
- [Acknowledgments](#acknowledgments)


## Overview

### The challenge

- Build a landing page for a travel agency website

### Screenshot

![preview site](Screenshot%202023-06-12%20at%2019-10-07%20Natours%20Exciting%20tours%20for%20adventurous%20people.png)

Add a screenshot of your solution. The easiest way to do this is to use Firefox to view your project, right-click the page and select "Take a Screenshot". You can choose either a full-height screenshot or a cropped one based on how long the page is. If it's very long, it might be best to crop it.

Alternatively, you can use a tool like [FireShot](https://getfireshot.com/) to take the screenshot. FireShot has a free option, so you don't need to purchase it.

Then crop/optimize/edit your image however you like, add it to your project, and update the file path in the image above.


### Links

- Solution URL: [Add solution URL here](https://your-solution-url.com)
- Live Site URL: [Add live site URL here](https://your-live-site-url.com)


## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- SASS CSS
- Flexbox
- Float
- Tables
- Desktop-first workflow


### What I learned

- if a feature won't be availabe for hover in mobile devices, instead of trying to target mobile devices screens, i could target an hover media query to give alternative feature to users.

- I have some npm commands I can copy from my json file to use in subsequent project

- Graceful degredation: @supports feature query..., always put prefixed property before original

- Responsive images with CSS: min-resolution: 192dpi on other browsers, -webkit-min-device-pixel-ratio: 2 for safari.

- Responsive Images with HTML???
  - Resolution switching: change same image based on screen size, uses sourceset, sizes, width descriptors (width of image, w).
  - Density switching: change same image based in screen resolution (same size). uses density descriptors "1x, 2x etc".
  - Art resolution: select different image based on screen size, uses picture element.

- I can divide a section of text into 2 column layout by using column-count = 2, column-gap and column-rule.

- background-blend-mode, backdrop-filter: used to set what happens to whats behind an element. In this project, it was used to blur everything behind a popup.

- z-index property does not support decimal numbers.

- Basic responsive design principles
  - fluid layouts- float, flexbox, grid
  - responsive units
  - flexible images
  - media queries

- [atribute selector] : 
  - ^= start, 
  - $= end, 
  - \*= contains, 
  - = mathching,
  - ~ general sibling selector, 
  - \+ adjacent sibling selector
shape outside???

- The image zoom out feature I did in section\_\_story can also be done with background-size and background repeat properties but I didn't get the precision i wanted.

- If I have make a transform property present on direct children by "\*" selector, the children with a transform property won't pick up a the parent transform property. **Glitch with css. I have to manually copy the property into such children.**

- when a content bg-img overflows the border radius, use overflow:hiddent to fix it.

- the container classes should be stand alone, don't add modifiers to them, instead create new div to store modifiers

- **Make text have gradient color** by having a background image and "-webkit-background-clip: text and color: transparent" also they have to have a display of inline block

- To ensure multiple radio button inputs can't be selected at the same time, I can give them the same name value

- New pseudo-element: 
  - invalid, 
  - placeholder-shown, 
  - checked

- Margin: 0 auto; centers block element, while text-align: center on parent element, centers inline element contents
  
- From a browser's POV, it's best to only animate opacity and transform.

- **SASS**:
  - $ begins variable name
  - @ begins mixin, 
  - @include --mixin-name is used to call a mixin
  - % begins extend, 
  - @extend --extend-placeholder-name is used to call placeholder

> when using calc function in SASS, wrap variable in curly braces and place '#' in front of them, see below:
```sass
width: calc((100% - #{$gutter-horizontal}) / 2);
```

> give floats parent a height

```css
.parent {
  content: "";
  display: table;
  clear: both;
}
```

> How to prevent the backside of a rotated element from showing. Infact whenever I'm having any issue with animations, this should be the first go-to fix. 
This CSS property prevents parent element(back part) from being visible whenever a child has a transform property(especially rotate) on it. This is done to stabilize the transformation and prevent akward movements.

```css
.element {
  backface-visibility: hidden;
}
```

> Two ways of doing the same thing

```css
div:not(:first-child) {
  margin-top: 10px;
}
```

```css
div + div {
  margin-bottom: 10px;
}
```

> Centering block level elements inside another block level element

```css
.proud-of-this-css {
  margin: 0 auto;
}
```

> font size can be altered from the default 16px to 10px in my file without affecting user defined font-size. **Now 1rem = 10px**

```css
html {
  font-size: 62.5%;
  <!--this is relative to the user defined font-size (i.e 16px * 62.5\%) will be 10px in my code -->
  }
```

>I can make the outside of a circular element have a cirular flow around it. This is used in my section stories

```scss
&__shape {
  position: relative;
  height: 15rem;
  width: 15rem;
  float: left;
  -webkit-shape-outside: circle(50% at 50% 50%);
  shape-outside: circle(50% at 50% 50%);
  -webkit-clip-path: circle(50% at 50% 50%);
  clip-path: circle(50% at 50% 50%);
  transform: translateX(-3rem) skewX(12deg);
  // background-image: url(../img/nat-8.jpg);
  // background-size: contain;
  // background-repeat: no-repeat;

  @include respond(phone) {
    transform: translateX(-3rem) skewX(0);
  }
}
```

> Clipaths are good features to generate various shape I could make my element appear. In this case, I wanted a polygon(top left, top right, bottom right, bottom left).

```css
.shape {
  clip-path: polygon(0 0, 100\%0, 100\%85\%, 0 100\%);
  background-image: linear-gradient(
    105deg,
    rgba($color-white, 0.9) 50%,
    transparent 50%
  );
}
```

> Alternatively i could skew the parent and skew children conversely. or I could also use gradient to get this effect if I desire it within a content.

```css
  background-image: linear-gradient(
      105deg,
      rgba($color-white, 0.9) 50%,
      transparent 50%
    ),
    url(../img/nat-10.jpg);
```

> Animation effect: letters move rightward and background is filled leftward

```scss
&__link {
  &:link,
  &:visited {
    display: inline-block;
    font-size: 3rem;
    font-weight: 100;
    padding: 1rem 2rem;
    color: $color-white;
    text-transform: uppercase;
    text-decoration: none;
    background-image: linear-gradient(
      120deg,
      transparent 0%,
      transparent 50%,
      $color-white 50%
    );
    background-size: 220%;
    transition: all 0.4s;

    span {
      display: inline-block;
      margin-right: 1rem;
    }
  }

  &:hover,
  &:active {
    background-position: 100%;
    color: $color-primary;
    transform: translateX(1rem);
  }
}
```

```js
const proudOfThisFunc = () => {
  console.log("🎉");
};
```

### Continued development
Since I just followed the video tutorial, I didn't add some flair to the site. However, Jonas gave some suggestions on how I could further expand the site, I'll come back to do it.
These suggestions can be found in *Folder-6 video 13*

### Useful resources

- [Example resource 1](https://www.example.com) - This helped me for XYZ reason. I really liked this pattern and will use it going forward.
- [Example resource 2](https://www.example.com) - This is an amazing article which helped me finally understand XYZ. I'd recommend it to anyone still learning this concept.


## Author

- Website - [Add your name here](https://www.your-site.com)
- Frontend Mentor - [@yourusername](https://www.frontendmentor.io/profile/yourusername)
- Twitter - [@yourusername](https://www.twitter.com/yourusername)

## Acknowledgments
I duff my hat for **Jonas Schmedtmann** for the well explanatory tutorial.

