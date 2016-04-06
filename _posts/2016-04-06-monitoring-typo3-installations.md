---
layout:     post
title:      Monitoring TYPO3 installations
summary:    This blog post describes the extension t3monitoring which enables you to monitor all of your clients
date:       2016-04-06
categories: typo3 monitor client
og-image:   t3monitor/index.png
---
If you got more than a dozen of clients it is important to know which extensions and which core versions are used. 
`t3monitoring` shows you all of this information and even more in a clearly arranged module.
<!--more-->

## Features

- **Used core**: This includes information about outdated and insecure versions
- **Used extensions**: This includes information about new releases (bugfix, minor, major) and insecure versions
- **Additional information**: A simple API allows to add additional information. As a first example, it is shown if the project is built by using composer or not
- All data of extensions and core are fetched automatically from typo3.org

## How does it look like

![T3monitor Overview](/assets/t3monitor/index.png)
A nice dashboard like overview shows you all the important numbers like "How many clients are using an insecure core version"

![T3monitor Search](/assets/t3monitor/client-list.png)
A search with some additional filters makes it possible to select those clients you are interested at

![T3monitor Client](/assets/t3monitor/client-single.png)
The single view of a client shows you all the data you need:

- Versions of TYPO3, Mysql and PHP
- Extensions which are not installed but available
- Extensions which are marked as insecure by the TYPO3 security team
- Extensions which got new updates

![T3monitor Extension list](/assets/t3monitor/extension-list.png)
The extension list shows you all extensions which are used in your clients. A simple search makes it easy to find those you are interested in.

![T3monitor Extension single view](/assets/t3monitor/extension-show.png)
The single view of an extension shows you all the versions, upload comments and release dates.

![T3monitor Administration](/assets/t3monitor/administration.png)
In the adminstration section you can force an import of the core, extensions or clients. As those can take a while, a call via CLI is preferred.

## Pricing

Now you know how cool this extension is, it is time to talk about $$$! 
Of course the extension is **completly free** and uses GPL2 as license but I would like to try out a different concept based on **trust**.

If you want to use this extension it would be fair to support further development and all my other open source projects:

- less then 20 clients: € 150
- less then 100 clients: € 350
- more than 100 clients: € 500

Those numbers are just a proposal for a **onetime payment**. Please get in [contact if you want to support me](mailto:georg.ringer@gmail.com)!

## Workflow

The monitoring concept requires 2 extensions. 

1) The extension `t3monitoring_client` is installed at the client and provides all information

2) The extension `t3monitoring` collects all data, processes those and displays them nicely.

### Requirements

- The **monitor** must be able to connect to all clients. TYPO3 CMS 7.6 LTS is required.
- The **client** works currently with TYPO3 CMS 4.5 - 7.6

### Installation

The installation is really easy:

1) Install the client: Get the extension from [github](https://github.com/georgringer/t3monitoring_client) (and soon from TER), install it and configure it in the Extension Manager by providing a **secret**. Also provide the IP of the monitor's server. Repeat this process for every client.

2) Install the monitor: Get the extension from [github](https://github.com/georgringer/t3monitoring) (and soon from TER) and create a new client record. Important is the domain and the secret you just created.

3) Switch to the command line and use `./typo3/cli_dispatch.phpsh extbase monitoring:importAll`. You can also create a scheduler task for that.

4) Switch to the T3monitoring module and start using it.

## Next steps

A release to the TER will follow soon. After that I would like to collect more ideas and create a realistic roadmap out of that.

## Feedback

I would be **very** happy to get any feedback about `t3monitoring`. Don't hesitate to contact me via slack, twitter, email, ...! 

*Thanks for reading!*