---
layout:     post
title:      "Opshell - Quickly work with your AWS instances"
subtitle:   "An early development project for working with AWS instances across multiple organizations"
date:       2017-09-29 13:46:00
author:     "Rick Baker"
header-img: "img/post-bg-04.jpg"
repo:       "https://github.com/ricktbaker/devops_helper"
---

# Opshell

This is my current pet project which is meant to help those that work with a number of AWS accounts.   I have a ton of different AWS clients, so I am always having to login to the console to find the server I want to connect to.   Figure out what ssh key I need to use, etc.   

I've had a small bash script I've used in the past that makes things a bit easier, but it's been neglected so instead of updating it, I decided to scratch it and start over.

This is still very early in the development phase.   It has some rough edges for sure.   It has been developed on a Mac, so your mileage may vary on other platforms.

It's built on electron and vue which at this point in time I have about 1 week experience with, so there are probably many things that can be done better, cleaner, etc.   I wanted to learn the electron/vue combo and wanted to make something useful in the process.

Primary Components: 
- Electron
- Vue
- XTerm.js
- node-pty
- Amazon SDK

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

Swap out node-pty for ssh2

Preferences, colors, styles, etc.

Ability to show more details about servers

Too much to list...