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
