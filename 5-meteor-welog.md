
## 

### 项目代码库
* https://github.com/kevingzhang/welog

### 代码分析

#### layout 框架
* https://github.com/kevingzhang/welog/blob/master/client/layout.html

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