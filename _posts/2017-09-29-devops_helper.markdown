---
redirect_from:
  - /opshell
---

# Opshell

This is my current pet project which is meant to help those that work with a number of AWS accounts. Always having to login to the console to find the server you want to connect to, if you need to use a bastion host, what key you need to use, etc.

This is still very early in the development phase. It has some rough edges for sure. It has been developed on a Mac, so your mileage may vary on other platforms. Currently there are no built downloads available. Once I get to a good solid base I will try and make Mac and Windows downloadables available. For now, if you have node installed, then you should be able to run/build on your own.

Primary Components: 
- Electron
- Vue
- XTerm.js
- node-pty
- Amazon SDK

#### Build Setup for Mac/Linux
``` bash
# install dependencies and native modules
./do_install.sh

# serve with hot reload at localhost:9080
npm run dev

# build electron application for production
npm run build
```

#### Build Setup for Windows

``` bash
# install dependencies
yarn

# rebuild native modules
./node_modules/.bin/electron-rebuild

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