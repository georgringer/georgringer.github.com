---
layout:     post
title:      Sponsoring the development of the TYPO3 extension news
date:       2015-02-25
categories: typo3 ext news
---
I am currently planning the next releases of the TYPO3 extensions "news" and looking for sponsors! If you are using this extension, please read on!
<!--more-->

## Current status

The *version 3.1.0* has been released on 2015-02-12 during the T3BOARD15 and is the first version supporting TYPO3 CMS 7 and of course 6.2 LTS.

The current status is quite ok but many things can and should be improved!

## Planned features

A lot of things should be changed in the upcoming versions to make the users and editors even happier.

### 1) Documentation

A proper documentation is crucial for any software project! The current documentation must be improved in numerous ways:

- Update to state of the art REst syntax
- Document all available features & settings
- Describe best practices


### 2) Best practice code base

The following major things need to be rewritten:

- **Namespaces:** Currently the extension is not yet based on namespaces. This feels nowadays really weird.
- **Remove Classloader hack:** To be able to let others extend EXT:news, an ugly way has been introduced which needs to be rewritten from scratch.

### 3) Improved usability for editors

The editors are very important for the CMS and its extensions. Improving the user experience 
is therefore also one goal of *TYPO3 CMS 7 LTS*. The user experience can also be improved for *EXT:news*:

- Usage of the Context Sensitive Help (CSH) in every appropriate situation.
- Improve the Administration module
- Improve the rendering of the plugin in the page module

### 4) Demo page

During the T3BOARD15 [Josef Florian Glatz](http://typo3blog.at/) and me came up with idea of a demo site showing not only 
the default features of *EXT:news* but also the usage of all snippets and examples which can be found in the documentation.


## I really need you!

As you can imagine, this is a ton of work! I try to put every love and time into this extension. 

**If you are using this extension already** and it saves you time, makes you and your customers happy, 
it would be awesome if you could support the next steps! 

**If you don't use the extension yet**, take some minutes, look into the 
[manual](http://docs.typo3.org/typo3cms/extensions/news/) and just try it! 

### How can you help?

There are multiple ways how you can help:

- Patches for code or documentation
- Send your best practice snippets
- Send me your ideas
- Money (yes of course that helps as well)

A [donation link can be found on my website](http://www.montagmorgen.at/donate.html).

If you have *any* questions, don't hesitate to contact me by [mail](mailto:georg.ringer@gmail.com) or any other channel!

*Thanks for reading!*
