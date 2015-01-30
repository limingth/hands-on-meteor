
## Chapter C
http://zh.discovermeteor.com/chapters/collections/

### 1 Add Collection to maodou

#### vi posts.js
	Posts = new Meteor.Collection('posts');

Posts will be both accessible by client and server

#### add posts.js under lib/collection
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
	│   └── collection
	│       └── posts.js
	├── public
	└── server

	8 directories, 10 files
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ 

#### meteor mongo
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ meteor mongo
	MongoDB shell version: 2.4.12
	connecting to: 127.0.0.1:3001/meteor
	Server has startup warnings: 
	Mon Jan 26 17:38:38.786 [initandlisten] 
	Mon Jan 26 17:38:38.786 [initandlisten] ** WARNING: soft rlimits too low. rlimits set to 266 processes, 8192 files. Number of processes should be at least 4096 : 0.5 times number of files.
	meteor:PRIMARY> show collections
	posts
	system.indexes
	meteor:PRIMARY> db.posts.find()
	{ "title" : "Introducing Telescope", "url" : "http://sachagreif.com/introducing-telescope/", "_id" : "PuC2JqKarRNfRdrkD" }
	{ "title" : "Meteor", "url" : "http://meteor.com", "_id" : "JZecJoRhSD7rdXwM4" }
	{ "title" : "The Meteor Book", "url" : "http://themeteorbook.com", "_id" : "XppkaXWDMDJKXzLtq" }
	meteor:PRIMARY> db.posts.remove()
	meteor:PRIMARY> db.posts.find()
	meteor:PRIMARY> 	

#### a trick to clear all collections in db
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ meteor reset
	Project reset.  