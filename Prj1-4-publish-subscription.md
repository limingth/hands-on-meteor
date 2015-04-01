
### Step 4 publish and subscribe

Understanding Meteor Publish / Subscribe
* http://stackoverflow.com/questions/19826804/understanding-meteor-publish-subscribe

```
Meteor.subscribe('record-set-name')
calls. Note that the parameter to subscribe isn't a collection name; 
it's the name of a record set that the server used in the publish call. 

The subscribe() call subscribes the client to a record set - a subset of records from the server collection (e.g. most recent 100 blog posts), 

with all or a subset of the fields in each record (e.g. only title and date). 
How does Minimongo know into which collection to place the incoming records? 
The name of the collection will be the collection argument used in the publish handler's added, 
changed, and removed callbacks, or if those are missing (which is the case most of the time), 
it will be the name of the MongoDB collection on the server.
```

发布与订阅 附录
* http://zh.discovermeteor.com/chapters/publications-and-subscriptions/

#### meteor remove autopublish
	vi server/publications.js

	Meteor.publish('posts', function() {
	  return Posts.find();
	});

#### meteor.subscribe
	vi client/main.js

	Meteor.subscribe('posts');
	

### filt the data

#### Only publish those not flagged
	// On the server
	Meteor.publish('posts', function() {
	  return Posts.find({flagged: false}); 
	});

#### Only publish those not flagged and specific author
	Meteor.publish('posts', function(author) {
	  return Posts.find({flagged: false, author: author});
	});

	// On the client
	Meteor.subscribe('posts', 'bob-smith');

#### Select those specific category from subscribe
	// On the client
	Template.posts.helpers({
	  posts: function(){
	    return Posts.find(author: 'bob-smith', category: 'JavaScript');
	  }
	});

#### Publishing Full Collections

	Meteor.publish('allPosts', function(){
	  return Posts.find();
	});


#### Publishing Partial Collections
	// only tom's posts
	Meteor.publish('somePosts', function(){
	  return Posts.find({'author': 'Tom'});
	});

	// only tom's posts and hiding the date
	Meteor.publish('allPosts', function(){
	  return Posts.find({}, {fields: {
	    date: false
	  }});
	});




