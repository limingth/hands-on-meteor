
### Step 4 publish and subscribe

Understanding Meteor Publish / Subscribe
* http://stackoverflow.com/questions/19826804/understanding-meteor-publish-subscribe

```
To properly understand why you need to call find() more than once, you need to understand how collections, publications and subscriptions work in in Meteor:

You define collections in MongoDB. No Meteor involved yet. These collections contain database records (also called "documents" by both Mongo and Meteor, but a "document" is more general than a database record; for instance, an update specification or a query selector are documents too - JavaScript objects containing field: value pairs).

Then you define collections on the Meteor server with

MyCollection = new Mongo.Collection('collection-name-in-mongo')
These collections contain all the data from the MongoDB collections, and you can run MyCollection.find({...}) on them, which will return a cursor (a set of records, with methods to iterate through them and return them).

This cursor is (most of the time) used to publish (send) a set of records (called a "record set"). You can optionally publish only some fields from those records. It is record sets (not collections) that clients subscribe to. Publishing is done by a publish function, which is run every time a new client subscribes, and which can take parameters to manage which records to return (e.g. a user id, to return only that user's documents).

On the client, you have Minimongo collections that partially mirror some of the records from the server. "Partially" because they may contain only some of the fields, and "some of the records" because you usually want to send to the client only the records it needs, to speed up page load, and only those it needs and has permission to access.

Minimongo is essentially an in-memory, non-persistent implementation of Mongo in pure JavaScript. It serves as a local cache that stores just the subset of the database that this client is working with. Queries on the client (find) are served directly out of this cache, without talking to the server.
These Minimongo collections are initially empty. They are filled by

Meteor.subscribe('record-set-name')
calls. Note that the parameter to subscribe isn't a collection name; it's the name of a record set that the server used in the publish call. The subscribe() call subscribes the client to a record set - a subset of records from the server collection (e.g. most recent 100 blog posts), with all or a subset of the fields in each record (e.g. only title and date). How does Minimongo know into which collection to place the incoming records? The name of the collection will be the collection argument used in the publish handler's added, changed, and removed callbacks, or if those are missing (which is the case most of the time), it will be the name of the MongoDB collection on the server.
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




