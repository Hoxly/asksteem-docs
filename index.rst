.. AskSteem documentation master file, created by
   sphinx-quickstart on Sun Aug 27 21:27:19 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to AskSteem!
====================
This is the documentation for the AskSteem Search API the fastest and most powerful
way to search the blockchain.

Getting Started
===============
.. toctree::
   :maxdepth: 2

What is AskSteem
----------------

`AskSteem`_ is a powerful and fast search engine that indexes the steem
blockchain. You can find out what AskSteem is capable of `here`_

What is the AskSteem API
------------------------

The AskSteem API is a RESTful HTTP API that allows developers to
integrate search functionality into their applications easily.

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

App Filtering
-------------

While this is not a new feature of the API and was available in v1.0 and
the standard AskSteem.com interface it was not documented. To restrict
search results to a specific app use the following query syntax:
``meta.app:appname AND query goes here``

Parameters
----------

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
--------------------

We require that all applications using the API place AskSteem branding
on the search results page in a location that is immediately visible to
the user without any interaction on their part. Additionally, to ensure
reliability and uptime we request that you send between 1% and 2% of
post beneficiary rewards to the @hoxly user account if applicable to
your app.

Branding Examples
^^^^^^^^^^^^^^^^^

Here is an example of some HTML code to embed AskSteem branding:
``<a href="https://www.asksteem.com"><img src="https://cdn.hoxly.com/asksteem/attribution.png" width="100px"></a>``

Preview:

|image0|

.. |image0| image:: https://cdn.hoxly.com/asksteem/attribution.png
   :width: 100px
   :target: https://www.asksteem.com

Thank you, and happy searching!

.. _AskSteem: https://www.asksteem.com
.. _here: https://steemit.com/steemit/@thekyle/introducing-asksteem-a-steem-search-engine

Query Syntax
============

There are many different ways that you can query the AskSteem index.
I’ve created a video demonstrating each of them, but you may also read
their descriptions and examples below.
https://www.youtube.com/watch?v=gw2kGFLGmxo&t=215s ### Keyword/Phrase
Search Like many other search engines, you can search for general
phrases and terms. AskSteem will try its best to find the document that
is most relevant to your query based on our ranking algorithm. **Example
Queries:** **Tip:** Click the example to go to that query on AskSteem
```How to buy bitcoin```_ ```What is steem```_ ```Markdown tutorial```_

Exact Search
~~~~~~~~~~~~

Putting a query into quotes requests that AskSteem only returns
documents that have exactly that phrase in that order. **Example
Queries:** ```"How to buy bitcoin"```_ ```"What is steem"```_
```"Markdown tutorial"```_

Tag Search
~~~~~~~~~~

AskSteem allows you to filter posts by tag. **Example Queries:**
```tags:life```_ ```tags:steemit```_

Author Search
~~~~~~~~~~~~~

You can filter posts by the author too. **Example Queries:**
```author:thekyle```_ ```author:abit```_ ```author:steemit```_

Creation Date Search
~~~~~~~~~~~~~~~~~~~~

AskSteem provides a highly flexible and powerful date search tool for
posts. You can search by exact date or by date range. Dates must be in
the form of YYYY-MM-DD. **Example Queries:** Search for all posts posted
on June 2, 2017 ```created:2017-06-02```_ Search for all posts posted
between May 1, 2017, and May 31, 2017
```created:[2017-05-01 TO 2017-05-31]```_

Search by Number of Votes/Comments
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Similar to dates AskSteem has another set of robust tools that allow
searches based on the number of upvotes or comments a post receives.
**Example Queries:** Posts with 150 votes: ```net_votes:150```_ Posts
with between 100 and 150 votes ```net_votes:[100 TO 150]```_ Posts with
50 comments: ```children:50```_ Posts with between 40 and 50 comments:
```children:[40 TO 50]```_ Posts with more than 50 comments:
```children:>50```_ or less than 50: ```children:<50```_ this also works
with votes, less than or equal to 10 votes: ```net_votes:<=10```_

