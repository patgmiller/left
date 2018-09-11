---
layout: post
status: publish
published: true
title: Extending colorbox.js
author:
  display_name: Patrick
  login: admin
  email: patrick@millermoments.net
  url: ''
author_login: admin
author_email: patrick@millermoments.net
wordpress_id: 453
wordpress_url: http://his.millermoments.net/?p=453
date: '2013-05-25 03:42:29 -0600'
date_gmt: '2013-05-25 07:42:29 -0600'
categories:
- Programming
tags:
- javascript
- colorbox
- decorator
comments: []
---
## Colorbox.js
[Colorbox](http://www.jacklmoore.com/colorbox/) is a very flexible lightbox plugin for jQuery which I have used for 2 to 3 years now and found virtually no limitations to what I've wanted to do with it. I've used it for many things like simple image previews, custom image cropping, image file uploads, as well as custom product checkout processes.

<!--more-->
## Resizing Colorbox Behavior
There is one aspect that I found difficult achieve. Recently I was working with some content in colorbox which was taller than the viewable browser window and certain actions withing the colorbox content would cause it to grow. This was primarily because the client didn't want the scroll bars, understandably I also think they look a little ugly with modal windows. Colorbox has a helper method `$.colorbox.resize()` which handles resizing colorbox to fit the content within it. It has fixed and absolute positioning, with absolute being the default. The default behavior is when the method is called it also repositions the window to have the top of colorbox nicely positioned at the top of your browsers viewable area. This is exactly what my client wanted when opening colorbox, but not while the user is editing the content within colorbox.

## Extending Colorbox
I prefer not to 'hack' the source code, and if the client ever wanted to update to the latest version of the colorbox plugin, I wanted this adjustment to the behaviour to be forgiving. So I wrote a small extension to colorbox which provided the clients desired behaviour and could be toggled on off. It works really well in Firefox and IE (7, 8, + 9), and worked reasonably well in Chrome.

I believe this would be similar to a JavaScript Decorator Pattern, since it wraps the original object behavior to modify / enhance what can be done. The difference being that a Decorated object technically would get extended at runtime, where as this is more of wrapping the object to modify the behaviour and allows it to fall back to the original functionality.

{% highlight javascript %}
/*
 * Extend $.colorbox to allow fixed position during resize.
 */
$.extend($.colorbox, {
	_resize: $.colorbox.resize,
	resize: function(options) {
		var options = options || {reposition: this.settings.reposition};
		//add style to absolute position colorbox if reposition == false
		if('reposition' in options &amp;&amp; !options.reposition) {
			var $style = $('head style').last();
			//and if it doesn't already exist
			if(!RegExp(/#colorbox/).test($style.html())) {
				$('head').append(
					'<style> #colorbox { ' +
					'top: ' + parseInt($('#colorbox').css('top')) + 'px !important;' +
					'} </style>'
				);
			}
		} else {
			//remove css rule if repostioning is allowed.
			var $style = $('head style').last();
			if(RegExp(/#colorbox/).test($style.html())) {
				$style.remove();
			}
		}
		return this._resize(options);
	}
});
{% endhighlight %}
