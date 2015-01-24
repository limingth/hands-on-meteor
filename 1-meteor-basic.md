
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