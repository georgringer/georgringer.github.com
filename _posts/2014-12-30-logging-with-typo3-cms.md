---
layout:     post
title:      Logging with TYPO3 CMS using monolog
date:       2014-12-30
categories: typo3 cms7 monolog log
og-image:   logging-module.png
---

**tl;dr:** The extension *logging* brings the logging framework *monolog* to TYPO3 CMS. Included is a backend module to list & filter log entries. 
<!--more-->
Logging is an important part of an application which is not only useful during the development phase but also later on 
to be able know very fast if something does go wrong.

TYPO3 CMS has a nice logging framework which is described in detail at [docs.typo3.org](http://docs.typo3.org/typo3cms/CoreApiReference/ApiOverview/Logging/Index.html). 
The code is heavily inspired by [monolog](https://github.com/Seldaek/monolog) itself. 

For me it makes more sense to bring the original code into the world of TYPO3 instead of manually backporting it. 
This is one of the goals of my extension "**logging**". You can find it [here](https://github.com/georgringer/logging).

### About monolog

[Monolog](https://github.com/Seldaek/monolog) is an awesome logging framework. The 2 main parts are Handlers and Processors.

#### Handler

Handlers are used to do something with a log entry. Most important available actions are:

* Log to files and syslog
* Send mails and alerts to slack,flowdock, hipchat, ...
* Log specific servers and networked logging using amqp, graylog, socket, ...
* Logging in development to the console of your browser
* Log to databases like redis, mongodb, couchdb, elasticsearch, ...

#### Processor

A log entry can contain more information than the message itself. Examples are:

* MemoryUsage
* Line number and file where the call came from
* Current URL

### Using monolog in TYPO3 CMS

The extension [logging](https://github.com/georgringer/logging) requires TYPO3 CMS 7.x and works currently only 
if installed with composer.

#### Features

Besides the integration of monolog you will also get:

* A custom processor to add some additional information like the user ID and the IP.
* A custom Handler to write log entries into the database of TYPO3.
* A nice backend module to list & filter the log entries

![Logging backend module](/assets/logging-module.png)

#### How to use

Please follow the [installation instructions](https://github.com/georgringer/logging). 
After the installation you can place a simple configuration in your ```AdditionalConfiguration.php``` 
file which could look like this:

{% highlight php %}
$GLOBALS['TYPO3_CONF_VARS']['MONOLOG'] = array(
	'processorConfiguration' => array(
		\GeorgRinger\Logging\Log\Monolog\Processor\Typo3Processor::class => array()
	),
	'handlerConfiguration' => array(
		'name' => 'General',
		'handlers' => array(
			\GeorgRinger\Logging\Log\Monolog\Handler\DatabaseHandler::class => array()
		)
	)
);
{% endhighlight %}

After that you are ready to go with starting logging in your classes:

{% highlight php %}
/** @var \Monolog\Logger $logger */
$logger = GeneralUtility::makeInstance(\GeorgRinger\Logging\Log\MonologManager::class)
		->getLogger(__CLASS__);

$logger->info('Some text');
{% endhighlight %}