
## Chapter 2

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
    limingth@gmail ~/Github/Meteor.js/todos$ tree .meteor/local/build/programs/ -a -L 3
    .meteor/local/build/programs/
    ├── server
    │   ├── app
    │   │   ├── lib
    │   │   └── server
    │   ├── assets
    │   │   └── packages
    │   ├── boot-utils.js
    │   ├── boot.js
    │   ├── config.json
    │   ├── node_modules -> /Users/limingth/.meteor/packages/meteor-tool/.1.0.40.1socvfe++os.osx.x86_64+web.browser+web.cordova/meteor-tool-os.osx.x86_64/dev_bundle/server-lib/node_modules
    │   ├── npm
    │   │   ├── ddp
    │   │   ├── email
    │   │   ├── iron:router
    │   │   ├── logging
    │   │   ├── minifiers
    │   │   ├── mongo
    │   │   ├── npm-bcrypt
    │   │   └── webapp
    │   ├── npm-shrinkwrap.json
    │   ├── package.json
    │   ├── packages
    │   │   ├── accounts-base.js
    │   │   ├── accounts-base.js.map
    │   │   ├── accounts-password.js
    │   │   ├── accounts-password.js.map
    │   │   ├── application-configuration.js
    │   │   ├── application-configuration.js.map
    │   │   ├── autoupdate.js
    │   │   ├── autoupdate.js.map
    │   │   ├── base64.js
    │   │   ├── base64.js.map
    │   │   ├── binary-heap.js
    │   │   ├── binary-heap.js.map
    │   │   ├── blaze-tools.js
    │   │   ├── blaze-tools.js.map
    │   │   ├── blaze.js
    │   │   ├── blaze.js.map
    │   │   ├── boilerplate-generator.js
    │   │   ├── boilerplate-generator.js.map
    │   │   ├── callback-hook.js
    │   │   ├── callback-hook.js.map
    │   │   ├── check.js
    │   │   ├── check.js.map
    │   │   ├── ddp.js
    │   │   ├── ddp.js.map
    │   │   ├── deps.js
    │   │   ├── deps.js.map
    │   │   ├── ejson.js
    │   │   ├── ejson.js.map
    │   │   ├── email.js
    │   │   ├── email.js.map
    │   │   ├── follower-livedata.js
    │   │   ├── follower-livedata.js.map
    │   │   ├── geojson-utils.js
    │   │   ├── geojson-utils.js.map
    │   │   ├── global-imports.js
    │   │   ├── html-tools.js
    │   │   ├── html-tools.js.map
    │   │   ├── htmljs.js
    │   │   ├── htmljs.js.map
    │   │   ├── id-map.js
    │   │   ├── id-map.js.map
    │   │   ├── insecure.js
    │   │   ├── insecure.js.map
    │   │   ├── iron_core.js
    │   │   ├── iron_core.js.map
    │   │   ├── iron_dynamic-template.js
    │   │   ├── iron_dynamic-template.js.map
    │   │   ├── iron_layout.js
    │   │   ├── iron_layout.js.map
    │   │   ├── iron_router.js
    │   │   ├── iron_router.js.map
    │   │   ├── jquery.js
    │   │   ├── jquery.js.map
    │   │   ├── json.js
    │   │   ├── json.js.map
    │   │   ├── less.js
    │   │   ├── less.js.map
    │   │   ├── livedata.js
    │   │   ├── livedata.js.map
    │   │   ├── logging.js
    │   │   ├── logging.js.map
    │   │   ├── meteor-platform.js
    │   │   ├── meteor-platform.js.map
    │   │   ├── meteor.js
    │   │   ├── meteor.js.map
    │   │   ├── minifiers.js
    │   │   ├── minifiers.js.map
    │   │   ├── minimongo.js
    │   │   ├── minimongo.js.map
    │   │   ├── mongo.js
    │   │   ├── mongo.js.map
    │   │   ├── npm-bcrypt.js
    │   │   ├── npm-bcrypt.js.map
    │   │   ├── observe-sequence.js
    │   │   ├── observe-sequence.js.map
    │   │   ├── ordered-dict.js
    │   │   ├── ordered-dict.js.map
    │   │   ├── random.js
    │   │   ├── random.js.map
    │   │   ├── reactive-dict.js
    │   │   ├── reactive-dict.js.map
    │   │   ├── reactive-var.js
    │   │   ├── reactive-var.js.map
    │   │   ├── reload.js
    │   │   ├── reload.js.map
    │   │   ├── retry.js
    │   │   ├── retry.js.map
    │   │   ├── routepolicy.js
    │   │   ├── routepolicy.js.map
    │   │   ├── service-configuration.js
    │   │   ├── service-configuration.js.map
    │   │   ├── session.js
    │   │   ├── session.js.map
    │   │   ├── sha.js
    │   │   ├── sha.js.map
    │   │   ├── spacebars-compiler.js
    │   │   ├── spacebars-compiler.js.map
    │   │   ├── spacebars.js
    │   │   ├── spacebars.js.map
    │   │   ├── srp.js
    │   │   ├── srp.js.map
    │   │   ├── templating.js
    │   │   ├── templating.js.map
    │   │   ├── tracker.js
    │   │   ├── tracker.js.map
    │   │   ├── ui.js
    │   │   ├── ui.js.map
    │   │   ├── underscore.js
    │   │   ├── underscore.js.map
    │   │   ├── webapp-hashing.js
    │   │   ├── webapp-hashing.js.map
    │   │   ├── webapp.js
    │   │   └── webapp.js.map
    │   ├── program.json
    │   ├── shell.js
    │   └── start.sh
    ├── web.browser
    │   ├── 441446561166576bf5533950a789ecac8d1ce87f.css
    │   ├── 441446561166576bf5533950a789ecac8d1ce87f.css.map
    │   ├── app
    │   │   ├── apple-touch-icon-precomposed.png
    │   │   ├── client
    │   │   ├── favicon.png
    │   │   ├── font
    │   │   ├── icon
    │   │   ├── img
    │   │   └── lib
    │   ├── head.html
    │   ├── packages
    │   │   ├── accounts-base.js
    │   │   ├── accounts-base.js.map
    │   │   ├── accounts-password.js
    │   │   ├── accounts-password.js.map
    │   │   ├── application-configuration.js
    │   │   ├── application-configuration.js.map
    │   │   ├── autoupdate.js
    │   │   ├── autoupdate.js.map
    │   │   ├── base64.js
    │   │   ├── base64.js.map
    │   │   ├── blaze.js
    │   │   ├── blaze.js.map
    │   │   ├── check.js
    │   │   ├── check.js.map
    │   │   ├── ddp.js
    │   │   ├── ddp.js.map
    │   │   ├── deps.js
    │   │   ├── deps.js.map
    │   │   ├── ejson.js
    │   │   ├── ejson.js.map
    │   │   ├── follower-livedata.js
    │   │   ├── follower-livedata.js.map
    │   │   ├── geojson-utils.js
    │   │   ├── geojson-utils.js.map
    │   │   ├── global-imports.js
    │   │   ├── htmljs.js
    │   │   ├── htmljs.js.map
    │   │   ├── id-map.js
    │   │   ├── id-map.js.map
    │   │   ├── insecure.js
    │   │   ├── insecure.js.map
    │   │   ├── iron_core.js
    │   │   ├── iron_core.js.map
    │   │   ├── iron_dynamic-template.js
    │   │   ├── iron_dynamic-template.js.map
    │   │   ├── iron_layout.js
    │   │   ├── iron_layout.js.map
    │   │   ├── iron_router.js
    │   │   ├── iron_router.js.map
    │   │   ├── jquery.js
    │   │   ├── jquery.js.map
    │   │   ├── json.js
    │   │   ├── json.js.map
    │   │   ├── launch-screen.js
    │   │   ├── launch-screen.js.map
    │   │   ├── less.js
    │   │   ├── less.js.map
    │   │   ├── livedata.js
    │   │   ├── livedata.js.map
    │   │   ├── localstorage.js
    │   │   ├── localstorage.js.map
    │   │   ├── logging.js
    │   │   ├── logging.js.map
    │   │   ├── meteor-platform.js
    │   │   ├── meteor-platform.js.map
    │   │   ├── meteor.js
    │   │   ├── meteor.js.map
    │   │   ├── minimongo.js
    │   │   ├── minimongo.js.map
    │   │   ├── mongo.js
    │   │   ├── mongo.js.map
    │   │   ├── observe-sequence.js
    │   │   ├── observe-sequence.js.map
    │   │   ├── ordered-dict.js
    │   │   ├── ordered-dict.js.map
    │   │   ├── random.js
    │   │   ├── random.js.map
    │   │   ├── reactive-dict.js
    │   │   ├── reactive-dict.js.map
    │   │   ├── reactive-var.js
    │   │   ├── reactive-var.js.map
    │   │   ├── reload.js
    │   │   ├── reload.js.map
    │   │   ├── retry.js
    │   │   ├── retry.js.map
    │   │   ├── service-configuration.js
    │   │   ├── service-configuration.js.map
    │   │   ├── session.js
    │   │   ├── session.js.map
    │   │   ├── sha.js
    │   │   ├── sha.js.map
    │   │   ├── spacebars.js
    │   │   ├── spacebars.js.map
    │   │   ├── srp.js
    │   │   ├── srp.js.map
    │   │   ├── templating.js
    │   │   ├── templating.js.map
    │   │   ├── tracker.js
    │   │   ├── tracker.js.map
    │   │   ├── ui.js
    │   │   ├── ui.js.map
    │   │   ├── underscore.js
    │   │   ├── underscore.js.map
    │   │   ├── webapp.js
    │   │   └── webapp.js.map
    │   └── program.json
    └── web.cordova
        ├── 441446561166576bf5533950a789ecac8d1ce87f.css
        ├── 441446561166576bf5533950a789ecac8d1ce87f.css.map
        ├── app
        │   ├── apple-touch-icon-precomposed.png
        │   ├── client
        │   ├── favicon.png
        │   ├── font
        │   ├── icon
        │   ├── img
        │   └── lib
        ├── head.html
        ├── packages
        │   ├── accounts-base.js
        │   ├── accounts-base.js.map
        │   ├── accounts-password.js
        │   ├── accounts-password.js.map
        │   ├── application-configuration.js
        │   ├── application-configuration.js.map
        │   ├── autoupdate.js
        │   ├── autoupdate.js.map
        │   ├── base64.js
        │   ├── base64.js.map
        │   ├── blaze.js
        │   ├── blaze.js.map
        │   ├── check.js
        │   ├── check.js.map
        │   ├── ddp.js
        │   ├── ddp.js.map
        │   ├── deps.js
        │   ├── deps.js.map
        │   ├── ejson.js
        │   ├── ejson.js.map
        │   ├── fastclick.js
        │   ├── fastclick.js.map
        │   ├── follower-livedata.js
        │   ├── follower-livedata.js.map
        │   ├── geojson-utils.js
        │   ├── geojson-utils.js.map
        │   ├── global-imports.js
        │   ├── htmljs.js
        │   ├── htmljs.js.map
        │   ├── http.js
        │   ├── http.js.map
        │   ├── id-map.js
        │   ├── id-map.js.map
        │   ├── insecure.js
        │   ├── insecure.js.map
        │   ├── iron_core.js
        │   ├── iron_core.js.map
        │   ├── iron_dynamic-template.js
        │   ├── iron_dynamic-template.js.map
        │   ├── iron_layout.js
        │   ├── iron_layout.js.map
        │   ├── iron_router.js
        │   ├── iron_router.js.map
        │   ├── jquery.js
        │   ├── jquery.js.map
        │   ├── json.js
        │   ├── json.js.map
        │   ├── launch-screen.js
        │   ├── launch-screen.js.map
        │   ├── less.js
        │   ├── less.js.map
        │   ├── livedata.js
        │   ├── livedata.js.map
        │   ├── localstorage.js
        │   ├── localstorage.js.map
        │   ├── logging.js
        │   ├── logging.js.map
        │   ├── meteor-platform.js
        │   ├── meteor-platform.js.map
        │   ├── meteor.js
        │   ├── meteor.js.map
        │   ├── minimongo.js
        │   ├── minimongo.js.map
        │   ├── mobile-status-bar.js
        │   ├── mobile-status-bar.js.map
        │   ├── mongo.js
        │   ├── mongo.js.map
        │   ├── observe-sequence.js
        │   ├── observe-sequence.js.map
        │   ├── ordered-dict.js
        │   ├── ordered-dict.js.map
        │   ├── random.js
        │   ├── random.js.map
        │   ├── reactive-dict.js
        │   ├── reactive-dict.js.map
        │   ├── reactive-var.js
        │   ├── reactive-var.js.map
        │   ├── reload.js
        │   ├── reload.js.map
        │   ├── retry.js
        │   ├── retry.js.map
        │   ├── service-configuration.js
        │   ├── service-configuration.js.map
        │   ├── session.js
        │   ├── session.js.map
        │   ├── sha.js
        │   ├── sha.js.map
        │   ├── spacebars.js
        │   ├── spacebars.js.map
        │   ├── srp.js
        │   ├── srp.js.map
        │   ├── templating.js
        │   ├── templating.js.map
        │   ├── tracker.js
        │   ├── tracker.js.map
        │   ├── ui.js
        │   ├── ui.js.map
        │   ├── underscore.js
        │   ├── underscore.js.map
        │   ├── url.js
        │   ├── url.js.map
        │   ├── webapp.js
        │   └── webapp.js.map
        └── program.json
    
    33 directories, 331 files
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
