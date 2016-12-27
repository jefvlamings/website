---
layout: post
title:  "Chrome extensions for dummies"
description: "Test"
date:   2012-04-05 16:47:14
---

I only recently started programming after following courses on [Codecademy](https://www.codecademy.com) and now I’m already building full-blown Chrome extensions. 
The first browser extension I made is [“Loop” a YouTube video playlist](https://chrome.google.com/webstore/detail/loop-by-jef-vlamings/mmnobpjdkkmlaalimhnohcklkmkohkjn) to cue your favorite YouTube videos and play them like you would on your iPod. 
It has a simple and easy to use UI that popups up once you click a button in Chrome. 
To learn how I developed this in just two weeks, keep on reading!

![Loop - A YouTube playlist for Chrome]({% asset_path loop.png %})

## Background information
Before you get started you should know that basic Javascript and HTML skills are required. 
If you need to refresh these, I strongly advise you to go to [codeyear.com](http://www.codeyear.com) and take some courses.

### Documentation
Once you got a hold on Javascript and HTML/DOM you should definitely pin the following webpages to your bookmarks because you’ll be visiting them a lot.

* [Google Chrome Extensions documentation](https://developer.chrome.com/extensions)
* [Stack Overflow – [google-chrome-extensions]](http://stackoverflow.com/questions/tagged/google-chrome-extension)
* [Google Groups – Chrome extensions](https://groups.google.com/a/chromium.org/forum/#!forum/chromium-extensions)

I found myself mostly looking for answers on Stack Overflow because I felt like Google was skipping some not so obvious steps in their official documentation.

### Types of extensions
There are 4 different kinds of user interfaces a Chrome extension can have. 
The official documentation is not so clear about all the options you have. 
But these 4 appearances are the ones you’re most likely to use.

![Different UI's for Chrome extensions]({% asset_path chrome-extensions-types.png %})

* **Browser Actions**: add an icon next to your address bar (i.e. to show a popup)
* **Page Actions**: show a little icon in the address bar
* **Desktop notifications**: show notifications on your desktop
* **Omnibox**: add functionality to your address bar with predefined keywords

In this tutorial we will focus more on browser actions. 
The Chrome extension I built is a typical example of a browser action with a popup window. 
If you want to use one of the 4 appearances you’ll have to specify it in something called the “manifest file”.

## Getting started
To build your very first Chrome extension, create a folder on your computer and call it something like “my first extension”. 
This folder will be used to store all the files necessary for your extension. 
The first file you need to create is the manifest file.

### Manifest file
The manifest file contains all the information Chrome needs to understand how your extension should work. I’ll give you a quick overview of all the elements a proper manifest file needs. First of all, open a decent text editor (I like to use Sublime Text 2 or Textwrangler) and copy-paste these lines of code.

```json
{
    "name": "The name of your extension",
    "description": "Explain what your extension does",
    "version": "1",
    "permissions": ["tabs", "http://*/*", "background"],
    "background_page": "background.html",
    "content_scripts": [{"matches": ["http://*/*"],"js": ["inject.js"]}],
    "browser_action": {"default_icon": "16x16.png","popup": "popup.html"}
}
```
Now save this file as “manifest.json” in your extension folder.

**Tip**: notice how every rule is ended with a comma except the last one! JSON objects aren’t allowed to have a trailing comma.

* **permissions**: You need to set permissions if you want to use some of the API functionality of Chrome extensions.
    * **tabs**: if you want to access tabs or detect when something changes in a tab.
    * **url**: determine which webpages you want your extension to work with (use http://*/* for all websites).
    * **background**: if you want to use a background page (clarified further down this page).
* **background_page**: specify the file that will serve as your background page.
* **content_scripts**
    * **matches**: specify for which webpages the content script should be injected.
    * **js**: specify the file that will serve as your content script.
* **browser_action**
    * **default_icon**: specify where the icon for your extension is located (must be 16px wide and 16px high) in your extension folder.
    * **popup**: specify the file that will serve as your popup page.

As you can see quite a lot of files are necessary to build a simple extension. Anyway let’s start to make a “Hello World!”-application.

### Popup.html
Most Chrome extensions use a popup window that shows up if you click on an extension icon. 
This popup browser action, as Google likes to call it, is particularly useful if you want to show information to your users **without interrupting** the browsing experience. 
There are a lot of cases where a popup is much more efficient than opening a new webpage for instance.

To show “Hello World!” to your users, create a new file called “popup.html” and add the following lines of code.
```html
<html>
  <head><title>Hello World!</title></head>
  <body>
    <p>Hello World!</p>
  </body>
</html>
```
A popup is simply displaying a local HTML-file in a dedicated window. 
The good part is that you don’t have to worry about browser compatibility since your building this extension exclusively for Chrome. 
It’s the perfect playground to experiment with some of the recently supported HTML5 tags.

Hey presto! Your first extension!
Now you should have a folder on your computer with 2 files, i.e. **“manifest.json”** and **“popup.html“**. 
That’s all it takes to create a Chrome extension.

But since we also specified other files in our manifest file we must add those files to the folder as well. 
So before you can fire up your extension, create the next dummy files, which we’ll be needing for the rest of the tutorial. 
Don’t worry about the purpose of these files yet. It will all be explained further down this page.

* **background.html**: create an empty HTML-file with the appropriate tags
* **inject.js**: create an empty Javascript file
* **16×16.png**: you need a 16 by 16px icon.

Now let’s fire it up. 
Open your Chrome browser and go to the extensions page. 
Click on the wrench icon next to the address bar and choose **Tools >> extensions**. 
Make sure “developer mode” is ticked. 
Next, click on **“Load unpacked extension”** and choose your folder in the file dialog. 
Your extension should now be loaded in your Chrome browser. 
To confirm if everything went well, check if a **new icon appeared** next to the address bar.

If you click on it you should see something like this:
![Extension Popup showing Hello World!]({% asset_path chrome-extensions-hello-world.png %})
Congratulations! You’ve just build your first Chrome extension. From now on, we’ll dive deeper into the possibilities of extensions.

## Execution environments
I think it’s about time to talk about background pages and content scripts. 
Background pages and content scripts are actually the same. 
They are both files where most of the coding happens. 
The main difference is that background pages and content scripts run in different execution environments. 
**Background pages** run in the **extension environment** and are hidden from the user, while **content scrips** run in the **webpage environment** and can affect the web page you’re visiting.

Just like me, you’re probably wondering why Google made it so complicated. 
It actually has a very important purpose, i.e. if your extension runs in a different environment you’ll never have to worry about your code interfering with the one of the webpages. 
This means you can use the same variable, function or object names as the website with absolutely no interference.

In my extension (Loop), I used three extra files of which I’ll be discussing two:

* **Background.html**. This is my background page which holds most of the code. 
All information I gather is controlled in this file.
* **Inject.js**. This is a content script I load in every YouTube page. 
It tells me all about the video I’m watching.

### Background pages

![Background pages vs browser actions]({% asset_path chrome-extensions-background.png %})

Background pages are scripts that run in the background. 
The benefits of background pages is that they are able to **communicate** with **every tab** and **every extension file** in you browser. 
It doesn’t matter how many tabs or windows you’ve opened, it can easily detect changes being made. 
On top of that background pages can **also** communicate with **browser actions** and **content scripts**. 
So they serve as the ideal negotiator between your popup, your content script and the webpages that are being viewed.

```html
<html>
  <script>
    console.log("Hello World!");
  </script>
</html>
```
A background page is nothing more than **Javascript code** being wrapped in an HTML-file. 
Make sure you use it wisely because background pages are always open. 
This means that from the moment you start Chrome, your background pages are being loaded. 
If they demand a lot of computing power or network bandwidth, you’re browsing experience could be harmed.

### Debugging
Keep in mind that background pages run in the background (strangely enough). 
If you want to see error messages or console logs you won’t find it in the standard debugging console of your browser because they’re are meant for webpages. 
Background pages run in the extension environment and thus have a **dedicated debugging console**.

![Debugging console for background.html]({% asset_path chrome-extensions-debugging-console.png %})

To activate this console, go to the extensions page and click on “background.html” listed in your extension.

**Tip.** type “chrome://settings/extensions” in your address bar or right-click your extension icon and click “manage extensions..”.

### Content scripts
In most cases you’ll want to **read the DOM** of the visited **webpages**. 
Since extensions run in a different execution environment it is **impossible for background pages or browser actions** to read DOM-elements of the webpages you’re visiting. 
Google came up with something clever called “content scipts”. 
Content scripts are **injected in the current webpage** as if they were supplied by the original website.

![Content scripts vs background pages]({% asset_path chrome-extensions-content-script.png %})

Content scripts have the **benefit** of communicating with background pages while maintaining the ability to read the DOM of the webpages you’re visiting. 
The **downside ** of using content scripts is that you can’t directly call Chrome API functions from within the content script because they’re separated from the extension environment.

So how can you pass information from a content script to a background page and vice versa if they run in different execution environments? 
Luckily there are ways to work around this with something called “message passing”.

### Message passing
Through message passing you’re able to send and receive information between **content scripts** and **background pages**. 
Message passing is done like this:

To send a request add this piece of code.

```javascript
chrome.extension.sendRequest({
  "greeting": "hello",
  "var1": "variable 1",  //string
  "var2": true           //boolean
});
```

The first variable could serve as a recognition phrase. 
That’s how I tend to use it. 
Make sure you don’t add a trailing comma to the array or your code will fail.

On the receiving end add something like this:

```javascript
chrome.extension.onRequest.addListener(function(request, sender, sendResponse) {
  if (request.greeting == "hello"){
    var1 = request.var1; // Set variable 1
    var2 = request.var2; // Set variable 2
  }
  else{
    sendResponse({});    // Stop
  }
});
```
Although this piece of code listens to all the requests that are being sent from other files in the extension, it will only store information if the variable of greeting has the string “hello” attached to it. 
It’s a simple but effective method to distinguish between different requests.

It doesn't matter if you’re in a content script or in a background page, the way messages are being passed remains the same. 
So you could put the code for the reception of a request in any of the files.

## Conclusion
I tried to give a brief overview of how Chrome extensions work and how they are being built. 
I hope this short introduction will set you off to start and build something beautiful. 
To conclude I would like to give some extra advice to beginners.

Please, take your time to build your first extension. 
You will get frustrated at one point because you’ll find yourself in situations where you’re code isn’t running like it should or the documentation is inadequate and you can’t reproduce another ones output. 
Just *keep calm* and *keep trying*. 
If nothing seems to work, just try trial-and-error and you’ll stumble upon some answers eventually. 
Also, **try to understand what you’re doing**, it will help you in the long run and you’ll benefit from it later on. 
After all making your first extension is probably more about learning than about delivering a complete product.

If you want to snoop around in the source code of my first extension, feel free to go and check it out on GitHub! 
You can find the full code base on my GitHub page.

[Get the code](https://github.com/jefvlamings/Loop)

If you still have some questions left, feel free to ask questions in the comment section below or check out one of the suggested links. 
Good luck with your first Chrome extension!