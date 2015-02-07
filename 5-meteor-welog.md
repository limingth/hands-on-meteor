
## 

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
  － http://welog.meteor.com/lists
* 点击post，看到 viewpost
  - http://welog.meteor.com/headersFooters






