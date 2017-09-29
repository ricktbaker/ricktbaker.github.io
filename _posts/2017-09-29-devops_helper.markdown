---
layout:     post
title:      "DevOps Helper - Quickly work with your AWS instances"
subtitle:   "An early development project for working with AWS instances across multiple organizations"
date:       2017-09-29 13:46:00
author:     "Rick Baker"
header-img: "img/post-bg-04.jpg"
repo:       "https://github.com/ricktbaker/devops_helper"
---

# DevOps Helper

This is my current pet project which is meant to help those that work with a number of AWS accounts.   Always having to login to the console to find the server you want to connect to, if you need to use a bastion host, what key you need to use, etc.

This is still very early in the development phase.   It has some rough edges for sure.   It has been developed on a Mac, so your mileage may vary on other platforms.

It's built on electron and vue

#### Build Setup

``` bash
# install dependencies
yarn

# serve with hot reload at localhost:9080
yarn run dev

# build electron application for production
yarn run build
```


#### What is working thus far

Setup multipe organizations
<img src="http://raw.githubusercontent.com/ricktbaker/devops_helper/master/screenshots/multiple_orgs.png" />

Add your AWS access keys per Organization and region (only needs ec2.describeInstances currently)

<img src="http://raw.githubusercontent.com/ricktbaker/devops_helper/master/screenshots/access_keys.png" />

Scan for keys that are used for SSH access, and import them

<img src="http://raw.githubusercontent.com/ricktbaker/devops_helper/master/screenshots/import_keys.png" />

Easily list out instances in regions you have setup

<img src="http://raw.githubusercontent.com/ricktbaker/devops_helper/master/screenshots/instanceList.png" />

Setup a bastion host per region if you need to ssh into it first to access private ip servers behind

<img src="http://raw.githubusercontent.com/ricktbaker/devops_helper/master/screenshots/bastion_host.png" />

Easily connect via ssh to a server with the click of a button

<img src="http://raw.githubusercontent.com/ricktbaker/devops_helper/master/screenshots/ssh_connection.png" />

### What's to come

So much more.   Eventually would like to add regular server support, google cloud, etc.

Preferences, colors, styles, etc.

Ability to show more details about servers

Too much to list...