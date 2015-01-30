
### Step 5 routing

* http://zh.discovermeteor.com/chapters/routing/

#### Add iron:router package
	meteor add iron:router

#### Change main.html
	<head>
	  <title>Microscope</title>
	</head>
	<body>
	  <div class="container">
	    <header class="navbar navbar-default" role="navigation"> 
	      <div class="navbar-header">
	        <a class="navbar-brand" href="/">Microscope</a>
	      </div>
	    </header>
	    <div id="main" class="row-fluid">
	      {{> postsList}}
	    </div>
	  </div>
	</body>

	to 

	<head>
	  <title>Microscope</title>
	</head>

#### Add a layout file
	li@MacbookAir ~/Github/meteor-maodou$ cat client/templates/application/layout.html
	<template name="layout">
	  <div class="container">
	    <header class="navbar navbar-default" role="navigation"> 
	      <div class="navbar-header">
	        <a class="navbar-brand" href="/">Microscope</a>
	      </div>
	    </header>
	    <div id="main" class="row-fluid">
	      {{> yield}}
	    </div>
	  </div>
	</template>

#### Create a router.js
	li@MacbookAir ~/Github/meteor-maodou$ cat lib/router.js
	Router.configure({
	  layoutTemplate: 'layout'
	});

	Router.route('/', {name: 'postsList'});

* Everything is ok now, same as before


#### Move the posts subscription to route.js
	li@MacbookAir ~/Github/meteor-maodou$ cat lib/router.js
	Router.configure({
	  layoutTemplate: 'layout',
	  waitOn: function() { return Meteor.subscribe('posts'); }
	});

	Router.route('/', {name: 'postsList'});

	li@MacbookAir ~/Github/meteor-maodou$ cat client/meteor-maodou.coffee 
	#Meteor.subscribe('posts');

* Refresh the browser, see there is a "loading..." emerged

### Get A Load Of This
#### add a loading template to router
	li@MacbookAir ~/Github/meteor-maodou$ cat lib/router.js 
	Router.configure({
	  layoutTemplate: 'layout',
	  loadingTemplate: 'loading',
	  waitOn: function() { return Meteor.subscribe('posts'); }
	});

	Router.route('/', {name: 'postsList'});

#### add a spinner template
	li@MacbookAir ~/Github/meteor-maodou$ mkdir client/templates/includes
	li@MacbookAir ~/Github/meteor-maodou$ vi client/templates/includes/loading.html
	li@MacbookAir ~/Github/meteor-maodou$ cat client/templates/includes/loading.html
	<template name="loading">
	  {{>spinner}}
	</template>
	li@MacbookAir ~/Github/meteor-maodou$ 

#### meteor add sacha:spin 
	li@MacbookAir ~/Github/meteor-maodou$ meteor add sacha:spin 
	                                              
	Changes to your project's package version selections:
	                                              
	sacha:spin  added, version 2.0.4              

	                                              
	sacha:spin: Simple spinner package for Meteor 
	li@MacbookAir ~/Github/meteor-maodou$  

https://www.discovermeteor.com/blog/a-guide-to-meteor-templates-data-contexts/


#### add a not found template
	li@MacbookAir ~/Github/meteor-maodou$ cat client/templates/application/not_found.html
	<template name="notFound">
	  <div class="not-found jumbotron">
	    <h2>404</h2>
	    <p>Sorry, we couldn't find a page at this address. 抱歉，我们无法找到该页面。</p>
	  </div>
	</template>
	li@MacbookAir ~/Github/meteor-maodou$ 

* http://localhost:3000/wrongurl   you can see our 404 page now..


