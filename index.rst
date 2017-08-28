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
results would look like:

::

    {
            "followers_count": 226,
            "name": "steem",
            "rep": 25,
            "created": "2016-03-24T17:00:18",
            "post_count": 0,
            "type": "user",
            "following_count": 0
    }

User results also support the ``includes`` parameter for fetching
additional fields about users.

Sorting
-------

This new version of the API supports custom sorting of results by a
field with two new URL parameters ``sort_by`` and ``order``. The
``sort_by`` parameter takes the name of the field you would like to use
for sorting, for example, ``created`` (for creation date) or
``net_votes`` (for the number of votes). The ``order`` parameter
determines how the field is to be sorted and accepts either ``desc`` or
``asc``\ for descending and ascending respectively.

For example to sort results by most recent use the following:
``https://api.asksteem.com/search?q=steem&sort_by=created&order=desc``
To sort results by most comments use this:
``https://api.asksteem.com/search?q=steem&sort_by=children&order=desc``
The default value of ``order`` is ``desc`` so it can be left out like
below: ``https://api.asksteem.com/search?q=steem&sort_by=net_votes``

Restrict Search Results to App
------------------------------

While this is not a new feature of the API and was available in v1.0 and
the standard AskSteem.com interface it was not documented. To restrict
search results to a specific app use the following query syntax:
``meta.app:appname AND query goes here``

How to Upgrade
==============

If you used the AskSteem API v1.0 in your app then you have already been
transitioned to using this new version. The AskSteem API v1.1 is fully
backward-compatible with v1.0.

Summary
=======

Here is a table to summarize the parameters of the API.
+------------+------------------------------------------------------------+-----------+
| param      | description                                                | default   |
+============+============================================================+===========+
| q          | takes the search term to query for.                        | None      |
+------------+------------------------------------------------------------+-----------+
| pg         | takes the page number                                      | 1         |
+------------+------------------------------------------------------------+-----------+
| include    | takes a CSV list of additional fields to return            | None      |
+------------+------------------------------------------------------------+-----------+
| types      | takes a CSV list of types of items to return (post/user)   | post      |
+------------+------------------------------------------------------------+-----------+
| sort\_by   | takes a single field to be used for sorting the results    | \_score   |
+------------+------------------------------------------------------------+-----------+
| order      | takes either ``desc`` or ``asc``                           | desc      |
+------------+------------------------------------------------------------+-----------+

Required Attribution
====================

We require that all applications using the API place AskSteem branding
on the search results page in a location that is immediately visible to
the user without any interaction on their part. Additionally, to ensure
reliability and uptime we request that you send between 1% and 2% of
post beneficiary rewards to the @hoxly user account if applicable to
your app.

Branding Examples:
------------------

Here is an example of some HTML code to embed AskSteem branding:
``<a href="https://www.asksteem.com"><img src="https://cdn.hoxly.com/asksteem/attribution.png" width="100px"></a>``

Preview:
<a href="https://www.asksteem.com"><img src="https://cdn.hoxly.com/asksteem/attribution.png" width="100px"></a>

Thank you, and happy searching!

.. _AskSteem: https://www.asksteem.com
.. _here: https://steemit.com/steemit/@thekyle/introducing-asksteem-a-steem-search-engine
.. _this post: https://steemit.com/asksteem/@thekyle/asksteem-search-api-docs

Other
==================

* :ref:`genindex`
