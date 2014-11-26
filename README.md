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

	<!-- Latest compiled and minified CSS -->
	<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.1/css/bootstrap.min.css">

	<!-- Optional theme -->
	<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.1/css/bootstrap-theme.min.css">

	<!-- Latest compiled and minified JavaScript -->
	<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.1/js/bootstrap.min.js"></script>
