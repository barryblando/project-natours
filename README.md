# Project-Natours

BEM, Advanced CSS and SASS, using Animations w/o JS with Simple Setup using NPM Scripts for a Landing Page.

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

## INFO : FIXES

* Tip #1:

```css
/* fixes problems like animations and translating things */
backface-visibility: hidden;
```

* Tip #2:

```css
/* fix video/images occupying other sections, fill entire parent while still maintaining aspect ratio */
object-fit: cover;
```