
## Chapter 3

### Latency Compensation
本地数据库先添加，然后通过DDP进行同步
  
#### Cookie
    Cookie:
    __utma=73549582.631407578.1418441986.1418441986.1418447713.2; 
    __utmz=73549582.1418441986.1.1.utmcsr=(direct)|utmccn=(direct)|utmcmd=(none); 
    remember_token=yeyaVfdm2kjFMNA; 
    _maodou_io_session=SkJES3hsZEdlZjR2Wlp4MWJyaWRzKdWtwaE00dTYwVXlQMTRDdC9yTS9iQUN2STZwVnJEYmw3S1N6TjFaUWc4ZGdmTHo0cklIMzNxTUFtR0ZnZVJXcTh0VjZBPT0tLUtpaVpiY25nTFZqRDhmZE01MGFvelE9PQ%3D%3D--96b7ed3542f936a867c3f988cb26b9f42d9b1c22
    Host:maodou.io
    
    Cookie:
    SINAGLOBAL=3583935862407.0884.1416863529423; 
    _ga=GA1.2.347114625.1420509196; 
    myuid=1413336560; 
    ULV=1421951988321:11:4:1:9436249409336.598.1421951988077:1420949551708; 
    UOR=test.maodou.io,weibo.com,www.lieyunwang.com; 
    YF-V5-G0=7a7738669dbd9095bf06898e71d6256d; YF-Ugrow-G0=ad83bc19c1269e709f753b172bddb094; 
    SUS=SID-2529882607-1422138997-GZ-fhks9-b22f0d12a6ad69e5e24143e90ab5e110; 
    SUE=es%3D06c7b7da5dc8013533fb751b4dbda56e%26ev%3Dv1%26es2%3D344fd58158012d57affbb6cbeb30f895%26rs0%3DAf6k2jgzHRfNbuMrA%252F29BCCiMplMbe6GQj2xtTJCuFKGCQvzgVA%252BaEuYL%252FgwN2U%252BpdExdvtGDeOSf2TguMoo%252FCV4gw%252BJGytERTobtZ8vmuJpKUZYsg%252BJ6QuZrOzcHOcCrp%252B7EyuEB6rBcH%252FO0n6rg1hhBPrgSJ%252FBHS73n%252FqA%252FDo%253D%26rv%3D0; 
    SUP=cv%3D1%26bt%3D1422138997%26et%3D1422225397%26d%3Dc909%26i%3De110%26us%3D1%26vf%3D0%26vt%3D0%26ac%3D2%26st%3D0%26uid%3D2529882607%26name%3D2372614758%2540qq.com%26nick%3D%25E6%25AF%259B%25E8%25B1%2586%25E7%25BD%2591%25E6%259D%258E%25E6%2598%258E%25E8%2580%2581%25E5%25B8%2588%26fmp%3D%26lcp%3D2012-04-19%252021%253A11%253A59; 
    SUB=_2A255wG4lDeTxGeRL6VsZ-CzKyzuIHXVatNjtrDV8PUNbvtBuLVKjkW9pXbCbTpsqQamSLfSbART4_vJ_UQ..; 
    SUBP=0033WrSXqPxfM725Ws9jqgMF55529P9D9WFKSnTAc2P7mb-.mF4kp2OE5JpX5KMt; 
    SUHB=0vJ5nbQbrC0E5r; ALF=1453674993; 
    SSOLoginState=1422138998
    Host:www.weibo.com
    
### Template
#### https://docs.meteor.com/#/full/templates_api
      
    limingth@gmail ~/Github/Meteor.js/todos$ cat lib/router.js 
    Router.configure({
      // we use the  appBody template to define the layout for the entire app
      layoutTemplate: 'appBody',
    
      // the appNotFound template is used for unknown routes and missing lists
      notFoundTemplate: 'appNotFound',
    
      // show the appLoading template whilst the subscriptions below load their data
      loadingTemplate: 'appLoading',
    
      // wait on the following subscriptions before rendering the page to ensure
      // the data it's expecting is present
      waitOn: function() {
        return [
          Meteor.subscribe('publicLists'),
          Meteor.subscribe('privateLists')
        ];
      }
    });

#### example router join
    this.route('join');
    
    imingth@gmail ~/Github/Meteor.js/todos$ find . -name auth-join.html
    ./client/templates/auth-join.html

#### meteor list
    limingth@gmail ~/Github/Meteor.js/todos$ meteor list
    accounts-password  1.0.6  Password support for accounts
    insecure           1.0.2  Allow all database writes by default
    iron:router        0.9.4* Routing specifically designed for Meteor
    less               1.0.12  The dynamic stylesheet language
    meteor-platform    1.2.1  Include a standard set of Meteor packages in your app
    
                                                  
    * New versions of these packages are available! Run 'meteor update' to try to update those packages to
      their latest versions. If your packages cannot be updated further, try typing
      `meteor add <package>@<newVersion>` to see more information.
    limingth@gmail ~/Github/Meteor.js/todos$   
      
#### Route process
    Router.map(function() {
      this.route('join');
      this.route('signin');
    
      this.route('listsShow', {
        path: '/lists/:_id',
        // subscribe to todos before the page is rendered but don't wait on the
        // subscription, we'll just render the items as they arrive
        onBeforeAction: function () {
          this.todosHandle = Meteor.subscribe('todos', this.params._id);
    
          if (this.ready()) {
            // Handle for launch screen defined in app-body.js
            dataReadyHold.release();
          }
        },
        data: function () {
          return Lists.findOne(this.params._id);
        },
        action: function () {
          this.render();
        }
      });
    
      this.route('home', {
        path: '/',
        action: function() {
          Router.go('listsShow', Lists.findOne());
        }
      });
    });
    
#### lists-Show.html
    Lists.findOne()
    Object {_id: "ZMSREPRKvTchnvwnT", name: "Meteor Principles", incompleteCount: 7}
    
    {{name}} --> List B
    
    limingth@gmail ~/Github/Meteor.js/todos$ cat client/templates/lists-show.js 
    Template.listsShow.helpers({
      editing: function() {
        return Session.get(EDITING_KEY);
      },
      
* Session 本地内存变量，例如 EDITING_KEY
* Session.get(EDITING\_KEY) 在编译时会发现“EDITING\_KEY”是一个依赖源，则会把editing加入reactive链


