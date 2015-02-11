
## Welog 项目

### 项目代码库
* https://github.com/kevingzhang/welog

### 代码分析

#### layout 框架
	{{#ionBody}}
	  {{#ionSideMenuContainer}}
		  {{#ionSideMenu}}  // default 是左边的 menu，向左拉动可以看到
		  {{/ionSideMenu}}

		  {{#ionSideMenu side="right"}}  // 右边的 menu，向右拉动可以看到
		  {{/ionSideMenu}}

		  {{#ionSideMenuContent}}	// 中间的全部区域
		    {{> ionNavBar class="bar-positive"}}	// 中间的顶部 navbar
		    {{#ionNavView}}
		      {{> yield}}			// 根据 route 来确定 render 那个 template
		    {{/ionNavView}}
		  {{/ionSideMenuContent}}
	  {{/ionSideMenuContainer}}
	{{/ionBody}}

* https://github.com/kevingzhang/welog/blob/master/client/layout.html  

#### Router 路由
	Router.map(function() {
	  this.route('index', {path: '/'});
	  this.route('actionSheet');
	  this.route('backdrop');
	  this.route('forms', {
	    data: function () {
	      return {
	        post: Posts.find().fetch()[0]
	      };
	    }
	  });
	  this.route('headersFooters');
	  this.route('lists');
	  this.route('loading');
	  this.route('modal');
	  this.route('navigation');
	  this.route('navigation.one', {path: '/navigation/one'});
	  this.route('navigation.two', {path: '/navigation/two'});
	  this.route('navigation.three', {path: '/navigation/three'});
	  this.route('popover');
	  this.route('popup');
	  this.route('sideMenu');
	  this.route('slideBox');
	  this.route('tabs.one', {path: '/tabs/one', layoutTemplate: 'tabsLayout'});
	  this.route('tabs.two', {path: '/tabs/two', layoutTemplate: 'tabsLayout'});
	  this.route('tabs.three', {path: '/tabs/three', layoutTemplate: 'tabsLayout'});
	  this.route('tabs.four', {path: '/tabs/four', layoutTemplate: 'tabsLayout'});
	  this.route('userAccounts');
	});

* https://github.com/kevingzhang/welog/blob/master/both/router.js

#### contentFor 用法
	<template name="navigation">
	  {{#contentFor "headerButtonLeft"}}
	    {{>ionNavBackButton path="index"}}
	  {{/contentFor}}
	  {{#contentFor "headerTitle"}}
	    <h1 class="title">Navigation</h1>
	  {{/contentFor}}

	  {{#ionView}}
	    {{#ionContent}}
	      <div class="padding">
	        <a href="{{pathFor 'index'}}" class="button button-stable" data-nav-direction="back">{{> ionIcon icon="ios-arrow-back"}} Back</a>
	        <a href="{{pathFor 'navigation.one'}}" class="button button-stable">{{> ionIcon icon="ios-arrow-forward"}} Forward</a>
	      </div>
	    {{/ionContent}}
	  {{/ionView}}
	</template>

* https://github.com/kevingzhang/welog/blob/master/client/templates/navigation/navigation.html

#### headerButtonLeft 出处
	<template name="ionNavBar">
	  <div class="{{classes}} nav-bar-block nav-bar-transition-{{transition}} nav-bar-direction-forward" data-navbar-container>
	    {{> yield "headerButtonLeft"}}
	    {{> yield "headerTitle"}}
	    {{> yield "headerButtonRight"}}
	  </div>
	</template>

* https://github.com/meteoric/meteor-ionic/blob/master/components/ionNavBar/ionNavBar.html

#### ionicframework
* http://ionicframework.com/
* http://ionicframework.com/docs/components/#footer
* http://ionicframework.com/docs/components/#item-thumbnails

#### welog 设计方案
* 首页进入选择用menu方案，不用tab方案
* 右上角放一个人头像，虚的表示未登录，实的表示已登录
* 点击人头像，跳出一个 actionSheet
  - http://welog.meteor.com/actionSheet
* 如果登录后，加入 Add blog 功能
  - http://welog.meteor.com/forms
* 首页显示blog的 list
  - http://welog.meteor.com/lists
* 点击post，看到 viewpost
  - http://welog.meteor.com/headersFooters

#### mongoDB 数据库设计
* title
* body
* _id
* published
* time
* comments

### Meteor.user 
* http://docs.meteor.com/#/basic/Meteor-users
* https://github.com/meteor-useraccounts/core/blob/master/Guide.md
* https://github.com/meteor-useraccounts/ionic

#### Meteor.user doc example
	{
	  _id: "bbca5d6a-2156-41c4-89da-0329e8c99a4f",  // Meteor.userId()
	  username: "cool_kid_13", // unique name
	  emails: [
	    // each email address can only belong to one user.
	    { address: "cool@example.com", verified: true },
	    { address: "another@different.com", verified: false }
	  ],
	  createdAt: Wed Aug 21 2013 15:16:52 GMT-0700 (PDT),
	  profile: {
	    // The profile is writable by the user by default.
	    name: "Joe Schmoe"
	  },
	  services: {
	    facebook: {
	      id: "709050", // facebook id
	      accessToken: "AAACCgdX7G2...AbV9AZDZD"
	    },
	    resume: {
	      loginTokens: [
	        { token: "97e8c205-c7e4-47c9-9bea-8e2ccc0694cd",
	          when: 1349761684048 }
	      ]
	    }
	  }
	}

#### userData publish and subscribe
	// server
	Meteor.publish("userData", function () {
	  if (this.userId) {
	    return Meteor.users.find({_id: this.userId},
	                             {fields: {'other': 1, 'things': 1}});
	  } else {
	    this.ready();
	  }
	});

	// client
	Meteor.subscribe("userData");

#### 添加 username 表项
	if !Meteor.users.findOne()
	  Meteor.http.post 'http://api.randomuser.me/?results=20', { dataType: 'json' }, (err, data) ->
	    err2 = undefined
	    fakeusers = undefined
	    msg = undefined
	    if !err
	      fakeusers = JSON.parse(data.content).results
	      try
	        fakeusers.forEach (user) ->
	          Meteor.users.insert user.user
	          return
	        msg = fakeusers.length + ' users added to Meteor.users'
	        console.log msg
	      catch _error
	        err2 = _error
	        console.log 'Oops! insert error' + err2
	    else
	      console.log err
	    return   

#### seeds.js
	  if (Posts.find({}).count() === 0) {
	    Posts.insert({
	      title: Fake.sentence(),
	      body: Fake.paragraph(),
	      published: Fake.fromArray([true, false])
	    });

* https://github.com/kevingzhang/welog/blob/master/server/seeds.js

#### simple-schema
* https://atmospherejs.com/aldeed/simple-schema

#### avatar
* https://github.com/bengott/meteor-avatar/blob/master/export.js

#### momentjs
* http://momentjs.com/
