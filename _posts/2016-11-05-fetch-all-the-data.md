---
layout:     post
title:      "Fetch all the data"
subtitle:   "Gathering hockey data with cacheblob"
article-type: "long"
categories: ["hockey", "goalies", "data"]
description: "Some data rarely changes, such as old boxscores, while some data changes every day, such as game results, and other
data may change every time I view it, such as gamelogs for a game in progress. I want to cache my data, but with a
concept of staleness and control over data expiry."
tags:       ["hockey", "goalies", "data", "nhl"]
date:       2016-11-05 12:00:00
author:     "RDJ"
header-img: "img/noise_med.jpg"
header-img-title: "D700 noise tests"
header-img-link: "https://www.flickr.com/photos/_belial/4881763904/"
header-img-author: "Carl Jones"
header-img-author-link: "https://www.flickr.com/photos/_belial/"
header-img-license: "CC BY-NC"
header-img-license-link: "https://creativecommons.org/licenses/by-nc/2.0/"
---

[NHL 2017 projections]: {{ site.baseurl }}/nhl-projections-2017
[NHL 2017 goalies]: {{ site.baseurl }}/predicting-goalies-with-scikit-learn
[cacheblob PyPi]: https://pypi.python.org/pypi/cacheblob/0.1.0
[cacheblob github]: https://github.com/oddacious/python-cacheblob
[hockey-reference]: http://www.hockey-reference.com/
[corsica]: http://corsica.hockey/
[goalie fetcher]: https://github.com/oddacious/goalies/blob/master/fetch_data/fetch_goalies.py  

Before the start of the current NHL season, I decided to dig into making my own goalie predictions. I wrote about this
earlier, first about the [projections][NHL 2017 projections] and then in more detail on how I [modeled][NHL 2017 goalies]
the goalies in particular. Now I wanted to go into more detail on how to get the data yourself, and in particular on a
Python package that I [wrote][cacheblob github] and [released][cacheblob PyPi] to help with exactly this purpose. Peruse
the goalie fetching code [here][goalie fetcher].

# The use case

In the sports analytics ecosystem, data may flow from producers to aggregators to analysts to users. For example, hockey
data may flow from the NHL.com feeds to a website like [hockey-reference.com][hockey-reference] to a statistician like me
to a reader like you. The sources in the middle, such as the excellent [corsica.hockey][corsica], are both consumers of
data from basic sources and producers of data for fans or analysts further down the assembly line. Some of the data I pull
comes in a structured format, like NHL.com providing JSON APIs. However much of it comes in a presentation format,
designed to be read by an end user and not consumed as inputs for another data provider. Many of these sites have
aspirations of vertical integration, or are simply trying to couple the data closely with advertising, so they purposely
do not make it as easy as they could for potential competitors.

![Nerd crossing]({{ site.baseurl }}/img/cacheblob/empty_seats2.jpg){: .center-image }

<span class="caption text-muted">Competitors for the hearts and minds of the massive sports analytics community?</span>

<div class="citation">

<p>

<a href="https://www.flickr.com/photos/brookward/14154659155/">Empty Seats</a> from <a href="https://www.flickr.com/photos/brookward/">Brook Ward</a> used under licence <a href="https://creativecommons.org/licenses/by-nc/2.0/">CC BY-NC</a>

</p>

</div>

This means that I have to extract a lot of data from HTML files. That's fine. But I don't want to pull all of the HTML
pages for every change I make to the code, nor do I want to totally separate data gathering into its own process. I
don't want to update the data every time, but often I want it to update at some interval. Some data rarely changes,
such as old boxscores, while some data changes every day, such as game results, and other
data may change every time I view it, such as gamelogs for a game in progress. I want to cache my data, but with a
concept of staleness and control over data expiry.

# Enter cacheblob

cacheblob, as I describe it in its [PyPi][cacheblob PyPi] description, is a key-value interface for expiring items. You
store a key that has an associated value, with a duration for which it should live. 

In the case of hockey data, I store a URL as the key and the HTML as the value, with the expiry set to an appropriate
duration.

Here's the gist of the code that handles this:

~~~~
def fetch_page_if_needed(cache, url, duration=datetime.timedelta(days=1)):
    """Fetch a page from `url` and store it in the `cache`, unless it is already cached.

    :param cache: The cacheblob object to use for storage.
    :param url: The URL to fetch, which will be the key in the cache.
    :param duration: How long to store the value in the cache [default: 1 day].

    :returns: The page text, or None if it was not status 200.
    """
    res = cache.fetch(url)
    if res:
        return res.value

    page = requests.get(url)
    if page.status_code != 200:
        print("Error fetching page \"{0}\": {1}".format(url, page.status_code))
        return None
    else:
        cache.store(index=url, value=page.text, duration=duration)
        return page.text
~~~~

If the item does not exist or has expired, *fetch* returns None, and only then do I actually retrieve the page and *store*
it in the cache.

In the rest of my code, whenever I need to retrieve a URL, I call my function like this:

~~~~
page = fetch_page_if_needed(cache, url)
~~~~

# Where the caching happens

cacheblob itself is not a storage mechanism. Instead, it supports a number of storage patterns. If you want your data in
SQLite databases, it has you covered. MongoDB, covered. Flat files on your hard drive? Covered. Purely in-memory, for
cases where you don't want any persistent storage? I got you.

In this case I chose to use a local MongoDB instance.

~~~~
cache = Cacheblob.cache(handler="mongo", opts={"table_name": "goalie_stats_html"})
~~~~

The essential nature of cacheblob is not about storage, it's about data expiry and providing an interface to access
expiring data. So I designed it to be adaptable to different models of data storage and persistence. I (or you) can
write more of them. There are so many important design decisions on which databases vary, that I wanted none of that
debate, and certainly didn't want to commit cacheblob users to a specific choice.

Likewise, the implementation I've coded is in Python, but if there's interest in this I could easily port to R or other
languages. Essentially it's a language-agnostic concept where I didn't find an existing implementation that quite fit
my purposes.

# Explaining the goalie fetching code

There's not much to how my [goalie fetching code][goalie fetcher] works.
I fetch the per-season pages on goalies, going through the list of years. For each of those pages I fetch, I use
BeautifulSoup to parse the page and iterate through the table rows. For each table row, I look for cells (td tags)
matching the specific statistics that I want to find. 

This is not a complicated case, because hockey-reference.com structures the data in tables and clearly identifies the cells.

# Conclusion

I built cacheblob because it solved a problem that I had dealt with in myriad ugly ways over the years. It fits a
specific niche, that nothing else has quite the same purpose. Please let me know of any suggestions or ideas you have,
or any feature requests.

Enjoy!
