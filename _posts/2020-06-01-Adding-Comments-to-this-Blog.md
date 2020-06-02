---
layout: post  
title: Adding Comments to this Blog
author: Gregory Horvath  
date: 2020-06-01
tags: blog Jekyll Github-Pages Gitalk 
---

I know that all of you have been eagerly awaiting comments on this blog to discuss the riveting topics presented here. I snuck in Google Analytics (this will be discussed in a later post), so I have the data to disprove that statement. Either way, I am writing this post to discuss how to add comments to a blog using [Gitalk](https://gitalk.github.io/). First, let me remind you that this won't be a tutorial but rather an explanation to help you along. If you need a step-by-step guide there is one right in the [Gitalk readme](https://github.com/gitalk/gitalk/blob/master/readme.md). In fact this post could easily be used in addition to the readme.

First, the value proposition. Gitalk is of value because it provides you a free and open source way to get comments on a blog. I explored a few options and many solutions were free right up until it came time to host the comments somewhere to preserve history. Gitalk addresses this issue by hosting your comments on Github Repository Issue Feed. Larger pages might prefer a more scalable solution, but for this small blog Gitalk works perfectly. The only issue I encountered with Gitalk is that the amount of English documentation is lacking, so I had to get a little creative fixing my own bugs.

As such lets go through what is going on here as you working through setting up Gitalk. First off you are going to require the Gitalk library which is essentially a JavaScript file and a Style Sheet. The simplest way is just referencing one of the two sets of links in your HTML where you want to put comments. The second option is to use their [NPM Package](https://www.npmjs.com/package/gitalk). 

Once you have the proper links setup for the JavaScript files, you will notice you are sent back to Github to register a new [OAuth Application](https://github.com/settings/applications/new). All you are doing at this step is setting up a Github application to authenticate commenters. One issue I ran into was I changed the name of my OAuth application, and I couldn't figure out why I couldn't authenticate. If you run into this, just revoke all certificates through the Github OAuth Application dashboard.

Next you'll notice instructions to add the following to your code:

```javascript
<div id="gitalk-container"></div> 

const gitalk = new Gitalk({
  clientID: 'GitHub Application Client ID',
  clientSecret: 'GitHub Application Client Secret',
  repo: 'GitHub repo',      // The repository of store comments,
  owner: 'GitHub repo owner',
  admin: ['GitHub repo owner and collaborators, only these guys can initialize github issues'],
  id: '{{ page.title }},      // Ensure uniqueness and length less than 50
  distractionFreeMode: false  // Facebook-like distraction free mode
})

gitalk.render('gitalk-container')
```
At this point the instructions were not explicit and I ran into a couple issues. First, to stick with Jekyll, I created a "Gitalk.html" under _includes and added it to my post layout file. Second, I registered a Github repository with issue tracking turned on. Once properly configured Gitalk should automatically generate a new Issue for each blog post, and new comments will appear within that issue and simultaneously on your blog. Last, you'll notice I adjusted the "id" field from what was described in the Gitalk documentation. This was something I found to work better with Jekyll, location.pathname wasn't easily converting to a name so I still to the page.title reference. Make sure you page titles are under 50 character to make it possible for Gitalk to generate issues on Github.

From here, I was able to generate this blog and get the comments field to work for each post. It took a fair amount of fiddling and trying to understand Chinese text in Google searches, but alas, it works! I suppose at this point if you run into any issues, leave me a comment!

