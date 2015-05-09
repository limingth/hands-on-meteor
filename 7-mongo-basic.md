## MongoDB 
* http://docs.mongodb.org/manual/

### example query string
    > Lists.find()
    LocalCollection.Cursor {collection: LocalCollection, sorter: null, _selectorId: undefined, matcher: Minimongo.Matcher, skip: undefined…}
    
    > Lists.find().fetch()
    [Object_id: "ZMSREPRKvTchnvwnT"incompleteCount: 7name: "Meteor Principles"__proto__: Object__defineGetter__: function __defineGetter__() { [native code] }__defineSetter__: function __defineSetter__() { [native code] }__lookupGetter__: function __lookupGetter__() { [native code] }__lookupSetter__: function __lookupSetter__() { [native code] }constructor: function Object() { [native code] }hasOwnProperty: function hasOwnProperty() { [native code] }isPrototypeOf: function isPrototypeOf() { [native code] }propertyIsEnumerable: function propertyIsEnumerable() { [native code] }toLocaleString: function toLocaleString() { [native code] }toString: function toString() { [native code] }valueOf: function valueOf() { [native code] }get __proto__: function __proto__() { [native code] }set __proto__: function __proto__() { [native code] }
	
	> db.users.findOne({'profile.login': 'pp2code'}, {limit:10})
	{ "_id" : "kEGkxCdaiu36Q6dmi" }
	
	> db.users.remove({});    如果需要对某个 collection 全部删除，()里面必须加入 {}
	
	> db.users.remove({_id: 'kEGkxCdaiu36Q6dmi'}, 1);
	> db.users.findOne({'profile.login': 'pp2code'}, {limit:10})
	null
	> db.users.remove({'profile.login': 'pp2code'});
	> db.players.update({_id:"CWuxjkfuBHyv9cbkX"}, {$inc: {score: -1}});
	> db.voters.remove({name:"Larry"});
	> db.lessons.find({name:{ $in:["hello", "world"]}})
	> db.lessons.find({name: {$regex: /^meteor*/}})
	> db.courses.remove({title: {$regex:/^MyT*/}})
	WriteResult({ "nRemoved" : 1 })
	> db.courses.find({title: {$regex:/^MyT*/}})

### Complex query string
http://docs.mongodb.org/manual/reference/method/db.collection.find/
http://docs.mongodb.org/manual/reference/operator/query/or/#op._S_or
http://docs.mongodb.org/manual/reference/operator/query/regex/#syntax-restrictions

    return Meteor.users.find({
      $or:
      [
        { skills: {
              $elemMatch: {
                language: { $regex: RegExp.escape(query), $options: 'i' }
              }
            }
        },
        { repos: {
              $elemMatch: {
                name: { $regex: RegExp.escape(query), $options: 'i' }
              }
            }
        },
        { repos: {
              $elemMatch: {
                description: { $regex: RegExp.escape(query), $options: 'i' }
              }
            }
        },
        {
          'profile.name': { $regex: RegExp.escape(query), $options: 'i' }
        },
        {
          'profile.email': { $regex: RegExp.escape(query), $options: 'i' }
        },
        {
          'profile.login': { $regex: RegExp.escape(query), $options: 'i' }
        }
      ]
    });
  };