Searches with Boosts
~~~~~~~~~~~~~~~~~~~~

You can prioritize certain parts of your query with boosts. These are
indicated by placing a ``^n`` at the end of a term, where ``n`` is the
power you want to boost that part of the query to. **Example Queries:**
Give the term bitcoin a boost of two:
```I really want posts to have the term bitcoin^2 in them.```_ Give the
term mine a boost of two, and term steem a boost of three:
```How to mine^2 steem^3```_

Inclusive/Exclusive Search
~~~~~~~~~~~~~~~~~~~~~~~~~~

You can indicate whether you want documents to contain certain terms by
placing a ``+`` or a ``-`` in front of the term. **Example Queries:**
Find documents about mining but not bitcoin:
```cryptocurrency +mining -bitcoin```_

Wildcard Search
~~~~~~~~~~~~~~~

You can use the wildcard expressions of ``?`` for a single character, or
``*`` to match any number of characters. **Example Queries:** How to
mine any cryptocurrency: ```How to mine *```_
Boolean Search
~~~~~~~~~~~~~~

| AskSteem supports any combination of the previously mentioned search
  types in a single powerful query. This uses boolean values of AND, OR,
  and NOT, along with parenthesis to separate statements.
| **Example Queries:** Posts tagged with asksteem by @thekyle:
  ```tags:asksteem AND author:thekyle```_ Posts with between 50 and 100
  comments that have more than 500 upvotes and that are tagged with
  ‘bitcoin’ or have the term bitcoin in the document:
  ```(bitcoin OR tags:bitcoin) AND (net_votes:>500 AND children:(>50 AND <100))```_
  Posts created on June 2, 2017, with 100 or more upvotes but less than
  10 comments:
  ```created:2017-06-02 AND net_votes:>=100 AND children:<10```_

Developers
==========

https://www.youtube.com/watch?v=aiqasuhUPXU Because AskSteem integrates
directly into the steem blockchain it can read metadata directly from
posts and use that data when performing queries and displaying results.
We encourage developers to add AskSteem compatible metadata to their
posts so that we can show links to your application in our search
results. The full documentation can be found at
`asksteem.com/developers`_, however, in this post I will summarize the
most important tags.

+--------------+----------------+--------+
| Tag          | Description    | Exampl |
|              |                | e      |
+==============+================+========+
| domain       | The domain     | ``exam |
|              | name or web    | ple.co |
|              | address that   | m``    |
|              | your           |        |
|              | application is |        |
|              | hosted on.     |        |
+--------------+----------------+--------+
| locator      | The path to    | ``/CAT |
|              | reach the post | EGORY/ |
|              | on the domain  | @AUTHO |
|              | relative to    | R/PERM |
|              | the root.      | LINK`` |
+--------------+----------------+--------+
| protocol     | Either ‘http’  | ``http |
|              | or ‘https’ if  | s``    |
|              | not provided   |        |
|              | then http will |        |
|              | be used by     |        |
|              | default        |        |
+--------------+----------------+--------+

If none of the above metadata is provided then AskSteem will link to
steemit.com for all posts by default, however, it is assumed that the
platform creating the content will have the best interface for viewing
it, so we would rather link there.

| The ``domain`` and ``locator`` tags are required for custom linking to
  work, however, the ``protocol`` tag is optional and will default to
  http.
| \* The domain tag should be the domain name that your web-based steem
  application is hosted on and is subdomain sensitive (so if your
  hosting on www subdomain then put that). \* The locator should be the
  permalink to that particular post in your applications URL structure,
  also notice the leading forward slash, this is required.

The final URL that we point to will be generated by concatenating the
domain and locator together with the protocol at the beginning which
will be http unless otherwise specified.

Additionally, if you are building an application on the steem blockchain
and need a search API please email us at contact@asksteem.com, we are
able to query cu

