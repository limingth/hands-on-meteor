
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
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ git add .
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ git commit -a -m "Initial commit of meteor-maodou"
	[master (root-commit) 91f5980] Initial commit of meteor-maodou
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

#### Deploy it as meteor-maodou.meteor.com
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ meteor deploy meteor-maodou.meteor.com
	Deploying to meteor-maodou.meteor.com.        
	Now serving at http://meteor-maodou.meteor.com
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ 

#### Push this repo to Github
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ curl -u 'limingth' https://api.github.com/user/repos -d '{"name":"meteor-maodou" ,"description":"Meteor.js dev of maodou", "homepage":"http://maodou.meteor.com"}'
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
	limingth@gmail ~/Github/Meteor.js/meteor-maodou$ git push -u origin master
	Counting objects: 13, done.
	Delta compression using up to 2 threads.
	Compressing objects: 100% (9/9), done.
	Writing objects: 100% (13/13), 1.99 KiB | 0 bytes/s, done.
	Total 13 (delta 0), reused 0 (delta 0)
	To https://github.com/limingth/meteor-maodou
	 * [new branch]      master -> master
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
