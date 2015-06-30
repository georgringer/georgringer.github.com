---
layout:     post
title:      Release of EXT:page_speed
summary:    TYPO3 extension page_speed to show the performance and usability score of your website.
og-image:   typo3-extension-pagespeed_insights.png
date:       2015-06-30
categories: typo3 ext page_speed
---
I am proud to present the release of a new extension called *page_speed*. It renders the results of the Google's **PageSpeed Insights** in the TYPO3 CMS backend.
<!--more-->

## What does it do

**PageSpeed Insights** is a very nice tool by Google to get feedback about the performance and usability of your website. You can try it by submitting a URL at [developers.google.com/speed/pagespeed/insights](https://developers.google.com/speed/pagespeed/insights/).

The following screenshot shows pretty good the integration of the API.

![TYPO3 CMS and PageSpeed Insights](/assets/typo3-extension-pagespeed_insights.png)

I especially like those information provided by the the service and the integration:

- Visual errors like too small fonts or too small links which are hard to click on mobile are highlighted in the screenshot.
- Multilingual description of all checks

 
### Installation

Basically all you need is:

- TYPO3 CMS 7.2+
- A google account

A demo mode can be enabled in the configuration inside the Extension Manager which will show you a static result without the need of configuring anything!

Please follow the guidelines at [github.com/georgringer/page_speed](https://github.com/georgringer/page_speed/blob/master/README.rst#installation--configuration).


### Feedback please!

If you test this extension, please provide feedback by mail, twitter, fb, ...! This helps a lot to improve further versions!

### Thanks

A big thanks to all contributors of TYPO3 CMS 7.x! It is so great to work with this foundation and it makes it so much easier to generate awesome backend modules now having bootstrap available!
