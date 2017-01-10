---
layout: post
title: "10 steps to selling in the App Store"
description: "Sell in app store"
date: 2016-12-31 16:47:14
---

So you want to sell an app in die App Store?

## TL;DR
Get your contract in order well before you actually want to sell your app in the App Store.

## 1. Get a developer account
First of all, you need to be registered as a developer at Apple.
Go over to [Apple developer website](https://developer.apple.com/) and sign in with your Apple ID.
You will now have access to all the developer goodies Apple has to offer.

Quickly glance at the different sections to get an overview of all the information available.
You'll be tempted to jump right in to the developer section and start building your app.
That's great, but if your main focus is selling apps for profit, I suggest you skip this stuff for now.

Your developer account will only get you so far. 
While you have all information at hand you will still need the right tools and permissions to get an app in the App Store.
Therefor Apple requires you to enroll in the Apple Developer Program.

## 2. Enroll in Apple Developer Program ($$$)
This is the part where you have put money on the table.
Go to the [Apple developer program page](https://developer.apple.com/programs/enroll/), fill in the forms and pay 99 dollars.
Remember, this is a membership fee you'll have to pay each year.

For some of you this will seem like a large amount of money just to get your app in the App Store.
In return a real person will check your app for performance, stability, maturity and overall quality.
This lengthy process ensures most crappy apps don't make it to the App Store.

This is a good thing. Apple users expect good quality apps and are willing to pay for it.

## 3. Set up user roles in Itunes Connect
When your payment has been received, you will get access to iTunes Connect.
The name is probably a leftover from times where all apps lived in the iTunes Store.

Go to the [iTunes Connect page](https://itunesconnect.apple.com/) and login with your Apple ID.
At the time of writing there are 7 icons which lead you to the different sections of iTunes Connect.
If you're stuck in any of the processes, click 'Resources and Help'. Apple has got you covered for most of the issues.

The most important thing to do now is to set up users and roles.
Apple needs to know who to contact for different cases.
Therefor all kinds of roles within a company need to be assigned to one or more users.

If you enrolled as an individual, the easiest way to get over this step is to create a user and assign every role to yourself. 

Everything is now set up to get your contract in order.

## 4. Get your contract in order
Hang in there! You're almost done with the boring part. Just some last paperwork and you're ready to go.

In order to get paid for your app, Apple needs some more information about you.
It needs to know 3 things:
* **Contact info**: how and where to reach you
* **Bank info**: how and where to pay you
* **Tax info**: how and where to arrange taxes

Each piece of information can be filled out in forms under the section **"Agreements, Tax, and Banking"**.

For contact info and bank info this is all pretty straight forward.
The tax info on the other hand needs a bit more explanation.

You need to pay taxes one way or the other.
Since Apple is a US-based company, taxes need to be arranged with the Tax service of the United States federal government.
Therefor each company needs to fill in a US Tax form, which is provided in iTunes Connect.

If your company is based in the US and will receive payments on a US bank account, you only need to fill in the first part.
For foreign companies this is a bit more difficult. 
The US has all sorts of agreements which each country in the world on how to handle taxes.
For quite a lot of countries there is a treaty which declares no taxes need to be paid in the US, as long as they are paid in the other country.

**Tip:** Follow [this link](https://developer.apple.com/library/content/documentation/LanguagesUtilities/Conceptual/iTunesConnect_Guide/Chapters/ManagingContractsandBanking.html) if you need more information.
  
If your country has this kind of treaty with the US, most of you will need to fill out a form called "US Tax form W8BEN".
Make sure you enter all information correctly, since this is a one-time submission.
If there is something wrong with this form, changing it will take far more effort.

> Forewarned is forearmed

If every step is completed, the status of your contract will change to **pending**.
After a while, your contract will move to the section **Contracts In Effect**.
If you see this, champagne bottles can be popped, because the boring stuff will be completed and you will finally be able to just focus on your app.


## 5. Build your app
Work your magic! Building apps is what your are born for.

Just make sure you checkout the latest API's and SDK's at the developer pages.

It helps to pin down the last version of the platform you want to support.
This gives you a clear view of which SDK's you can or can't use.

The more versions you support, the more users you will reach.
On the other hand, not being able to use newer SDK's will make your app lag behind of the competition.
Make this decision wisely, because it will affect your revenue. 

## 6. Set up Provisioning Profile
While developing your app you want to test your app in a natural environment, i.e. outside a simulator.
Before you can do this you'll need a provisioning profile.
A provisioning profile is a collection of certificates, device identifiers and an App ID.
Setting up such a profile will tie you as a developer and your devices uniquely to your app.

Setting up a provisioning profile includes the process of code signing.
This step guarantees all app users that the code has not been altered or corrupted after signing.
It is important for you, Apple and your costumers to have this kind of guarantee. 

New provisioning profiles can be created in your [Apple developer account](https://developer.apple.com).
After that you can add the provisioning profile to your app in Xcode.

When everything is set up, you can test your app on any of the provisioned devices.

## 7. Create an App in iTunes Connect
After you get to test your app and made sure everything runs smoothly, you are ready to put it in the App Store.
Each app has its own page in the App store and all that information needs to be provided somewhere.
You do this in the "**My Apps**" section of iTunes Connect.

Go over to [iTunes Connect] and create a new app.

There are 2 menu items in this section.
* App information
* Pricing and Availability

The first page will allow you to customize your app's page in the App store.
The second page will allow you to set up a pricing model for your app. 

## 8. Upload to App store
Before you can publish this page, you will need to upload your app.
If you made it this far, you only have 1 obstacle to overcome.
The all-feared App review!

## 9. Submit for approval
Apple likes to have control over all the apps on there platform.
This enables them to provide a reliable experience on all of their platforms.
As discusses in chapter 2, this quality assurance is good thing for your company.

While this step is frustrating for a lot of developers, the guidelines are very clear.
If you take the time to checkout the most common mistakes, you'll find very little resistance from Apple.

Here is a very short list of things to look for:
* Don't let it crash all the time (duh)
* Follow the [design guidelines](https://developer.apple.com/design/)
* Replace all placeholder content
* Make sure the description tells exactly    what to expect from your app. Nothing less, nothing more.
* In case you are showing ads, let Apple know.
* Make sure your app adds value to the ecosystem.

**Tip:** There is only 1 real guideline: "Don't upset Apple". Don't build anything you know Apple wouldn't want on there platform. 
Anything that gives users a bad experience is a no-go.

How long it takes to review an app depends on the time of the year.
During the holidays it could take a bit longer, because of understaffed review teams.
A good estimate is provided at [appreviewtimes.com](http://appreviewtimes.com/).

When your app is approved all status lights will jump to green.
This is a reward for all the effort you've put in this everlasting quest.
Now it is time to finally make some money!

## 10. Money
Cash flows wildly

## Summary
There are few things to remember. Apple users expect good quality apps and are willing to pay good money for it.
During the whole process of developing an app, Apple wants to make sure you and your app are up to par.
They employ a lot of staff to look over this process and that is why you need to pay $99/year.

The slowest and most boring step is setting up a contract.
Make sure you start with this, since it may postpone your project if you let it wait for the very last moment.

There are a lot of good articles on the Apple developer sites. 
If your stuck at any of the above steps, there is most certainly a clear solution available.
Don't give up because having your app released in the App Store is an amazing experience!