.. _```tags:asksteem AND author:thekyle```: https://www.asksteem.com/search?q=tags:asksteem+AND+author:thekyle
.. _```(bitcoin OR tags:bitcoin) AND (net_votes:>500 AND children:(>50 AND <100))```: https://www.asksteem.com/search?q=%28bitcoin+OR+tags:bitcoin%29+AND+%28net_votes:%3E500+AND+children:%28%3E50+AND+%3C100%29%29
.. _```created:2017-06-02 AND net_votes:>=100 AND children:<10```: https://www.asksteem.com/search?q=created:2017-06-02+AND+net_votes:%3E%3D100+AND+children:%3C10
.. _asksteem.com/developers: https://www.asksteem.com/developers

.. _```net_votes:150```: https://www.asksteem.com/search?q=net_votes:150
.. _```net_votes:[100 TO 150]```: https://www.asksteem.com/search?q=net_votes:%5B100+TO+150%5D
.. _```children:50```: https://www.asksteem.com/search?q=children:50
.. _```children:[40 TO 50]```: https://www.asksteem.com/search?q=children:%5B40+TO+50%5D
.. _```children:>50```: https://www.asksteem.com/search?q=children:%3E50
.. _```children:<50```: https://www.asksteem.com/search?q=children:%3C50
.. _```net_votes:<=10```: https://www.asksteem.com/search?q=net_votes:%3C%3D10
.. _``I really want posts to have the term bitcoin^2 in them.``: https://www.asksteem.com/search?q=I+really+want+posts+to+have+the+term+bitcoin%5E2+in+them.
.. _``How to mine^2 steem^3``: https://www.asksteem.com/search?q=How+to+mine%5E2+steem%5E3
.. _``cryptocurrency +mining -bitcoin``: https://www.asksteem.com/search?q=cryptocurrency+%2Bmining+-bitcoin
.. _``How to mine *``: https://www.asksteem.com/search?q=How+to+mine+*
.. _```tags:asksteem AND author:thekyle```: https://www.asksteem.com/search?q=tags:asksteem+AND+author:thekyle
.. _```(bitcoin OR tags:bitcoin) AND (net_votes:>500 AND children:(>50 AND <100))```: https://www.asksteem.com/search?q=%28bitcoin+OR+tags:bitcoin%29+AND+%28net_votes:%3E500+AND+children:%28%3E50+AND+%3C100%29%29

.. _``How to buy bitcoin``: https://www.asksteem.com/search?q=How+to+buy+bitcoin
.. _``What is steem``: https://www.asksteem.com/search?q=What+is+steem
.. _``Markdown tutorial``: https://www.asksteem.com/search?q=Markdown+tutorial
.. _``"How to buy bitcoin"``: https://www.asksteem.com/search?q=%22How+to+buy+bitcoin%22
.. _``"What is steem"``: https://www.asksteem.com/search?q=%22What+is+steem%22
.. _``"Markdown tutorial"``: https://www.asksteem.com/search?q=%22Markdown+tutorial%22
.. _```tags:life```: https://www.asksteem.com/search?q=tags:life
.. _```tags:steemit```: https://www.asksteem.com/search?q=tags:steemit
.. _```author:thekyle```: https://www.asksteem.com/search?q=author:thekyle
.. _```author:abit```: https://www.asksteem.com/search?q=author:abit
.. _```author:steemit```: https://www.asksteem.com/search?q=author:steemit
.. _```created:2017-06-02```: https://www.asksteem.com/search?q=created:2017-06-02
.. _```created:[2017-05-01 TO 2017-05-31]```: https://www.asksteem.com/search?q=created:%5B2017-05-01+TO+2017-05-31%5D
.. _```net_votes:150```: https://www.asksteem.com/search?q=net_votes:150
.. _```net_votes:[100 TO 150]```: https://www.asksteem.com/search?q=net_votes:%5B100+TO+150%5D
