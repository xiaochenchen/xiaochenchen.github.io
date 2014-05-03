---
layout: post
title: "[Octopress] How to setup your octopress blog on a new computer"
date: 2014-05-03 02:09:52 -0400
comments: true
categories:
- octopress
- blog
---
###What is the problem?
You are most likely to encouter some error when you try to clone your octopress repo onto a new computer and make a post.
###How to fix it?
Here is a fix to that. You need to create and link the `_deploy` directory to `master` branch.

* Clone the repo, switch to the `source` branch.
``` bash
git clone https://github.com/username/username.github.io.git
git checkout source
```
* set up the `_deploy` directory, and link it to the `master` branch
``` bash
mkdir _deploy
cd _deploy
git init
git remote add -t master -f origin https://github.com/username/username.github.io.git
```
