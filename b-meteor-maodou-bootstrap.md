
## Chapter B 

### 1 Add Bootstrap to maodou
http://zh.discovermeteor.com/chapters/getting-started/

#### meteor add mizzao:bootstrap-3
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ meteor add mizzao:bootstrap-3
	                                                                                   
	Changes to your project's package version selections:
	                                              
	mizzao:bootstrap-3  added, version 3.3.1_1    

	                                              
	mizzao:bootstrap-3: HTML, CSS, and JS framework for developing responsive, mobile first projects on the
	web.
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ 

#### cat .meteor/packages 
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ cat .meteor/packages 
	# Meteor packages used by this project, one per line.
	# Check this file (and the other files in this directory) into your repository.
	#
	# 'meteor add' and 'meteor remove' will edit this file for you,
	# but you can also edit it by hand.

	meteor-platform
	autopublish
	insecure
	mizzao:bootstrap-3
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ 

#### meteor run
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ meteor
	[[[[[ ~/Github/Meteor.js/meteor-maodou ]]]]]  

	=> Started proxy.                             
	=> Started MongoDB.                           
	=> Started your app.                          

	=> App running at: http://localhost:3000/

### 2 Redefine the structure of code
#### mkdir client server public lib
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ mv meteor-maodou.* client/
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ ls
	README.md	client		lib		public		server
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ tree
	.
	├── README.md
	├── client
	│   ├── meteor-maodou.css
	│   ├── meteor-maodou.html
	│   └── meteor-maodou.js
	├── lib
	├── public
	└── server

	4 directories, 4 files
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ 

### 3 Change js to coffeescript
http://js2coffee.org/

#### meteor add coffeescript
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ meteor add coffeescript
	                                                      
	Changes to your project's package version selections:
	                                              
	coffeescript  added, version 1.0.5            

	                                              
	coffeescript: Javascript dialect with fewer braces and semicolons
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ cat .meteor/packages 
	# Meteor packages used by this project, one per line.
	# Check this file (and the other files in this directory) into your repository.
	#
	# 'meteor add' and 'meteor remove' will edit this file for you,
	# but you can also edit it by hand.

	meteor-platform
	autopublish
	insecure
	mizzao:bootstrap-3
	coffeescript
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ 

### 4 Add files and directories
http://zh.discovermeteor.com/chapters/templates/

	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ tree
	.
	├── README.md
	├── client
	│   ├── meteor-maodou.coffee
	│   ├── meteor-maodou.css
	│   ├── meteor-maodou.html
	│   ├── stylesheets
	│   │   └── style.css
	│   └── views
	│       └── posts
	│           ├── post_item.html
	│           ├── post_item.js
	│           ├── posts_list.html
	│           └── posts_list.js
	├── lib
	├── public
	└── server

	7 directories, 9 files
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ 




