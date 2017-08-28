.. AskSteem documentation master file, created by
   sphinx-quickstart on Sun Aug 27 21:27:19 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to AskSteem!
====================
This is the documentation for the AskSteem Search API.

Getting Started
---------------
.. toctree::
   :maxdepth: 2

Hello, everyone! Today I’m releasing the AskSteem API v1.1 which brings
tons of new features for developers to play with in their apps.

What is AskSteem
================

`AskSteem`_ is a powerful and fast search engine that indexes the steem
blockchain. You can find out what AskSteem is capable of `here`_

What is the AskSteem API
========================

The AskSteem API is a RESTful HTTP API that allows developers to
integrate search functionality into their applications easily. To learn
more about the AskSteem API v1.0 read `this post`_.

Whats New
=========

The AskSteem API v1.1 brings loads of new functionality that has been
requested by developers.

Includes
--------

You can now tell AskSteem to return specific fields for each search
result so you don’t have you query the blockchain yourself for
additional data. By default the AskSteem API returns
``title``,\ ``summary``,\ ``net_votes``,\ ``children``,\ ``permlink``,\ ``created``,
and ``tags`` fields for each result. However, you can now use the
``include`` URL parameter to include specific fields that are not
returned by default.

For example, to include the ``json_metadata`` field for each result use
the following:
``https://api.asksteem.com/search?q=asksteem&include=meta`` This will
return results that look like this:

::

   {
           "children": 89,
           "type": "post",
           "permlink": "introducing-asksteem-a-steem-search-engine",
           "meta": {
               "format": "markdown",
               "app": "steemit/0.1"
           },
           "tags": ["steemit", "steem", "asksteem", "steem-project", "steemdev"],
           "author": "thekyle",
           "summary": "\nHello, Steemians!\nOver the past month, I've been building a new search engine that indexes the steem blockchain. It's currently live at asksteem.com. The goal of AskSteem is to provide a reliable, powerful, and fast search engine that is optimized for steem. In this post, I'd like to cover some of the features that are available. \nQuery Syntax\nThere are many different ways that you can query the AskSteem index. I've created a video demonstrating each of them, but you may also read their descrip",
           "net_votes": 300,
           "created": "2017-06-03T19:07:45",
           "title": "Introducing AskSteem - A steem search engine"
       }

The include parameter can take only one value or multiple values
seperated by commas.

User Search
-----------

When the AskSteem API originally launched it only supported searching
posts on the blockchain, not users like from the regular AskSteem.com
interface. But with v1.1 developers can now tap into our user database
with the ``types`` URL parameter.

To include users and posts in search results use the following:
``https://api.asksteem.com/search?q=steem&types=post,user`` or for only
users: ``https://api.asksteem.com/search?q=steem&types=user`` The
results would look like: \`\`\` { “followers\_count”: 226, “name”:
“steem”, “rep”: 25, “created”: “2016-03-24T17:00:18”, “post\_count”: 0,
“type”: “user”,

.. _AskSteem: https://www.asksteem.com
.. _here: https://steemit.com/steemit/@thekyle/introducing-asksteem-a-steem-search-engine
.. _this post: https://steemit.com/asksteem/@thekyle/asksteem-search-api-docs

Other
==================

* :ref:`genindex`
