# Frontend Mentor - 3-column preview card component solution

This is my own version of the Trillo project from [Advanced CSS and Sass Flexbox, Grid, Animations and More!](https://www.udemy.com/course/advanced-css-and-sass/). The project used CSS flex page layout.

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

Build a Hotel booking site.

### Screenshot

![site preview](/Trillo/Screenshot%202023-06-12%20at%2020-13-25%20trillo%20%E2%80%94%20Your%20all-in-one%20booking%20app.png)


### Links

- Solution URL: [Add solution URL here](https://your-solution-url.com)
- Live Site URL: [Add live site URL here](https://your-live-site-url.com)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- SASS CSS
- Flexbox
- Desktop-first workflow

### What I learned
- when there're 2 max-width media queries, I put the bigger one first before the smaller. 
Why? because the bigger media query will always be true even for smaller screen sizes.

- CSS variable can't be used as breakpoint values in media query. An alternative will be to use sass variables.

- Transition doesn't work on background images

- z-index property only works when the there's position property on the element

- create animations with @keyframes animation name.

- svg icons typically behave like inline elements. There is usually white space below them, to remove this I can set font-size to zero and line height to 1. or I could set the parent element to display flex.

> How to include an svg file in my project
```html
<svg class="search__icon">
  <use xlink:href="img/sprite.svg#icon-magnifying-glass"></use>
</svg>
```

> This is a useful property to let element inherit the element or parent's color

```css
.proud-of-this-css {
  color: currentColor;
}
```

> Rather than worrying about where to place an abosolutely positioned element, I could use

```css
.element {
  position: absolute;
  top: -100%;
}
```

> **when should i add my images from CSS?**  
whenever I'm avoiding the stress of writing multiple lines of code required to include the image in each element in the HTML file.  
The mask method, similar to clip path, specifies the outline of a background that will be revealed. This outline follows the shape of the mask-image.

```scss
&__item::before {
  content: "";
  display: inline-block;
  height: 1.2rem;
  width: 1.2rem;
  margin-right: 0.7rem;

  // older browsers
  // background-image: url(../img/chevron-thin-right.svg);
  // background-size: cover;

  // Newer browsers - mask approach
  background-color: var(--color-primary);
  -webkit-mask-image: url(../img/chevron-thin-right.svg);
  mask-image: url(../img/chevron-thin-right.svg);
  -webkit-mask-size: cover;
  mask-size: cover; // behaves like background-size
}
```

> a cool animation, that increases heigth first, then width

```css
&__item::before {
  position: absolute;
  content: "";
  top: 0;
  left: 0;
  //transform-origin: top;// this would make the animation come down first before going wide;
  width: 3px;
  height: 100%;
  background-color: var(--color-primary);
  transform: scaleY(0);
  transition: transform 0.2s, width 0.4s cubic-bezier(1, 0, 0, 1) 0.2s,
    background-color 0.1s;
}

&__item:hover::before,
&__item--active::before {
  transform: scaleY(1);
  width: 100%;
}
```

> The default value for transform origin is centre, therefor the starting point of rotation, animation etc. is the center. This could be modified.

```css
.proud-of-this-css {
  transform-origin: top;
}
```


### Continued development

Use this section to outline areas that you want to continue focusing on in future projects. These could be concepts you're still not completely comfortable with or techniques you found useful that you want to refine and perfect.

Jonas suggested further increasing the number of pages for the site.

### Useful resources

- [Example resource 1](https://www.example.com) - This helped me for XYZ reason. I really liked this pattern and will use it going forward.
- [Example resource 2](https://www.example.com) - This is an amazing article which helped me finally understand XYZ. I'd recommend it to anyone still learning this concept.

## Author

- Website - [Add your name here](https://www.your-site.com)
- Frontend Mentor - [@yourusername](https://www.frontendmentor.io/profile/yourusername)
- Twitter - [@yourusername](https://www.twitter.com/yourusername)


## Acknowledgments

Special thanks to **Jonas Schmedthmann** for the amazing course

