---
layout: article
published: true
title: Github Pages PubSubHubbub Support Levels Up
date: "2014-03-16 13:30"
tags: 
  - Jekyll
  - "gh-pages"
syndicate: 
  - 
    name: Twitter
    url: "https://twitter.com/bretolius/status/445310703457415168"
  -
    name: IndieNews
    url: "http://news.indiewebcamp.com/post"
---

A pleasing detail was noticed today.  A while back, Github [updated repository webhooks](https://github.com/blog/1778-webhooks-level-up) with a ton more options, events and granularity.  This update didn't initially include page build events, but now it appears that it does.  This is great news because it means that it is way easier to enable [pubsubhubbub](http://code.google.com/p/pubsubhubbub/) (PuSH) on a [Github pages](https://help.github.com/pages/‎) built blog.

## How to enable PubSubHubbub support on Github Pages as of now:

1. Make sure you add the appropriate headers to your feed required by PuSH.
	- `<link href="https://pubsubhubbub.superfeedr.com" rel="hub"/>`
	- `<link href="http://{{ site.url }}/atom.xml" rel="self"/>`
  - You can check my feed as a reference: [atom.xml](/atom.xml)
2. Disable any other webhook events related to PuSH that you used to use for your site.
3. Add a new webhook in your repository settings on Github.  
	- I used `https://pubsubhubbub.superfeedr.com/publish?hub.mode=publish&hub.url=http://bret.io/atom.xml`
    - Switch out the URL of my atom file for yours.
  - There is also a google run example hub that is open for general use: `http://pubsubhubbub.appspot.com`
3. Select `Let me select individual events` and only check `Page build - Pages site built.`
4. Save it!  Thats it.  You now have a realtime Github pages blog feed.

Previously, one had to add a delay between the repository push event and the webhook, as was discovered through the discussion over at [ivanzuzak.info](http://ivanzuzak.info/2011/01/02/enabling-pubsubhubbub-for-github-hosted-blogs.html).

