---
layout:     post
title:      "Introducing sqloose"
subtitle:   "On SQL, SQL coding practices, and making life easier"
article-type: "long"
categories: []
description: "sqloose is a little bit of syntactic sugar to make SQL coding easier. I’ve added ranges and negative indices to GROUP
BY and ORDER BY clauses, and added GROUP TO and GROUP THROUGH clauses to make it even easier to write SQL queries."
tags:       ["data"]
date:       2016-10-11 12:00:00
author:     "RDJ"
header-img: "img/sqloose/Zeelandbrug.jpg"
header-img-title: "Zeelandbrug, Oosterschelde, Zierikzee, Zeeland, The Netherlands"
header-img-link: "https://www.flickr.com/photos/dennisburger/11651823573/"
header-img-author: "Dennis Burger"
header-img-author-link: "https://www.flickr.com/photos/dennisburger/"
header-img-license: "CC BY-NC-ND"
header-img-license-link: "https://creativecommons.org/licenses/by-nc-nd/2.0/"
---

[github python-sqloose]: https://github.com/oddacious/python-sqloose
[PyPi python-sqloose]: https://pypi.python.org/pypi/sqloose
[paper towns]: https://en.wikipedia.org/wiki/Fictitious_entry
[SEQUEL paper]: http://www.almaden.ibm.com/cs/people/chamberlin/sequel-1974.pdf

sqloose is a little bit of syntactic sugar to make SQL coding easier. I've added ranges and negative indices to GROUP BY
and ORDER BY clauses, and added GROUP TO and GROUP THROUGH clauses to make it even easier to write SQL queries. See my
[github][github python-sqloose] or [PyPi][PyPi python-sqloose] for the Python implementation.

# Example

Suppose your SQL implementation supports numeric column references in GROUP BY and/or ORDER BY clauses, as many do.
Column references are substitutes for the column (or alias) names, where 1 refers to the first column, 2 to the second
column, etc.

~~~~
SELECT age, race, gender, count(*) AS num FROM stats GROUP BY 1,2,3 ORDER BY 4 DESC;
~~~~

sqloose allows you to refer to the last column as -1, and the second last as -2, etc. Further, if you specify a list of
column references such as 1,2,3,4,5, these can be replaced with [1:5], or in the special case of starting from 1, simply
[:5]. Column names can also be used in the ranges. Alternatively you could use GROUP THROUGH 5 or GROUP TO 6. sqloose 
simply translates from these to the commonly-supported numeric lists.

The following are all (some of the) ways to do this in sqloose:

~~~~
SELECT age, race, gender, count(*) AS num FROM stats GROUP BY [1:3] ORDER BY -1 DESC;
SELECT age, race, gender, count(*) AS num FROM stats GROUP BY [:3] ORDER BY -1 DESC;
SELECT age, race, gender, count(*) AS num FROM stats GROUP BY [:-2] ORDER BY -1 DESC;
SELECT age, race, gender, count(*) AS num FROM stats GROUP TO -1 ORDER BY -1 DESC;
SELECT age, race, gender, count(*) AS num FROM stats GROUP TO 4 ORDER BY -1 DESC;
SELECT age, race, gender, count(*) AS num FROM stats GROUP THROUGH 3 ORDER BY -1 DESC;
~~~~

python-sqloose does not implement any form of database on the backend. It translates sqloose syntax to the equivalent
SQL syntax, which can be then fed into your database of choice. The more important design decision of which database
to use are still left up to you.

# Why

Quite a lot of my SQL queries use numeric column references, and this will make my life easier. Maybe it'll make your
life easier too.

I end up writing lots of similar, successive queries, where I change the SELECT columns and need to simultaneously change
the GROUP BY and ORDER BY indices. The front and end of my queries. A typical session may be like so:

~~~~
SELECT count(*) AS num FROM stats;
SELECT age, count(*) AS num FROM stats GROUP BY 1 ORDER BY num DESC;
SELECT age, race, count(*) AS num FROM stats GROUP BY 1,2 ORDER BY num DESC;
SELECT age, race, gender, count(*) AS num FROM stats GROUP BY 1,2,3 ORDER BY num DESC;
~~~~

