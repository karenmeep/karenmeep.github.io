---
layout: post
section-type: post
title: Side Effects
category: Developer Experience
tags: [ 'product', 'SDK', 'API', 'DX', 'UX' ]
---

Two years ago I took on the role of product manager for Wix’s JavaScript SDK and web API (Hive API). One of the first decisions that I made without my boss double checking is one that haunts us till this day. 
In order to understand why what I did was so bad I’ll have to explain our ecosystem.

A Wix website is made out of 3 views: The editor, where a site is created and edited, the My Account section of the site, which is a back-office with tools for managing one’s business, and the viewer, which is accessible to the public only after saving and publishing the site. Wix's funnel always starts with the editor, where our users create the website their users will see. Up until the first save, the site technically doesn’t exist, there is no back-office and the site is inaccessible to anyone other than the owner. 
There are applications that exist in all parts of the site (they use the SDK), for example an e-Commerce application, which has the public facing store front that can be modified in the editor, and a back-office portion which lives in the My Account section of the site.

We got a request from a some applications to get the URL of the application within the My Account section of the site. They needed this URL so they could refer their users to the exact location within the back-office. Once the site is saved, getting the URL for the application within the back-office is no biggie. The question is, what value should the SDK return when the URL is requested and the site is not yet saved, when the URL does not yet exist? There are a few options:

- Return undefined.

- Return undefined, have the app register to receive a ‘save site’ event once the user actively chose to save the site, then ask for the URL again (or deliver it via the event information).

- Silently save the site with a temporary name, then return the URL. Back when this feature was requested, the ability to save the site silently and under a temporary name was not available, so this option was out of the question.

- Pop up a window asking the user to save their site, then return the URL.

Thinking back, what I should have chosen was option #2. However, I made the mistake of choosing option #4.

<pre><code>getDashboardAppUrl(function(url) {
    // do something with the URL
});
</code></pre>


Why was the choice that I made so bad?

I surprised my users. They thought they were doing one thing when in fact they were doing another. I created a bad developer experience.

Developers using the SDK quickly caught on to the fact that the function also forces the user to save the site, and abused it. They used it to create flows that badly effected our overall user experience. For the longest time, as we strive to avoid breaking changes, we had to put up with what I had put out, until we were able to support option #3.

I argue that an SDK function should do one thing and nothing else. It should have **no side effects**. The "Do One Thing and Do It Well” Unix philosophy is very helpful for big product dilemmas, but it is rarely used in our day-to-day when we design small features that make up our product. 

I argue that in the work of SDKs and APIs, functions and endpoints that have side effects should be defined as dangerous, as they are unreliable. It’s hard to rely on code that _maybe also does this other thing_, code that has unexpected side effects.


I am happy to say that a few months ago when I was approached with a similar request, I shot it down.

<hr>
