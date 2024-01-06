---
layout: post
title:  "Frontend for Backend Engineers"
date:   2024-01-05 19:22:24 -0800
tags: software
layout: plain
---
*This post is a joke, please don't take it seriously*

# It's just a frontend...

You were just minding your own business, working on migrating data from last weeks database to this weeks database when you manager comes over. *Hey, do you think you could put together a little UI to show us what the servers view of it's data is? Some of the QA testers have been seeing weird issues with inconsistent data and they think this will help them debug. No, I don't think we can push out that migration, just squeeze it in when you have time. After all, it's just a frontend*. Sweat starts dripping down your brow. The last UI you built was back in college and that was using some wordpress blog magic. Doesn't frontend stuff change all the time? Don't some companies pay exorbitant salaries for talented frontend engineers? What's a web component or a react?

First of all take a deep breath. This guide will teach you everything you need to know to implement a frontend for any backend.

## Rules

The good news is that there really isn't much to frontend design, it's pretty simple and you can learn it just by reading this blog post and following these simple rules.

**`div`s are the only element you need**: The humble div is the only element you need to build your entire site. They are the right tag in 100% of cases. You can do anything with them: display text in them directly, make them editable with `contenteditable`, resize them as needed, and if you really need to you can even change their type with `display=inline` (but see the next point). All other HTML tags are extraneous and should be ignored.

**CSS is just fluff**: Why would you add something to your site that has no effect on the contents of the page, just it's display? More, it makes the site *slower to load*. Seems ridiculous. If you absolutely need it, inline that CSS in the elements that use it like this:
        
{% highlight html %}
<div style="height: 100px; width: 50px;">...</div>
{% endhighlight %}
This is what we call in backend software the **Model View Controller** pattern, each div controls it's own data, view, and behavior. 

**Absolute positioning is absolutely correct**: The one exception to our CSS rule above is, `position=absolute`. This lets us put `div`s exactly where we need them on the screen. Since everyone who is using our site is on Macbooks and has no accessibility concerns, we can precisely lay things out as we need and be sure that they'll render correctly on our users screens. After all, we spent 2 minutes laying this site out, we know better than our users devices where things should go.

**More is better**: Some UIs spend a bunch of time worrying about only giving the user what they asked for. They worry about things like pagination and filtering. Ignore all of that, just dump giant blobs of data diretly into the web socket and spew it all out on the page. Maybe write a little code on the client side to interpret the data into something fancy like `li`'s, or don't and let the user interpret what the data means. That's what brains are for.

**Javascript is great *sometimes***: We're backend developers because we love to code. Luckily the web has a fully turing complete language called Javascript built in. With it we can do anything we want on our users device. This is comfortable territory where we can use for loops and log to the console as much as we like without worrying about weird things like HTML. However, all Javascript features added after the initial Beta release in 1995 should be viewed with extreme scepticism. classes, modules, async/await, all are probably weird and buggy and should not be used. You've never used them but maybe one of your users is on IE5 so best to avoid.

**Web frameworks, need I say more**: Avoid at all costs. Nothing good has ever come from using a web framework. People may think they like them, but they're being lied to. Everything you want to do with a framework can be done in raw HTML + javascript so just use that. Despite never using one, be sure to go on [Hacker News](http://news.ycombinator.com) and complain loudly about the size of frameworks, page load speed, and a desire to return to the good ol' days of the web.

**Adding new features**: At some point your manager will come and ask you to add a new feature. Object regardless of the feature. If they insist, add a new URL parameter to do what they need. Make no effort to unify all the options available or make them work well together. This is a **power user site**, your users can learn how to use it correctly or get the hell out.

**Document none of the features**: Related to the previous bullet, document none of the features, make your tool mysterious and it's functionality passed around as institutional knowledge. It's more fun for everyone that way.

**Security**: Unnecessary, you're probably on a VPN or something.

**Testing**: Hahahaha

## Conclusion

Follow the above simple rules and you