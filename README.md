# Project-Natours

## Features

* B.E.M

* Advanced CSS and SASS

* Animations without Javascript

* NPM  Scripts

* Desktop Approach

* Modern CSS Properties but before using them always check [CanIUse](https://caniuse.com/)

* Responsive Grid System [For more Info](https://zellwk.com/blog/responsive-grid-system/)

## SASS/SCSS Lint Installation

* Install sass lint extension on VSCode. Install NPM Package sass-lint. Create .sass-lint.yml and add rules. Done.

## Implements 7-1 CSS Architecture

```yml
sass/
|
|– abstracts/
|   |– _variables.scss    # Sass Variables
|   |– _functions.scss    # Sass Functions
|   |– _mixins.scss       # Sass Mixins
|   |– _placeholders.scss # Sass Placeholders
|
|– base/
|   |– _reset.scss        # Reset/normalize
|   |– _typography.scss   # Typography rules
|   …                     # Etc.
|
|– components/
|   |– _buttons.scss      # Buttons
|   |– _carousel.scss     # Carousel
|   |– _cover.scss        # Cover
|   |– _dropdown.scss     # Dropdown
|   …                     # Etc.
|
|– layout/
|   |– _navigation.scss   # Navigation
|   |– _grid.scss         # Grid system
|   |– _header.scss       # Header
|   |– _footer.scss       # Footer
|   |– _sidebar.scss      # Sidebar
|   |– _forms.scss        # Forms
|   …                     # Etc.
|
|– pages/
|   |– _home.scss         # Home specific styles
|   |– _contact.scss      # Contact specific styles
|   …                     # Etc.
|
|– themes/
|   |– _theme.scss        # Default theme
|   |– _admin.scss        # Admin theme
|   …                     # Etc.
|
|– vendors/
|   |– _bootstrap.scss    # Bootstrap
|   |– _jquery-ui.scss    # jQuery UI
|   …                     # Etc.
|
`– main.scss              # Main Sass file
```

## Principles of Responsive Design and Layout Types

* Float Layout [Used in this Project]
* FlexBox Layout
* CSS Grid Layout
* Layout Centering Techniques [Guide](https://dev.to/alanfall/css-layout-centering-techniques--608)

### A modern UI will combine all of these techniques to create a responsive design - [More Info](https://dev.to/mortoray/what-is-responsive-layout-5791)

* Dependent Sizes
* Columns and flowing
* Expanding coverage
* Collapsing and hiding
* Rearrangement


## Responsive images - 3 Use Cases - [More Info](https://github.com/barryblando/modern-workflow)

* Resolution Switching - Large screen to small screen - (Decrease image resolution on smaller screen)

```html
  <!--
    using Width descriptor (w) see Chrome Devtool
    171/900 = 20vw (~20% width of the viewport width 900px)
    171/600 = 30vw (~30% width of the viewport width 600px)
    300px as default size
    sizes use to inform the browser about the approximate width of the image at diff. viewport width,
    and which to use for the current viewport width and the current display resolution.
  -->

  <img srcset="img/nat-1.jpg 300w, img/nat-1-large.jpg 1000w"
      sizes="(max-width: 56.25em) 20vw, (max-width: 37.5em) 30vw, 300px"
      alt="Photo 1" class="composition__photo composition__photo--p1"
      src="img/nat-1-large.jpg">
```

* Density Switching - @2x screen (high-res) to @1x screen (low res) - (Half the image resolution on @1x screen)

```html
  <!-- using Density descriptor (1x, 2x) see Chrome Devtool -->
  <img srcset="img/logo-green-1x.png 1x, img/logo-green-2x.png 2x" alt="Full logo" class="footer__logo">
```

* Art Direction - Large screen to small screen (Image details were preserved but different image on smaller screen)

```html
  <!--
    Art Direction using picture element
    - basically force browser to use small-1x image in case that this media query applies
  -->
  <picture class="footer__logo">
    <source srcset="img/logo-green-small-1x.png 1x, img/logo-green-small-2x.png 2x" media="(max-width: 37.5em)">
    <img srcset="img/logo-green-1x.png 1x, img/logo-green-2x.png 2x" alt="Full logo" class="footer__logo">
  </picture>
```

## Animation Syntax

* animation-name: keyframe Name
* animation-duration: 0s
* animation-timing-function: ease
* animation-delay: 0s
* animation-iteration-count: 1
* animation-direction: normal
* animation-fill-mode: none
* animation-play-state: running

  [More info](https://developer.mozilla.org/en-US/docs/Web/CSS/animation)

## INFO/TIPS : FIXES

* Tip #1:

```scss
  /* fixes problems like animations and translating things */
  backface-visibility: hidden;
```

* Tip #2:

```scss
  /* fix video/images occupying other sections, fill entire parent while still maintaining aspect ratio */
  object-fit: cover;
```

* Tip #3:

```scss
 /**
   * INFO: :not() select everything except the last child
   * INFO: :last-child selector allows you to target the last element
   * directly inside its containing/parent element.
   */
  &:not(:last-child) {
    margin-bottom: $gutter-vertical;
  }
```

* Tip #4:

```scss
  /* NOTE: Below fixes image wiggling after hovering parent element, Browser Bug(Chrome 64.0.3282.167). */
  filter: blur(0.3px); /* the lowest value I could get on my machine: 0.12805650383234025436px */
  image-rendering: -webkit-optimize-contrast; /* just in case quality degrades */
```

* Tip #5: Sibling Selector

```scss
  /* element should be after the input/element in order to be selected with the sibling selector ~ */
  &__input:placeholder-shown ~ &__label { }

```

* Tip #6: Adjacent Selector

```scss
  /**
    * label/element should be after the input/element in order to be selected
    * with the adjacent sibling selector +
    * label that come immediately after any input of the same parent element
    */
  &__input:placeholder-shown + &__label { }
```

* Tip #6: Child combinator

```scss
  /**
    * .section-features > * { } selects direct / first degree child that come across which is row(only)
    * .section-features * { } selects all child and child of child
    */
  & > * {
    transform: skewY(7deg);
  }
```

* Tip #7: MEDIA QUERIES: ORDER MATTERS

```scss
  /* The order of Media query is the key. The one that after will override the rules before it. No Conflict. */

  /**
    * It means that, if you apply two rules that collide to the same elements,
    * it will choose the last one that was declared,
    * unless the first one has the !important marker or is more specific
    */

  /* DESKTOP APPROACH : < (max-width) */
  @include respond(tab-land) { // width < 1200?
    font-size: 56.25%; // 1 rem = 9px, 9/16 = 56.25%
  }

  @include respond(tab-port) { // width < 900?
    font-size: 50%; // 1 rem = 8px, 8/16 = 50%
  }

  @include respond(phone) { // width < 600?
    font-size: 37.5%; // 1 rem = 6px, 6/16 = 37.5%
  }

  /* MOBILE FIRST : > * (min-width) */
  @include respond(phone) { // width > 600?
    font-size: 37.5%; // 1 rem = 6px, 6/16 = 37.5%
  }

  @include respond(tab-port) { // width > 900?
    font-size: 50%; // 1 rem = 8px, 8/16 = 50%
  }

  @include respond(tab-land) { // width > 1200?
    font-size: 56.25%; // 1 rem = 9px, 9/16 = 56.25%
  }
```

* Tip #8: Graceful Degradation using supports @ rule (feature-queries)

```scss
  // --------------------------------------------------------------
  // If the browser support this property then apply this style
  // --------------------------------------------------------------
  @supports (-webkit-backdrop-filter: blur(10px)) or (backdrop-filter: blur(10px)) {
    -webkit-backdrop-filter: blur(10px);
    backdrop-filter: blur(10px);
    background-color: rgba($color-black, .3);
  }
```