
### Step 4 publish and subscribe

* http://zh.discovermeteor.com/chapters/publications-and-subscriptions/

#### meteor remove autopublish
	vi server/publications.js

	Meteor.publish('posts', function() {
	  return Posts.find();
	});

#### meteor.subscribe
	vi client/main.js

	Meteor.subscribe('posts');
	

### 2 filt the data

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

#### 3 Publishing Full Collections

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






