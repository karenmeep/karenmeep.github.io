---
layout: post
section-type: post
title: GDPR Mastery Guide For Product Managers
category: product management
tags: [ 'product', 'management', 'gdpr', 'privacy', 'integration' ]
---

The General Data Protection Regulation (GDPR) is a European regulation that aims to unify data protection for all. Businesses that are not compliant may get sanctioned up to 4% of the annual worldwide turnover or fined of up to € 20M (the higher of the two), per infringement. If your company processes any information of EU citizens you should start paying attention.

![Photo by Dayne Topkin on Unsplash](https://karenmeep.github.io/assets/img/dayne-topkin-78982-unsplash.jpg)

TLDR; When you collect data linked to a citizen of the EU, they are entitled to know what data is kept, for what purpose, and for how long. Users are entitled to access (“Right To Access”), export (“Right to Data Portability”), change, and permanently delete (“Right To Be Forgotten”) all their data from your systems (read more here). They should be able to access their data as easily as they entered it in the first place.

Given the complexity and nuances of the regulation as well as the implications of failing to comply, this is far from an ordinary task for anyone in the company to lead, be it a Product Manager or an Engineer. But fear not, I have written a guide for you.

## Work closely with a legal team

This is where it all starts. Your organization’s legal team must understand the regulation, the product AND the tech. They will decide how to approach the regulation and to what extent.

You’ll need to master your translation skills. From one end, you should familiarize yourself with all relevant legal terms and communicate them to your colleagues who are unfamiliar with the regulation. From the other end, you’ll need to explain the product and the tech details to your legal team so they can make the tough calls.

## Research and look for inspiration

### Know Your Domain

When handling cross-system product tasks, one of your most important assets is domain knowledge. Knowing where possible pitfalls lay will save you a lot of time.

You can start by documenting anything and everything you can about user data in your system:
- Do you have users who may be EU citizens? Note that the user’s location is by no way an indication of their citizenship and therefore rights.
- Where is data stored? Is the data stored in the EU region? Make an effort to search for unknown data stores such as logs, research data sets, backups and replications, and abandoned services.
- What is the purpose of storing the data? GDPR addresses data minimization, meaning, don’t keep what you don’t need.
- Does your product store Personally Identifiable Information (PII)? (e.g. name, address, birth date, Social Security number)
- Does your product store personal data? (e.g. photos, comments, blog posts, transactions)
- What third party service providers are used? Do they store user data on their databases? Your legal team must make a decision on how to react in case third parties are not compliant.
- What are the product implications of deleting data? Are there UX adjustments that need to be made?

### Competitor Research

As you would for any other product, look into what other companies are doing. However, this may be a challenge if you’ve started working early, as all companies share a similar release deadline.

When there isn’t a live product you can look at, you should try looking for:
- Support forums: customers will post questions about the upcoming regulation and how said company will be dealing with them. (See Shopify)
- Support articles: sometimes these go public before the actual product is released to ease customers minds. (See Wix)
- Blog posts and Public Relations announcements: some companies share information on their commitment to abide by regulations (See Slack).
- Conferences, talks and panels (See SRECon)

## Decision Time

It’s now time to decide what your solution will look like. As usual, first the product aspect and then the tech and architecture. Some questions you should be asking yourself include:
- Which parts can be manual and which must be automatic?
- What does the support model look like?
- If you’re dealing with a large integration project you should also ask: Whose job is it to make sure that the full integration flow works properly?

## Kickoff

### Combined Ownership

Depending on the size of the organization, it may be very hard for you to delve into details of each product. This is why you should identify domain owners and empower them to make decisions on their own. You can do this by supplying them with clear guidelines and motivation. Work with security experts to establish security guidelines. Your company should have a policy on how to deal with data breaches and general security guidelines when handling PII.

### Guidelines

Your job is now to guide domain owners on how to implement the regulation. Let your legal team explain what the interpretation and company policy is going to be for each part of the law. This will help owners from different teams make decisions on their own.

### Communication

Use the right channel, medium and most importantly language and terminology when communicating with different personas. Developers may use Slack, while UX, PMs and support agents may use Hangouts, and upper management uses emails. Shared documents are also not a “one size fits all” solution, for example, lawyers would prefer not to use shared documents for fear they may agree to content that will later be changed.

All the above mentioned personas are needed to make this effort happen, each of them focus on a different part of the picture and bring in different views and knowledge. You’ll need to adapt and practice superb presentation and communication skills.

## Execution

### Communication

Have yourself and your team available for questions, on all communication channels, no exceptions. Edge cases will rise and some hard legal decisions will have to be made. You will need to keep translating between the legal team and whoever is on the other end.

### Keep A Paper Trail

![Photo by Maarten van den Heuvel on Unsplash](https://karenmeep.github.io/assets/img/maarten-van-den-heuvel-73123-unsplash.jpg)

Document all slides, documents and decisions made. This is a best practice for running any project, but especially important when there are regulatory related products. It will help you run your project better and later on in understanding the thought process that was made for reaching decisions.

The research you did when you started is great. Let’s recall the key elements we described there:
- Who generates and processes data.
- What data is stored: PII and Personal Data.
- Where data is stored: Both logical location (BI, logs, databases) and physical location.
- What third party service providers are used?

## Pre-Release

### Support Protocol

Work with your support agents to define a protocol for handling requests, as well as complaints and errors in the system. Establishing clear identification and verification process is critical in this case, personal data could be shared with the wrong person in case of an ill defined method. Allow your support agents ample time to practice following this protocol.

### Content

Part of being GDPR compliant is helping the people whose data you hold understand what you’re doing with it. Depending on what your legal team decides, this might mean you’ll have some support articles discussing the types of data you’re collecting and your purpose. Make sure the legal team thoroughly reviews any content that comes out, so as not to be misleading or make your company legally liable.

### Operations

The GDPR Right To Access article states that data shall be supplied in 30 days. You should think about:
- How will you know there’s a problem? Discuss monitoring and alert solutions with your dev team.
- How will problems be dealt with and in what timeframe? An escalation policy for failures in the system must be discussed in advance.

## Good Luck

Exactly what will happen when the regulation goes into effect is still speculatory. There are many interpretations to the regulation and a matching wide range of solutions being implemented as we near the deadline on May 25th, 2018. We’ll get a gradual understanding of the true implications of the regulation as audits and sanctions arise.

My hope is that this post will help you make sense of GDPR and how you can push such an effort within your organization. I believe that caring for user’s data privacy is a noble mission and that we should all be thankful that the EU is promoting a healthier, safer ecosystem. Hopefully, more countries will follow.