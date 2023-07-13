# Nexter Project

This is my own version of the Nexter project from [Advanced CSS and Sass Flexbox, Grid, Animations and More!](https://www.udemy.com/course/advanced-css-and-sass/). This project used CSS grid for page layout.

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

Build a Real estate business landing page.

### Screenshot

![Site Preview](img/127.0.0.1_5500_Nexter_.png)

### Links

- Solution URL: [Add solution URL here](https://your-solution-url.com)
- Live Site URL: [Add live site URL here](https://your-live-site-url.com)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- SASS CSS
- Flexbox
- CSS Grid
- Desktop-first workflow

### What I learned

- Always use chrome to test responsiveness

- Texts can also be grid container

- when positioning images inside a grid, they would stretch to fill up more than the grid area because the have intrinsic dimensions (aspect ratio) they try to maintain. To prevent this, I'll use the object fit property, which doesn't work properly unless I specify the heigth and width of the image.

```scss
&__img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}
```

- Also I could use align items to place images centrally in their container

```scss
&__pictures {
  background-color: $color-primary;
  background-image: linear-gradient(
      rgba($color-primary, 0.5),
      rgba($color-primary, 0.5)
    ), url(../img/back.jpg);
  background-size: cover;
  // background-blend-mode: luminosity;
  grid-column: full-start / col-end 4;

  display: grid;
  grid-template-columns: repeat(6, 1fr);
  grid-template-rows: repeat(6, 1fr);
  align-items: center;

  @media screen and (max-width: $bp-medium) {
    padding: 6rem;
    grid-column: 1 /-1;
  }
}

&__img--1 {
  display: block;

  grid-area: 2/2/6/6;

  box-shadow: 0 2rem 5rem rgba(#000, 0.1);
  width: 100%;

  @media screen and (max-width: $bp-medium) {
    grid-column: 1/ 5;
    grid-row: 1 / -1;
  }
}

&__img--2 {
  display: block;
  width: 115%;

  grid-area: 4/4/6/7;

  z-index: 10;

  box-shadow: 0 2rem 5rem rgba(#000, 0.3);

  @media screen and (max-width: $bp-medium) {
    grid-row: 1 / -1;
    width: 100%;
  }
}
```
and I'll get this effect ![Displayed image](img/127.0.0.1_8080_.png)

- Emmet on fire. To specfify attributes on emmet, I use square bracket notation "[]". ie I could write the code below as

```html
(figure.gallery__item.gallery**item--$>img.gallery\_\_img[src="img/gal-1.jpeg][alt="gallery
image $"])\*13

<figure class="gallery__item gallery__item--1">
  <img src="img/gal-1.jpeg" alt="gallery image 1" class="gallery__img" />
</figure>
```

- When do I use an helper class? whenever I have a reusable component I don't want to mess up. Helper classes will be a good go-to.

- If I want to the dimension of a grid width to be relative to the vw, I use vw units

- If I want the row height to be relative to the the content, I can use min-content or auto

> how to include svg images in my code

```html
<svg class="feature__icon">
  <use xlink:href="img/sprite.svg#icon-global"></use>
</svg>
```

> To change the feel of a bacground image
> there's also backdrop-filter but when there's a single image, i could go for linear gradient to give the bg image some feel

```css
.bg {
  background-blend-mode: luminosity;
}

.bg {
  background-image: linear-gradient(to right, $color-primary, $color-secondary) url(img/bg.jpeg);
}
```

> The filter property can be used to edit the appearance of images

```css
img {
  height: 2.5rem;
  filter: brightness(70%);
}
```

> The -1 means the end of the explicitly defined grid row

```css
.content {
  grid-row: 1 / -1;
}
```

> A trick to responsively set the number of columns in a row automatically

```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(20rem, 1fr));
}
```

> Jonas default way of styling links

```css
__link:link,
__link:visited {
  text-decoration: none;
}

&__link:hover,
&__hover:active {
  background-color: rgba(#fff, 0.05);
  transform: translateY(-3px);
}
```

### Continued development

Use this section to outline areas that you want to continue focusing on in future projects. These could be concepts you're still not completely comfortable with or techniques you found useful that you want to refine and perfect.

**Note: Delete this note and the content within this section and replace with your own plans for continued development.**

### Useful resources

- [Example resource 1](https://www.example.com) - This helped me for XYZ reason. I really liked this pattern and will use it going forward.
- [Example resource 2](https://www.example.com) - This is an amazing article which helped me finally understand XYZ. I'd recommend it to anyone still learning this concept.

## Author

- Website - [Add your name here](https://www.your-site.com)
- Frontend Mentor - [@yourusername](https://www.frontendmentor.io/profile/yourusername)
- Twitter - [@yourusername](https://www.twitter.com/yourusername)

## Acknowledgments

Credits to **Jonas Schmedtmann** for putting up a well structered tutorial
