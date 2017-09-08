---
layout:     post
title:      "Replace Apache with Nginx and PHP_FPM in AWS ElasticBeanstalk"
subtitle:   "Sample Git Repository showing how to swap out apache with nginx and php_fpm 7.1 for your AWS PHP Beanstalk application strictly by using ebextensions."
date:       2017-09-08 11:48:00
author:     "Rick Baker"
header-img: "img/post-bg-nginx.jpg"
repo:       "https://github.com/ricktbaker/beanstalk-nginx-php-fpm"
---

## Replace Apache with Nginx and PHP-FPM on AWS Beanstalk

If you find yourself wanting to use Nginx and PHP-FPM instead of apache for your AWS Beanstalk PHP App, well good for you!

This is a sample deployment with all of the .ebextensions to do so without having to make a custom AMI

## What's accomplished here?

1. We swap out PHP 7.0 with PHP 7.1 because currently the amazon linux ami only comes with PHP 7.0.
2. Install nginx and phpfpm-71
3. Stop apache and keep it from starting up again
4. Make sure nginx and phpfpm start on reboot
5. Make sure environment variables are updated on both a configuration and app deployment

## How do I use it?

You can pull down this repo, zip up the contents, making sure you include the .ebextensions directory and deploy to your
beanlstalk application.   Once the deployment has finished you should be able to hit your beanstalk ip and pull up both
the index.html and the index.php file.

## Environment variables
Environment variables are set in the /etc/nginx/fastcgi_params_env file and you can include them in your server block.
You'll see an example of this in the default.   This file will get updated with any environment variable changes on both
application and config deployments.

You can get environment variables in your php script with:

`getenv('ENV_VARIABLE_NAME)`

## Nginx and PHPFPM config changes

You'll find the base config files within the .ebextensions directory.   You can modify as needed and they will take effect
when you deploy.

## Why not create a custom AMI?

You can go this route, but then in a few months when you want to use the latest version of amazon linux you'll need to
completely recreate your custom AMI all over again.  That gets to be a pain over the course of time.   So, why not just
stick with the default AMI and handle all of your setup via .ebextensions?

## I don't understand what's happening when I deploy?

Take a look at the .ebextensions/01_setup.config file.   I've commented each step.   Things in the "commands" section
happen early in the deployment process before your actual code is setup.    Things in the "container_commands" section
happen after your deployment zip file has been expanded, but before it is moved into the final /var/app/current directory

## Why not just get rid of apache completely?
This ends up being a complete pain.   Beanstalk has many commands baked in with apache, so it just gets troublesome to
get them all.    So instead we keep apache in place but just replace the daemon file with an empty shell script, so if any
beanstalk command tries to start it up again, it won't be able to.

