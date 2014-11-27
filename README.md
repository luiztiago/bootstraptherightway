# Bootstrap: The Right Way

Inspired on others "The Right Way's" projects. A compilation of good practices to use Bootstrap.

We do not deliver a cake recipe for you. We will show positive and negative points to be analyzed and used according to the needs of your project.

## Getting started

Bootstrap has a few easy ways to quickly get started, each one appealing to a different skill level and use case. Read through to see what suits your particular needs.

### Download or CDN

Compiled and minified CSS, JavaScript, and fonts. No docs or original source files are included.

* Download: [https://github.com/twbs/bootstrap/releases/download/v3.3.1/bootstrap-3.3.1-dist.zip](https://github.com/twbs/bootstrap/releases/download/v3.3.1/bootstrap-3.3.1-dist.zip)

You can customize and your minified version download too. [http://getbootstrap.com/customize/](http://getbootstrap.com/customize/)

**If you use this customization, never lost your config.json file**

* Or, use these CDN links

```html
<!-- Latest compiled and minified CSS -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.1/css/bootstrap.min.css">

<!-- Optional theme -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.1/css/bootstrap-theme.min.css">

<!-- Latest compiled and minified JavaScript -->
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.1/js/bootstrap.min.js"></script>
```

| +1                                                              | -1                                        |
|-----------------------------------------------------------------|-------------------------------------------|
| Increases the parallelism available.                            | Imports all the bootstrap code            |
| Increases the chance that there will be a cache-hit.            | Does not allow customization of variables |
| Ensures that the payload will be as small as possible.          | Does not allow use of mixins              |
| Reduces the amount of bandwidth used by your server.            |
| Ensures that the user will get a geographically close response. |

### Bower
Install and manage Bootstrap's Sass, CSS, JavaScript, and fonts using Bower.

```
$ bower install bootstrap
```

### Ruby Gem

Add gem on Gemfile file. You can choose use SASS or LESS port of bootstrap. The most common applications on Rails, is to use the port in SASS

```
gem 'bootstrap-sass', '~> 3.3.1'
```

## Customization

When you are using a framework such as Bootstrap, a CSS preprocessor is going to be involved. They enhance the vanilla CSS and add functionality such as use of variables, mixins and nesting of rules.

**Never do any update on the bootstrap files. This will kill you when you need to make any updates, and will be much more difficult to find out what changes were made.**

### Variables

You can create a variables file and do any customization here, such as colors, sizes, border-radius and a more things. You can get a list of LESS/SASS variables on bootstrap oficial site, or [click here](http://getbootstrap.com/customize/#less-variables).

#### Examples

```css

/* Colors */
$body-bg: #fff
$text-color: $gray-dark

/* Fonts */
$font-family-sans-serif: "Helvetica Neue", Helvetica, Arial, sans-serif
$font-size-base: 14px

/* Components */
$border-radius-small: 5px

/* Buttons */
$btn-primary-color: #fff

/* Inputs */
$input-border: #ccc
$input-border-focus: #66afe9

/* Media queries breakpoints */
$screen-xs: 480px
$screen-lg: 1200px

/* Grid system */
$grid-columns: 12 /* Number of columns in the grid. */
$grid-gutter-width: 30px /*Padding between columns. Gets divided in half for the left and right.*/
```

### Files Structure

Here's an example of files structure to organize modules and overrides, which will be better explained below.

```
/stylesheets
├── application.css.sass
├── _variables.css.sass
├── /modules
│   ├── _carousel.css.sass
│   ├── _dialog.css.sass
│   ├── _loading.css.sass
│   └── ...
└── /overrides
    ├── _alert.css.sass
    ├── _form.css.sass
    ├── _dropdown.css.sass
    └── ...
```

#### Modules

A Module is a more discrete component of the page. It is your navigation bars and your carousels and your dialogs and your widgets and so on. This is the meat of the page. Modules sit inside Layout components. Modules can sometimes sit within other Modules, too. Each Module should be designed to exist as a standalone component. In doing so, the page will be more flexible. If done right, Modules can easily be moved to different parts of the layout without breaking.

When defining the rule set for a module, avoid using IDs and element selectors, sticking only to class names. Here's an example of using modules structure.

```css
.widget
  @extend .box

.widget-title
  @extend .text-thin

.widget-footer
  min-height: 30px
```

#### Overrides

If you need to customize something that can not be changed through the variables, one solution is to do some overrides the modules already created by the Bootstrap. Here's an example of using overrides structure.

```css
.table
  border-top: 4px solid $primary-color

  th
    text-transform: uppercase
    @extend .text-thin
```

### "Classless"

Is good use of helper classes as the bootstrap itself already sets in your code, as `text-center`,` text-muted` and more things. But be careful not to mess up your code with repeated classes in various files and pages. Think if it is not better to create modules for this.

#### The wrong way

```html
<h2 class="text-center text-muted text-uppercase text-whatever">About company</h2>
```

#### The right way

If this title will be your title default, you can create a module for titles, and extend all this classes on css, like this:

```html
<h2 class="title">About company</h2>
```

```css
.title
  @extend .text-center
  @extend .text-muted
  @extend .text-uppercase
  @extend .text-whatever
```

## Grid

Grid module of Bootstrap is one of the most modules used by the community. In some cases the developers import all bootstrap to use only the grid. I will not even talk about this case. Does not deserve to be commented! lol

The most common, import some modules, and the grid is **one of the most imported**. The problem is: how many grids you will use in your application? If you look at the code, 48 classes are generated only for `.col-*-*`. There are 12 columns, for each with 4 screen sizes (xs, sm, md, lg), for each 4 differents media queries, and often, the developer uses only 2 or 3 of them.

```css
.col-lg-1, .col-lg-2, .col-lg-3, .col-lg-4, .col-lg-5, .col-lg-6, .col-lg-7, .col-lg-8, .col-lg-9, .col-lg-10, .col-lg-11, .col-lg-12,
.col-md-1, .col-md-2, .col-md-3, .col-md-4, .col-md-5, .col-md-6, .col-md-7, .col-md-8, .col-md-9, .col-md-10, .col-md-11, .col-md-12,
.col-sm-1, .col-sm-2, .col-sm-3, .col-sm-4, .col-sm-5, .col-sm-6, .col-sm-7, .col-sm-8, .col-sm-9, .col-sm-10, .col-sm-11, .col-sm-12,
.col-xs-1, .col-xs-2, .col-xs-3, .col-xs-4, .col-xs-5, .col-xs-6, .col-xs-7, .col-xs-8, .col-xs-9, .col-xs-10, .col-xs-11, .col-xs-12

@media (min-width:768px)
  .col-sm-1, .col-sm-2, .col-sm-3, .col-sm-4, .col-sm-5, .col-sm-6, .col-sm-7, .col-sm-8, .col-sm-9, .col-sm-10, .col-sm-11, .col-sm-12
    float:left

@media (min-width:992px)
  .col-md-1, .col-md-2, .col-md-3, .col-md-4, .col-md-5, .col-md-6, .col-md-7, .col-md-8, .col-md-9, .col-md-10, .col-md-11, .col-md-12
    float:left

/* ... and a lot of unused codes */
```

Here's an example of using the default settings to create a two-column layout with a gap between. You can modify the variables to your own custom values, or just use the mixins with their default values.

```css
@import "variables.less"
@import "mixins.less"

.wrapper
  +make-row()

.content-main
  +make-lg-column(8)

.content-secondary
  +make-lg-column(3)
  +make-lg-column-offset(1)
```

```html
<div class="wrapper">
  <div class="content-main">...</div>
  <div class="content-secondary">...</div>
</div>
```

With this technique, the HTML code is much cleaner than using classes as `.row`, `.col-md-3`, `.col-sm-6`. And is easier to maintain the code to make any visual update, just by changing the css file.

### When using .row and .col-* classes

Use rows to create horizontal groups of columns. If you're using 12 columns (bootstrap default), you never can have more than 12 columns. If more than 12 columns are placed within a single row, each group of extra columns will, as one unit, wrap onto a new line.

#### Example

```html
<div class="row">
  <div class="col-md-6">.col-md-6</div>
  <div class="col-md-6">.col-md-6</div>
</div>
<div class="row">
  <div class="col-md-6">.col-md-6</div>
  <div class="col-md-6">.col-md-6</div>
</div>
```

|.col-md-6|.col-md-6|
|---------|---------|
|.col-md-6|.col-md-6|

If you see code of grid file on bootstrap, `.row` class adds a negative margins left and right with half of variable `$grid-gutter-width`, and clearfix to break line after columns. Such as this:

```css
.row {
  margin-left: -15px;
  margin-right: -15px;
  /* clearfix code */
}
```

And for each `.col-*-*` classes, adds a positive padding left and right with half of variable `$grid-gutter-width`. `.row` class will fix the start position of first `.col-*-*` class and finish position of last `.col-*-*`, making the correct alignment.

```css
.col-*-* {
  padding-left: 15px;
  padding-right: 15px;
  /* ... */
}
```

**With this, never use `.row` class and one `col-md-12` inside of them. You're just messing your code.**

## Form

Individual form controls automatically receive some global styling. All textual <input>, <textarea>, and <select> elements with .form-control are set to width: 100%; by default. Wrap labels and controls in .form-group for optimum spacing.

```html
<form role="form">
  <div class="form-group">
    <label>Email address</label>
    <input type="email" class="form-control">
  </div>
  <div class="form-group">
    <label>Password</label>
    <input type="password" class="form-control">
  </div>
  <button type="submit" class="btn btn-default">Submit</button>
</form>
```

But to add horizontal or inline style, the Bootstrap documentation recommends you to add a lot of `.row` and `.col-md` classes for each field, for each form on your application. You can use the same technique of grid system and add this on your CSS. If in someday you will need update your form design, you can easily update it in a few CSS lines, and your markup will continue clean.

```css
.form-horizontal
  .form-group
    +make-row()

  label
    +make-md-column(3)

  .form-control
    +make-md-column(8)
    +make-lg-column-offset(1)
```

## Typography

If you're using same typography on several pages, try to customize this using variables. If not, creates a module for this, as `.title` and you can extend some helper classes used on Bootstrap, or create some stuff according to your preference. A example with this is a little above, at <a href="#classless">`Classless`</a> section.

## Bootstrap 4.0

Bootstrap's team announced on the blog some new features for Bootstrap 4. Here’s a quick preview of what’s to come:

* Updated grid system with at least one additional tier for handheld devices.
* A brand new component to replace panels, thumbnails, and wells.
* A completely new, simpler navbar.
* Switch all pixel values over to rems and ems for easier and better type and component sizing.
* Dropped support for IE8.
* Tons of form updates, including custom form controls.
* New component animations and transitions for several components.
* UMD support throughout our JavaScript plugins.
* Improved JavaScript positioning for tooltips, popovers, and dropdowns.
* Brand new documentation (written in Markdown, too!).
* A new approach to configuring global theming options.
* And hundreds more changes across the board.

## Source:
* [http://getbootstrap.com/](http://getbootstrap.com/)
* [http://htmlcsstherightway.org/](http://htmlcsstherightway.org/)
* [http://www.gotealeaf.com/blog/integrating-rails-and-bootstrap-part-1](http://www.gotealeaf.com/blog/integrating-rails-and-bootstrap-part-1)
* [https://realpython.com/blog/python/getting-started-with-bootstrap-3/](https://realpython.com/blog/python/getting-started-with-bootstrap-3/)
* [http://smacss.com/book/](http://smacss.com/book/)