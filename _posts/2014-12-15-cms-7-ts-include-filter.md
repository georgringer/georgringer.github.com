---
layout:     post
title:      Filter list of include static entries
date:       2014-12-15
summary:    CMS 7 - Simple way to filter the include statics in the template record
categories: typo3 cms7 filter ts
og-image:   typo3-include-static-filter.gif
---

A nice improvement just got merged into the master of TYPO3 CMS! Just one line has been added but 
it makes the live of an integrator a bit easier.<!--more-->

See the animated gif below for a short impression:

![Screen capture of filtering](/assets/typo3-include-static-filter.gif)

This is not a new feature but already possible since quite a while. If you need something like that as well, 
just use the following **TCA configuration**:

	'enableMultiSelectFilterTextfield' => TRUE,
	
If you want to get to know more kind of hidden features of the TCA, please take a look at the styleguide which covers
nearly all possible options: [github.com/7elix/TYPO3.CMS.Styleguide](https://github.com/7elix/TYPO3.CMS.Styleguide)