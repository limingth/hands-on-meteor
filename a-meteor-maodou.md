
## Chapter A 

### 1 Build a helloworld with meteor

#### Create a meteor app named meteor-maodou 
	limingth@gmail ~/Github/Meteor.js$ meteor create meteor-maodou
	meteor-maodou: created.                       

	To run your new app:                          
	  cd meteor-maodou                            
	  meteor                                      
	limingth@gmail ~/Github/Meteor.js$ cd meteor-maodou/
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ 

#### Test it in localhost:3000
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ meteor
	[[[[[ ~/Github/Meteor.js/meteor-maodou ]]]]]  

	=> Started proxy.                             
	=> Started MongoDB.                           
	=> Started your app.                          

	=> App running at: http://localhost:3000/

#### Deploy it in meteor-maodou.meteor.com
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ meteor deploy meteor-maodou.meteor.com
	Deploying to meteor-maodou.meteor.com.        
	Now serving at http://meteor-maodou.meteor.com
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ 

#### Create a Git repo with this project
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ git init
	Initialized empty Git repository in /Users/limingth/Github/Meteor.js/meteor-maodou/.git/
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ git status
	On branch master

	Initial commit

	Untracked files:
	  (use "git add <file>..." to include in what will be committed)

		.meteor/
		meteor-maodou.css
		meteor-maodou.html
		meteor-maodou.js

	nothing added to commit but untracked files present (use "git add" to track)

	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ cat .git/config 
	[core]
		repositoryformatversion = 0
		filemode = true
		bare = false
		logallrefupdates = true
		ignorecase = true
		precomposeunicode = true
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ 

#### Push this repo to Github
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ curl -u 'limingth' https://api.github.com/user/repos -d '{"name":"meteor-maodou" ,"description":"Meteor.js dev of maodou", "homepage":"http://meteor-maodou.meteor.com", "auto_init":true}'
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ git remote add origin https://github.com/limingth/meteor-maodou
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ cat .git/config 
	[core]
		repositoryformatversion = 0
		filemode = true
		bare = false
		logallrefupdates = true
		ignorecase = true
		precomposeunicode = true
	[remote "origin"]
		url = https://github.com/limingth/meteor-maodou
		fetch = +refs/heads/*:refs/remotes/origin/*

##### Add all new files in this new repo
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ git pull origin master
	remote: Counting objects: 3, done.
	remote: Total 3 (delta 0), reused 0 (delta 0)
	Unpacking objects: 100% (3/3), done.
	From https://github.com/limingth/meteor-maodou
	 * branch            master     -> FETCH_HEAD
	 * [new branch]      master     -> origin/master
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ git add .

##### Git Commit as initial commit
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ git commit -a -m "Initial commit of meteor-maodou"
	[master f1ddf18] Initial commit of meteor-maodou
	 10 files changed, 115 insertions(+)
	 create mode 100644 .meteor/.finished-upgraders
	 create mode 100644 .meteor/.gitignore
	 create mode 100644 .meteor/.id
	 create mode 100644 .meteor/packages
	 create mode 100644 .meteor/platforms
	 create mode 100644 .meteor/release
	 create mode 100644 .meteor/versions
	 create mode 100644 meteor-maodou.css
	 create mode 100644 meteor-maodou.html
	 create mode 100644 meteor-maodou.js
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ 

##### Git push master from origin
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ git push -u origin master
	Counting objects: 16, done.
	Delta compression using up to 2 threads.
	Compressing objects: 100% (11/11), done.
	Writing objects: 100% (15/15), 2.25 KiB | 0 bytes/s, done.
	Total 15 (delta 1), reused 0 (delta 0)
	To https://github.com/limingth/meteor-maodou
	   a6c8f9b..7d8b449  master -> master
	Branch master set up to track remote branch master from origin.

	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ cat .git/config 
	[core]
		repositoryformatversion = 0
		filemode = true
		bare = false
		logallrefupdates = true
		ignorecase = true
		precomposeunicode = true
	[remote "origin"]
		url = https://github.com/limingth/meteor-maodou
		fetch = +refs/heads/*:refs/remotes/origin/*
	[branch "master"]
		remote = origin
		merge = refs/heads/master
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ 
