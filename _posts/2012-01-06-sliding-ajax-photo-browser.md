---
layout: post
status: publish
published: true
title: Sliding AJAX Photo Browser
author:
  display_name: Patrick
  login: admin
  email: patrick@millermoments.net
  url: ''
author_login: admin
author_email: patrick@millermoments.net
wordpress_id: 205
wordpress_url: http://his.millermoments.net/?p=205
date: '2012-01-06 12:49:44 -0700'
date_gmt: '2012-01-06 16:49:44 -0700'
categories:
- Programming
tags:
- jquery
- ajax
comments: []
---
**Original Photo Browser**

![Buy Print Photo Browser - Basic](/uploads/2012/01/Buy-Print-Photo-Browser-Basic-300x115.png)

Above is the original photo browser for the print details page on any Instaproofs photographer website. It highlighted the previous, current, and next photo for an event category and the previous and next images were also links to the actual print details page and if clicked would result in a new page request. Very clean, simple, and effective. You could browse the prints quicker with a search or category page, which also resulted in a new page request.
<!--more-->

**Sliding AJAX Photo Browser**

![Buy Print Sliding AJAX Photo Browser](/uploads/2012/01/Buy-Print-Sliding-AJAX-Photo-Browser-300x113.png)

![Buy Print Sliding AJAX Photo Browser - Next](/uploads/2012/01/Buy-Print-Sliding-AJAX-Photo-Browser-Next1-300x113.png)

This is the updated photo browser for the print details page. Initially, the photo browser looks identical to the original version. When the page is loaded several additional print thumbnails from the event category are included in the hidden overflow. Then as you mouse over anywhere on the photo browser the previous and next buttons show up without red background and then turn red as the mouse cursor moves over each button respectively.

Clicking on either button, using JavaScript ( jQuery ), the viewing widow slides in the direction indicated and request up to two additional print thumbnails, via an AJAX call ( jQuery ), which are also links to the actual print details page shown.

**History**

This was a task from 2011 that I did for Instaproofs.com
