---
layout: post
section-type: post
title: Side Effects
category: Developer Experience
tags: [ 'product', 'SDK', 'API', 'DX', 'UX' ]
---

The "Do One Thing and Do It Well” Unix philosophy is known for being helpful for big product dilemmas, but it is rarely used in our day-to-day when we design the small features that make up our product. 
One of the first decisions I made as Wix's SDK product manager is one that haunts us till this day. 
In order to understand why what I did was so bad I’ll have to explain our ecosystem.

A Wix website is made out of 3 views: The editor, where a site is created and edited, the My Account section of the site, which is a back-office with tools for managing one’s business, and the viewer, which is accessible to the public only after saving and publishing the site. Wix's funnel always starts with the editor, where our users create the website their users will see. Up until the first save, the site technically doesn’t exist, there is no back-office and the site is inaccessible to anyone other than the owner. 

On top of the above views lay applications that have parts in each and every view, for example an e-Commerce application, which has the public facing store front that can be modified in the editor, and a back-office portion which lives in the My Account section of the site. These applications use our SDK to interact with the site.

We got a request from a few applications for an SDK function that returns the URL of the application within the My Account section of the site. They needed this URL so they could easily refer their users to the exact location of the app within the back-office. Once the site has been saved, getting the URL for the application within the back-office is no biggie. The question is, if the site is not yet saved (when the URL cannot be provided) what value should the SDK return? 
There are a few options:

- Return nothing (undefined).

- Return undefined, have the app register to receive a ‘save site’ event once the user actively choses to save the site, then the app can ask for the URL again (or deliver it via the event information).

- Silently save the site with a temporary name, then return the URL. Back when this feature was requested, the ability to save the site silently and under a temporary name was not available, so this option was out of the question.

- Pop up a window asking the user to save their site, then return the URL.

Thinking back, what I should have chosen was option #2. However, I made the mistake of choosing option #4, which looks like this:

<pre><code>getDashboardAppUrl(function(url) {
    // do something with the URL
});
</code></pre>


Why was the choice that I made so bad?

>"Rule of Least Surprise: In interface design, always do the least surprising thing."
>
> -- <cite>Unix Philosophy</cite>

I surprised my users. They thought they were doing one thing (getting a url) when in fact they were (also) doing another (opening a dialog for the user to save their site). I created a bad developer experience.

Developers using the SDK quickly caught on to the fact that the function also forces the user to save the site, and abused it. They used it to create flows that badly effected our overall user experience. For the longest time, as we avoided making breaking changes, we had to put up with what I had put out (until we were able to support option #3).

I argue that an SDK function should do one thing and nothing else. It should have **no side effects**. 

I argue that in the work of SDKs and APIs, functions and endpoints that have side effects should be defined as dangerous, as they are unreliable. It’s hard to rely on code that _maybe also does this other thing_.


I am happy to say that a few months ago when I was approached with a similar request, I shot it down.

<hr>
