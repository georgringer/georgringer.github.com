---
layout:     post
title:      How long does it take to add a change
summary:    Even small features might take a while to be implemeneted
date:       2016-02-19
categories: typo3 core
---
In this post I try to show why adding a simple feature may take a while and why maintaining an extension is something else than just adding some lines of code.
<!--more-->

Maintaining an extension is a hard thing as it requires makes decisions about the roadmap with every change. 
Not every feature fits into the roadmap and if it does, it still needs to be implemented. This post will show what all needs to be done to get a simple feature request done.

## What is it about?

In the ticket [73057](https://forge.typo3.org/issues/73057) someone requested to make the datetime field of EXT:news optional and his valid workaround just needed 4 lines of code.

As a first decision, I need to think if this report is valid and if it fits into the extension itself or if should be be done by another extension.

### Implementation

I decided to implement the proposed feature and this is what needs to be changed:

- Add a new setting which can be defined in the configuration section inside the extension manager
- Add a proper translation in the ``locallang.xlf`` file.
- Add a new property and getter to the ``EmConfiguration``.
- Check the new property in the TCA.
- Check the new property in a hook to stop prefilling the field
- Add a new test to the ``EmConfigurationTest``.
- Add a new test to the hook implementation.
- Test it
- Commit, push & submit the change on [gerrit](https://review.typo3.org/#/c/46768/)
- Add the property to the manual
- Write this blog post

### Summary

Just because something could be done in a couple of lines, it is not that easy when doing it properly.