Lots of unnecessary key presses or cursor motions. I
shouldn't have to modify my SQL statements in two places when I want to make one logical change. With an expressive
enough language, this becomes redundant. Enter sqloose.

~~~~
SELECT count(*) AS num FROM stats;
SELECT age, count(*) AS num FROM stats GROUP TO num ORDER BY num DESC;
SELECT age, race, count(*) AS num FROM stats GROUP TO num ORDER BY num DESC;
SELECT age, race, gender, count(*) AS num FROM stats GROUP TO num ORDER BY num DESC;
~~~~

No more accidentally forgetting to update your GROUP BY columns.

# More SQL history than I ever wanted to know

While I've long known that SQL implementations vary immensely, I've never before looked closely at the *de jure* SQL
standards. Which is probably for the best, since I'm not sure if there is a single implementation that is fully and
precisely compliant with any of *SQL-86*, *SQL-89*, *SQL-92*, *SQL:1999*, *SQL:2003*, *SQL:2006*, *SQL:2008*, or *SQL:2011*.

![Mouthful]({{ site.baseurl }}/img/sqloose/mouthful.jpg){: .center-image }

<span class="caption text-muted">That's a mouthful.</span>

<div class="citation">

<p>

<a href="https://www.flickr.com/photos/nathaninsandiego/15903936730/">Mouthful</a> from <a href="https://www.flickr.com/photos/nathaninsandiego/">Nathan Rupert</a> used under licence <a href="https://creativecommons.org/licenses/by-nc-nd/2.0/">CC BY-NC-ND</a>

</p>

</div>

I was surprised to find that the numeric syntax for GROUP BY was never standardized, and that while numeric column
references were permitted in ORDER BY as of *SQL-92*, these were stripped out in *SQL:1999* and later versions. Numeric
GROUP BY is supported by at least MySQL, PostgreSQL, and SQLite, but not by Microsoft SQL Server or Oracle.

Side note: Where in the world can I find a copy of the *SQL-86* or *SQL-89* specs? They're cited everywhere but with no
details on them, as if they are “[paper specs][paper towns]”. I have this gap between the [*SEQUEL* paper][SEQUEL paper]
from 1974 and the *SQL-92* spec (presumably released in or around 1992, but we can never be too sure). 

# A contentious issue

This research leads me to wonder why numeric columns were never standardized for GROUP BY, and why they were removed
from ORDER BY. I've hunted for opinions on them, and found a lot, generally recommending that SQL writers avoid numeric
columns because they are imprecise and unmaintainable. 

I don't disagree with that for a codebase. However, I think these opinions are narrow and ignore how SQL is used today.
The vast majority of queries I write are in some type of REPL loop, where I'm investigating data. I think this is a very
common pattern, especially among data scientists, analysts, and others who are seeking to understand their data.

# Two common uses of SQL

Most of the SQL that is written probably falls into two broad categories:

1. SQL written because it is part of a data pipeline and is the most efficient way to query data
2. SQL written temporarily, for quick data access or summarization

I do both, but because of the volume of queries for the second purpose, that is where I spend the majority of my SQL
time.

In the first class, although I use SQL, I also use a number of other mechanisms. Certainly there is no shortage of “Big
Data” design patterns that are not very SQL-like. Yet for the second type, quick data access, SQL is incredibly
persistent and dominant.

In fact, this is part of the heritage of SQL, and was recognized in the 1974 *SEQUEL* paper.

> [...] there is also a large class of users who, while they are not computer specialists, would be willing to learn to
> interact with a computer in a reasonably high-level, non-procedural query language. Examples of such users are
> accountants, engineers, architects, and urban planners. It is for this class of users that SEQUEL is intended.

I see nothing wrong with having two uses for SQL. The SQL that becomes part of my code is cleaner and more explicit than
my data discovery SQL, which is written very succinctly and needs not be shared in that format with anyone else.

We do this with other languages too. The way I write Python in the REPL is different than how I write it in organized
code. For that matter, the way I write Python as I'm developing my Jupyter notebooks is different than the way I write
it in the final versions, following refactoring phases.

We should support SQL the way it is actually used, and do what we can to make it easier for users.

# Conclusion

Less typing. Less errors. More knowledge. Faster.
