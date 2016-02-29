---
layout:     post
title:      Indexing dce elements in solr, used in EXT:news
summary:    This blog post describes how to index dce content elements in solr used by EXT:news
date:       2016-02-19
categories: typo3 news solr dce
---
In a recent project, the extensions *solr*, *news* & *dce* have been used. This blog post describes how relations to dce elements in a news record can be indexed.
<!--more-->

As a first requirement, please add the following static TypoScript entries:

- *Search - Index queue configuration for news (solr)*
- *Search - Index queue configuration for news with content elements (solr)*

### Add indexing userFunc

The extension *dce* saves its content in XML by using the core features of FlexForms. 
To be able to get the content into solr, a *userFunc* is reqired.

{% highlight bash %}
plugin.tx_solr.index.queue.news.fields.content.cObject {
  15 = USER
  15 {
    userFunc = GeorgRinger\NewsBlog\Hooks\Solr\DceIndexing->run
  }
}
{% endhighlight %}


### Get dce's content

By using the *FlexFormService* of the core, it is fairly simple to convert the xml structure to a useable and readable array.

Using a switch makes it easy to change the used fields per dce type.

{% highlight php %}
<?php

namespace GeorgRinger\NewsBlog\Hooks\Solr;

use TYPO3\CMS\Core\Database\DatabaseConnection;
use TYPO3\CMS\Core\Utility\GeneralUtility;
use TYPO3\CMS\Extbase\Service\FlexFormService;

class DceIndexing
{
    /**
     * @var \TYPO3\CMS\Frontend\ContentObject\ContentObjectRenderer
     */
    public $cObj;

    /** @var FlexFormService */
    protected $flexformService;

    public function __construct()
    {
        $this->flexformService = GeneralUtility::makeInstance(FlexFormService::class);
    }

    /**
     * @param mixed $content
     * @param array $conf
     * @return string
     */
    public function run($content, $conf)
    {
        $record = $this->cObj->data;

        $additionalContent = [];
        $contentElements = $this->getDatabaseConnection()->exec_SELECTgetRows(
            '*',
            'tt_content',
            'deleted=0 AND hidden = 0 AND CType LIKE "dce_%" AND tx_news_related_news=' . (int)$record['uid'],
            '',
            'sorting');

        foreach ($contentElements as $contentElement) {
            $dceContent = $this->getContentOfDce($contentElement);
            if (!empty($dceContent)) {
                $additionalContent[] = $dceContent;
            }
        }
        return implode(' ', $additionalContent);
    }


    protected function getContentOfDce(array $row)
    {
        $content = [];
        $xml = $row['pi_flexform'];
        if (empty($xml)) {
            return '';
        }

        $flexform = $this->flexformService->convertFlexFormContentToArray($xml);
        if (!empty($flexform['settings']['headline'])) {
            $content[] = $flexform['settings']['headline'];
        }

        $ctype = $this->getDceUid($row['CType']);
        switch ($ctype) {
            // Text
            case 1:
                if (!empty($flexform['settings']['txt'])) {
                    $content[] = $flexform['settings']['txt'];
                }
                break;
            default:
                // do nothing
        }

        return implode(' ', $content);
    }

    /**
     * @param string $ctype
     * @return int
     */
    protected function getDceUid($ctype)
    {
        $ctype = explode('dce_dceuid', $ctype);
        return (int)array_pop($ctype);
    }

    /**
     * @return DatabaseConnection
     */
    protected function getDatabaseConnection()
    {
        return $GLOBALS['TYPO3_DB'];
    }
}
{% endhighlight %}