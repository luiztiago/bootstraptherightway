# Bootstrap: The Right Way

	Inspired on others "The Right Way's" projects. A compilation of good pratices to use Bootstrap.
	
We do not deliver a cake recipe for you. We will show positive and negative points to be analyzed and used according to the needs of your project.

## Getting started

Bootstrap has a few easy ways to quickly get started, each one appealing to a different skill level and use case. Read through to see what suits your particular needs.

### Download or CDN

Compiled and minified CSS, JavaScript, and fonts. No docs or original source files are included. 

| +1                                                              | -1                                        |
|-----------------------------------------------------------------|-------------------------------------------|
| Increases the parallelism available.                            | Imports all the bootstrap code            |
| Increases the chance that there will be a cache-hit.            | Does not allow customization of variables |
| Ensures that the payload will be as small as possible.          | Does not allow use of mixins              |
| Reduces the amount of bandwidth used by your server.            | 
| Ensures that the user will get a geographically close response. | 


* Download: [https://github.com/twbs/bootstrap/releases/download/v3.3.1/bootstrap-3.3.1-dist.zip](https://github.com/twbs/bootstrap/releases/download/v3.3.1/bootstrap-3.3.1-dist.zip)

* Or, use these CDN links

```html
<!-- Latest compiled and minified CSS -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.1/css/bootstrap.min.css">

<!-- Optional theme -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.1/css/bootstrap-theme.min.css">

<!-- Latest compiled and minified JavaScript -->
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.1/js/bootstrap.min.js"></script>
```

### Bower
Install and manage Bootstrap's Sass, CSS, JavaScript, and fonts using Bower.

```
$ bower install bootstrap
```
 	
### Rails Gem

Add gem on Gemfile file. You can choose use SASS or LESS port of bootstrap. The most common applications on Rails, is to use the port in SASS

```
gem 'bootstrap-sass', '~> 3.3.1'
```

## Customization

When you are using a framework such as Bootstrap, a CSS preprocessor is going to be involved. They enhance the vanilla CSS and add functionality such as use of variables, mixins and nesting of rules.

## Grid

You can modify the variables to your own custom values, or just use the mixins with their default values. Here's an example of using the default settings to create a two-column layout with a gap between.

With this technique, the HTML code is much cleaner than using classes as `.row`, `.col-md-3`, `.col-sm-6`. And is easier to maintain the code to make any visual update, just by changing the css file.

```css
.wrapper {
  .make-row();
}
.content-main {
  .make-lg-column(8);
}
.content-secondary {
  .make-lg-column(3);
  .make-lg-column-offset(1);
}
```

```html
<div class="wrapper">
  <div class="content-main">...</div>
  <div class="content-secondary">...</div>
</div>
```

## Source:
* [http://getbootstrap.com/](http://getbootstrap.com/)
* [http://htmlcsstherightway.org/](http://htmlcsstherightway.org/)
* [http://www.gotealeaf.com/blog/integrating-rails-and-bootstrap-part-1](http://www.gotealeaf.com/blog/integrating-rails-and-bootstrap-part-1)
* [https://realpython.com/blog/python/getting-started-with-bootstrap-3/](https://realpython.com/blog/python/getting-started-with-bootstrap-3/)
* [http://untame.net/2012/08/twitter-bootstrap-how-to-load-sites-faster-with-bootstrapcdn/](http://untame.net/2012/08/twitter-bootstrap-how-to-load-sites-faster-with-bootstrapcdn/)