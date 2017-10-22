# AskSteem API Documentation
Welcome to the official AskSteem API Documentation! In this README you can find some basic steps for getting started, however, for full documentation visit our [wiki](https://github.com/Hoxly/asksteem-docs/wiki)

# Getting Started
Using the AskSteem Search API for basic queries is super simple. 

## Search Endpoint
The search endpoint is located at `https://api.asksteem.com/search` and has one required parameter called `q` which should be passed a keyword or phrase to search for.

For example:
`https://api.asksteem.com/search?q=steem` will search the AskSteem index for posts related to the keyword "steem" and return the results as JSON which can be easily parsed by most programming languages. 

Here is a sample response:
```json
{
	"pages": {
		"current": 1,
		"has_previous": false,
		"has_next": true
	},
	"error": false,
	"hits": 325,
	"results": [{
		"summary": "Hello, everyone!\nToday I'm releasing the AskSteem API v1.1 which brings tons of new features for developers to play with in their apps. \nWhat is AskSteem\nAskSteem is a powerful and fast search engine that indexes the steem blockchain. You can find out what AskSteem is capable of here\nWhat is the AskSteem API\nThe AskSteem API is a RESTful HTTP API that allows developers to integrate search functionality into their applications easily. To learn more about the AskSteem API v1.0 read this post.\nWhat",
		"children": 99,
		"created": "2017-08-19T21:44:33",
		"tags": ["asksteem", "steem-dev", "steem", "search", "api"],
		"permlink": "asksteem-api-v1-1-update-user-search-includes-and-sorting",
		"type": "post",
		"net_votes": 410,
		"title": "AskSteem API v1.1 Update - User Search, Includes, and Sorting",
		"author": "thekyle"
	}, {
		"summary": "Hi, Steemians! \nA popular missing feature here on steemit is the ability to quickly and easily find posts that mention you using the @username syntax. This functionality comes baked right into AskSteem, a steem search engine. I wanted to write a quick blog post showing you how easy it is the utilize this powerful capability to interact with those who are talking about you in their posts.\n\n\n1. Go to AskSteem.com\n\nTo use this service you will need to visit AskSteem\n2. Type Your Username in Quotes\n",
		"children": 85,
		"created": "2017-06-14T02:02:48",
		"tags": ["steemit", "asksteem", "steem", "steemdev", "mentions"],
		"permlink": "how-to-find-posts-that-mention-you-with-asksteem",
		"net_votes": 310,
		"title": "How to Find Posts that Mention You (with AskSteem)",
		"type": "post",
		"author": "thekyle"
	}],
	"time": 0.137
}
```

The `search` endpoint also accepts a `pg` parameter to select the page of results to return. If not provided the page will default to 1 and for any given query there is a max of 10 pages that can be returned. 

For example:
`https://api.asksteem.com/search?q=asksteem&pg=2` would return the second page of results for the term "asksteem".

Some other parameters for the search endpoint are:
* `include` - to include additional fields for each search result
* `sort_by` - to sort the search results by a specific field
* `order` - used in combination with `sort_by` to determine how the specified field should be sorted (`asc` or `desc`)
* `types` - used to specify the types of content to be included in results (`user` and/or `post`)
