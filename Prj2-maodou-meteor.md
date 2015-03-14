
## Begin from meteoric/meteor-ionic

### Router
    Router.route('/groups/:_id', {
      name: 'groups.show'
    });
    
    Router.map(function() {
    //  this.route('index', {path: '/'});
      this.route('sideMenu', {path: '/'});
    });

### Templates
* lists
* sideMenu
* popover

### Path
    <template name="groups">
    {{#each groups}}
      {{> _groupItem group=this path="groups.show"}}
    {{/each}}
    </template>
        
    <template name="groupsShow">
      {{#contentFor "headerButtonLeft"}}
        {{>ionNavBackButton path="index"}}
      {{/contentFor}}
    
      {{#contentFor "headerTitle"}}
        <h1 class="title">Profile of @{{group.name}}</h1>
      {{/contentFor}}
    
      {{#ionView}}
        {{#ionContent}}
            {{#with group}}
                  <img src="http://www.churchteams.com/ct/Data/Sites/1/group.jpg" width='120px'>
                  <h2>{{name}} ({{count}}人)</h2>
                  <p>{{desc}}</p>
            {{/with}}
        {{/ionContent}}
      {{/ionView}}
    </template>

### Controllers
    AppController = RouteController.extend({
      layoutTemplate: 'layout'
    });
    
    GroupsShowController = AppController.extend({
      waitOn: function () {
        return ;//Meteor.subscribe('group', this.params._id);
      },
      data: function () {
        console.log("data returned");
        var g = {_id: this.params._id, name:'group', count:this.params._id*100, desc:''};
        return {group: g};
        /*
        return {
          group: Meteor.users.findOne({_id: this.params._id})
        }
        */
      }
    });
    
### Linkedin Login
    meteor add accounts-ui
    meteor add pauli:accounts-linkedin
    meteor add pauli:linkedin