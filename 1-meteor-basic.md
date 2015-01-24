
## Chapter 1
### 1 Seven Principles
* [Meteor Seven Principles](https://docs.meteor.com/#/full/severnprinciples)

### 2 Web Dev History
####Old time
* html 
* css
* js
* DOM

#### Second age
* ajax 
* json

#### Now fasion
* meteor
* DDP 
* socket.io (based on websocket)
* data on 

### 3 Debuggin Todos
####  Inspect Elements -> Preview
    <body> </body>
  
* body is empty
  
####  template-hello.js 
    <script type="text/javascript" src="/client/template.hello.js?e61cdb4581122c6da2d9d39dce3157cca56f6975"></script>

* Inspect Elements -> Network -> Frames

### 4 Processing
* MongoDB Server
* mini mongo
* Lists

#### 5 hands-on
    limingth@gmail ~/Github/Meteor.js$ meteor create --example todos
    todos: created.                               
    
    To run your new app:                          
      cd todos                                    
      meteor                                      
    limingth@gmail ~/Github/Meteor.js$ cd todos/  
    limingth@gmail ~/Github/Meteor.js/todos$ 
    
    limingth@gmail ~/Github/Meteor.js/todos$ tree
    .
    ├── client
    │   ├── head.html
    │   ├── lib
    │   │   └── jquery.touchwipe.js
    │   ├── stylesheets
    │   │   ├── globals
    │   │   │   ├── base.import.less
    │   │   │   ├── button.import.less
    │   │   │   ├── form.import.less
    │   │   │   ├── icon.import.less
    │   │   │   ├── layout.import.less
    │   │   │   ├── link.import.less
    │   │   │   ├── list-items.import.less
    │   │   │   ├── menu.import.less
    │   │   │   ├── message.import.less
    │   │   │   ├── nav.import.less
    │   │   │   └── notification.import.less
    │   │   ├── main.less
    │   │   └── util
    │   │       ├── fontface.import.less
    │   │       ├── helpers.import.less
    │   │       ├── lesshat.import.less
    │   │       ├── reset.import.less
    │   │       ├── text.import.less
    │   │       ├── typography.import.less
    │   │       └── variables.import.less
    │   └── templates
    │       ├── app-body.html
    │       ├── app-body.js
    │       ├── app-not-found.html
    │       ├── app-not-found.import.less
    │       ├── auth-join.html
    │       ├── auth-join.js
    │       ├── auth-signin.html
    │       ├── auth-signin.js
    │       ├── auth.import.less
    │       ├── lists-show.html
    │       ├── lists-show.import.less
    │       ├── lists-show.js
    │       ├── loading.html
    │       ├── loading.import.less
    │       ├── todos-item.html
    │       └── todos-item.js
    ├── lib
    │   ├── collections.js
    │   └── router.js
    ├── mobile-config.js
    ├── public
    │   ├── apple-touch-icon-precomposed.png
    │   ├── favicon.png
    │   ├── font
    │   │   ├── OpenSans-Light-webfont.eot
    │   │   ├── OpenSans-Light-webfont.svg
    │   │   ├── OpenSans-Light-webfont.ttf
    │   │   ├── OpenSans-Light-webfont.woff
    │   │   ├── OpenSans-Regular-webfont.eot
    │   │   ├── OpenSans-Regular-webfont.svg
    │   │   ├── OpenSans-Regular-webfont.ttf
    │   │   └── OpenSans-Regular-webfont.woff
    │   ├── icon
    │   │   ├── todos.eot
    │   │   ├── todos.svg
    │   │   ├── todos.ttf
    │   │   └── todos.woff
    │   └── img
    │       └── logo-todos.svg
    ├── resources
    │   ├── icons
    │   │   ├── icon-29x29.png
    │   │   ├── icon-29x29@2x.png
    │   │   ├── icon-36x36.png
    │   │   ├── icon-40x40.png
    │   │   ├── icon-40x40@2x.png
    │   │   ├── icon-48x48.png
    │   │   ├── icon-50x50.png
    │   │   ├── icon-50x50@2x.png
    │   │   ├── icon-57x57.png
    │   │   ├── icon-57x57@2x.png
    │   │   ├── icon-60x60.png
    │   │   ├── icon-60x60@2x.png
    │   │   ├── icon-72x72.png
    │   │   ├── icon-72x72@2x.png
    │   │   ├── icon-76x76.png
    │   │   ├── icon-76x76@2x.png
    │   │   └── icon-96x96.png
    │   └── splash
    │       ├── splash-1024x768.png
    │       ├── splash-1024x768@2x.png
    │       ├── splash-1280x720.png
    │       ├── splash-200x320.png
    │       ├── splash-320x200.png
    │       ├── splash-320x480.png
    │       ├── splash-320x480@2x.png
    │       ├── splash-320x568@2x.png
    │       ├── splash-480x320.png
    │       ├── splash-480x800.png
    │       ├── splash-720x1280.png
    │       ├── splash-768x1024.png
    │       ├── splash-768x1024@2x.png
    │       └── splash-800x480.png
    └── server
        ├── bootstrap.js
        └── publish.js
    
    15 directories, 88 files
    limingth@gmail ~/Github/Meteor.js/todos$ 

#### 
* JavaScript 是很"牛"的"烂"语言
* Lists = new Meteor.Collection('lists')  默认是全局的
* var Lists = new Meteor.Collection('lists')  才是局部的

#### MongoDB 
http://docs.mongodb.org/manual/

    > Lists.find()
    LocalCollection.Cursor {collection: LocalCollection, sorter: null, _selectorId: undefined, matcher: Minimongo.Matcher, skip: undefined…}
    
    > Lists.find().fetch()
    [Object_id: "ZMSREPRKvTchnvwnT"incompleteCount: 7name: "Meteor Principles"__proto__: Object__defineGetter__: function __defineGetter__() { [native code] }__defineSetter__: function __defineSetter__() { [native code] }__lookupGetter__: function __lookupGetter__() { [native code] }__lookupSetter__: function __lookupSetter__() { [native code] }constructor: function Object() { [native code] }hasOwnProperty: function hasOwnProperty() { [native code] }isPrototypeOf: function isPrototypeOf() { [native code] }propertyIsEnumerable: function propertyIsEnumerable() { [native code] }toLocaleString: function toLocaleString() { [native code] }toString: function toString() { [native code] }valueOf: function valueOf() { [native code] }get __proto__: function __proto__() { [native code] }set __proto__: function __proto__() { [native code] }
    
### 在 client 和 server 中都会执行
    limingth@gmail ~/Github/Meteor.js/todos$ cat lib/collections.js 
    Lists = new Meteor.Collection('lists');
    
    // Calculate a default name for a list in the form of 'List A'
    Lists.defaultName = function() {
      var nextLetter = 'A', nextName = 'List ' + nextLetter;
      while (Lists.findOne({name: nextName})) {
        // not going to be too smart here, can go past Z
        nextLetter = String.fromCharCode(nextLetter.charCodeAt(0) + 1);
        nextName = 'List ' + nextLetter;
      }
    
      return nextName;
    };
    
    Todos = new Meteor.Collection('todos');limingth@gmail ~/Github/Meteor.js/todos$ 
    
    if (Meteor.isServer) {
      console.log ("I am server")
    }
    
    if (Meteor.isClient) {
      console.log ("I am client")
    }
    
#### Hot Code Push
* 后端 js -> Node.js 
* 前端 webbrowser 也会有一个js在实时监控代码变化
* 手机 cordova (以前的phoneGap)

#### famo.us
* https://www.meteor.com/blog/2014/06/03/meteor-famous-mobile

#### code tree
    limingth@gmail ~/Github/Meteor.js/todos$ ls .meteor/local/build/programs/server/
    app			config.json		package.json		start.sh
    assets			node_modules		packages
    boot-utils.js		npm			program.json
    boot.js			npm-shrinkwrap.json	shell.js
    limingth@gmail ~/Github/Meteor.js/todos$ ls .meteor/local/build/programs/web.browser/
    441446561166576bf5533950a789ecac8d1ce87f.css
    441446561166576bf5533950a789ecac8d1ce87f.css.map
    app
    head.html
    packages
    program.json
    limingth@gmail ~/Github/Meteor.js/todos$ ls .meteor/local/build/programs/web.cordova/
    441446561166576bf5533950a789ecac8d1ce87f.css
    441446561166576bf5533950a789ecac8d1ce87f.css.map
    app
    head.html
    packages
    program.json
    limingth@gmail ~/Github/Meteor.js/todos$ 
    
#### code tree in .meteor 
    limingth@gmail ~/Github/Meteor.js/todos$ tree .meteor/ -a -L 4
    .meteor/
    ├── .finished-upgraders
    ├── .gitignore
    ├── .id
    ├── local
    │   ├── build
    │   │   ├── README
    │   │   ├── main.js
    │   │   ├── programs
    │   │   │   ├── server
    │   │   │   ├── web.browser
    │   │   │   └── web.cordova
    │   │   ├── server
    │   │   │   └── .bundle_version.txt
    │   │   └── star.json
    │   ├── db
    │   │   ├── METEOR-PORT
    │   │   ├── journal
    │   │   │   └── j._0
    │   │   ├── local.0
    │   │   ├── local.1
    │   │   ├── local.ns
    │   │   ├── meteor.0
    │   │   ├── meteor.1
    │   │   ├── meteor.ns
    │   │   └── mongod.lock
    │   ├── isopacks
    │   └── shell.sock
    ├── packages
    ├── platforms
    ├── release
    └── versions
    
    10 directories, 21 files

