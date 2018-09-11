---
layout: post
status: publish
published: true
title: Redirect www to non-www
author:
  display_name: Patrick
  login: admin
  email: patrick@millermoments.net
  url: ''
author_login: admin
author_email: patrick@millermoments.net
wordpress_id: 382
wordpress_url: http://his.millermoments.net/?p=382
date: '2012-11-28 03:18:29 -0700'
date_gmt: '2012-11-28 07:18:29 -0700'
categories:
- Programming
tags:
- apache
- ".htaccess"
comments: []
---
I personally prefer the non-www domain to the www.* sub domain which evolved from the traditional web beginnings. Here is a generic .htaccess redirect from www.domain.tld to domain.tld.

{% highlight shell %}
Options +FollowSymLinks
RewriteEngine on
RewriteCond %{HTTP_HOST} ^www.(.*)$ [NC]
RewriteRule ^(.*)$ http://%1/$1 [L,R=301]
{% endhighlight %}
