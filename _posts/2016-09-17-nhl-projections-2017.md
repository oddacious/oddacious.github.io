---
layout:     post
title:      "How to be a little wrong everywhere"
subtitle:   "NHL skater and goalie projections 2016-17"
article-type: "long"
categories: ["hockey", "goalies", "data"]
description: "So there you have it, some no-holds-barred nothing-to-hide projections. Full tables are in my github link.
I'll use them as a starting point, but by no means an ending point, on my opinions and pool draft this year." 
tags:       ["hockey", "NHL", "goalies", "data"]
date:       2016-09-17 12:00:00
author:     "RDJ"
header-img: "img/nhl_pred_201617/cactus.jpg"
header-img-title: "If I was an alien, visiting Earth, I'd disguise myself as a cactus too."
header-img-link: "https://www.flickr.com/photos/_belial/5932900333/"
header-img-author: "Carl Jones"
header-img-author-link: "https://www.flickr.com/photos/_belial/"
header-img-license: "CC BY-NC-ND"
header-img-license-link: "https://creativecommons.org/licenses/by-nc-nd/2.0/"
---

[Skater projections]: https://github.com/oddacious/data/blob/master/NHL/skaters_basic_projections_201617_as_of_20160917.csv
[Goalie projections]: https://github.com/oddacious/data/blob/master/NHL/goalies_basic_projections_201617_as_of_20160917.csv
[TSN pred]: http://www.tsn.ca/crosby-no-1-in-the-top-300-projected-scorers-1.360216
[ESPN pred]: http://games.espn.com/fhl/tools/projections?display=alt
[Daily Faceoff pred]: http://www.dailyfaceoff.com/41179/dailyfaceoff-2016-17-fantasy-hockey-draft-kit-on-sale-now
[LWL pred]: http://leftwinglock.com/draftkits/index.php?r=apr05art
[Rotoworld pred]: http://www.rotoworld.com/premium/draftguide/hockey/main_page.aspx
[Models article]: {{ site.baseurl }}/hockey-pools-part-3/
[Wikipedia lasso]: https://en.wikipedia.org/wiki/Lasso_(statistics)
[Matt Cane]: https://puckplusplus.com/
[Voodoo twitter]: https://twitter.com/dataandme/status/774620848586100736
[Wikipedia MSE]: https://en.wikipedia.org/wiki/Mean_squared_error
[Wikipedia LAD]: https://en.wikipedia.org/wiki/Least_absolute_deviations
[Wikipedia Huber]: https://en.wikipedia.org/wiki/Huber_loss
[Rinne stats]: http://www.hockey-reference.com/players/r/rinnepe01.html
[Wikipedia GTB]: https://en.wikipedia.org/wiki/Gradient_boosting#Gradient_tree_boosting
[Github dir]: https://github.com/oddacious/data/tree/master/NHL

I've decided to upload my projections for NHL [skaters][Skater projections] and [goalies][Goalie projections] this year.
These are derived from basic statistical models. They cover many players and a variety of stats, but of course come with
some caveats. Mainly, they're wrong.

## Why

There aren't many sources that share NHL projections. The ones that do suffer from a few limitations:

- They often cover limited statistics, not always covering blocks, hits, or faceoffs
- They might be shared in a presentable format (e.g. a pretty website), but not parser-friendly (e.g. CSV)
- They are often opaque about their methodology. I don't know if they use models or how they arrive at their conclusions
- Many charge a fee 

Of course, mine also suffer from their own set of limitations, so I'll share a few links to others.

- [ESPN (free)][ESPN pred]
- [TSN (free)][TSN pred]
- [Daily Faceoff ($4.95)][Daily Faceoff pred]
- [Left Wing Lock ($7.99-$10.99)][LWL pred]
- [Rotoworld ($19.99)][Rotoworld pred]

I haven't evaluated any of those quantitatively, nor purchased the ones with fees (not that I think fees are unfair, $5
isn't a lot of money for someone's time). So this isn't an endorsement. But I would hope that the effort level plus
domain knowledge of those writers would result in better predictions than my lazy stats.

## Skater projections

These formed the basis of my fantasy draft last year, and the methodology is mostly unchanged from how I described it
[previously][Models article]. I use [LASSO][Wikipedia lasso] models with lags, averages, position, and recent experience. 
What this means is that any given stat prediction ends up (mostly) being a combination of last year's value for that 
player, and their career average. There's not much to it.

This is data in, data out. No manual review.

Some of the things my models will do a poor job of:

- It doesn't (directly) know about injuries
- It doesn't know about trades, of players or the players they will play with
- It doesn't know about movements up and down the depth charts
- For that matter, it doesn't know about retirement

Those are harder things to put into the model, because they require a lot of manual data creation. Not just for this
year, but imagine going back and filling out 15 years of data. Not with after the fact knowledge, but what we knew as of
September in each of those years.

Here are the top 20 players, ranking by one of the metrics I described in that earlier piece. My predictions come with
decimal precision, because round numbers are for jocks.

| name             | gp | g      | a     | hits  | blocks | ppp     | shg      | sog   | fow   |
|------------------|----|--------|-------|-------|--------|---------|----------|-------|-------|
| Brent Burns      | 81 | 24.921 | 44.27 | 109.2 | 132.02 | 25.5178 |  7.0e-01 | 294.8 |  12.2 |
| Patrice Bergeron | 77 | 26.822 | 40.16 |  73.6 |  51.93 | 21.9328 |  1.1e+00 | 242   | 960.3 |
| Claude Giroux    | 74 | 23.52  | 42.66 |  80.0 |  38.31 | 23.9544 |  9.7e-01 | 209.6 | 871.5 |
| Alex Ovechkin    | 71 | 32.857 | 34.43 | 182.7 |  34.73 | 23.7982 |  4.6e-01 | 306.5 |   0.0 |
| Jamie Benn       | 71 | 25.245 | 34.5  | 125.3 |  46.34 | 19.2462 |  7.8e-01 | 207.8 | 208.7 |
| Tyler Seguin     | 76 | 29.343 | 40.53 |  87.2 |  33.83 | 23.455  |  6.7e-01 | 268   | 402.5 |
| Sidney Crosby    | 68 | 24.786 | 43.23 |  66.2 |  33.64 | 24.231  |  5.4e-01 | 193.9 | 764   |
| Erik Karlsson    | 69 | 16.16  | 38.31 |  72.6 | 130.34 | 20.8205 |  3.3e-01 | 201.5 |   0.0 |
| Ryan O'Reilly    | 74 | 20.553 | 36.02 |  30.6 |  44.23 | 18.0807 |  1.0e+00 | 172   | 887.5 |
| Kris Letang      | 68 | 15.588 | 35.39 | 118.5 | 110.14 | 20.6859 |  2.5e-01 | 191.5 |   0.0 |
| Ryan Kesler      | 69 | 16.675 | 26.72 | 125.1 |  69.51 | 11.9275 |  8.8e-01 | 148.3 | 744.8 |
| Anze Kopitar     | 70 | 19.542 | 36.56 |  65.1 |  52.06 | 17.9106 |  8.5e-01 | 160.3 | 722.5 |
| Blake Wheeler    | 75 | 24.046 | 34.75 |  92.4 |  49.54 | 16.7632 |  8.4e-01 | 222   |  18.9 |
| Evander Kane     | 72 | 23.837 | 23.92 | 180.3 |  31.89 | 11.6929 |  9.2e-01 | 254.2 |  64.2 |
| Nazem Kadri      | 70 | 19.851 | 29.23 | 131.8 |  42.36 | 14.8053 |  6.9e-01 | 201.1 | 493.1 |
| Patrick Kane     | 71 | 28.767 | 42.29 |  42.3 |  23.43 | 26.052  |  3.1e-01 | 235.8 |  21.9 |
| Nathan MacKinnon | 73 | 22.473 | 32.68 |  59.6 |  51.52 | 17.0451 |  6.7e-01 | 225.4 | 435.6 |
| John Tavares     | 68 | 23.546 | 34.9  |  49.6 |  30.25 | 18.9998 |  5.4e-01 | 202.4 | 605.7 |
| Brandon Dubinsky | 69 | 15.315 | 25.19 | 186.5 |  40.24 | 10.7869 |  7.2e-01 | 142   | 613   |

Yeah, I didn't expect to see Dubinsky in there either. 

![Silly Dubinsky]({{ site.baseurl }}/img/nhl_pred_201617/dubinsky.jpg){: .center-image }

<span class="caption text-muted">I greatly enjoy the two facial expressions present during this groin kick</span>

<div class="citation">

<p>

<a href="https://www.flickr.com/photos/keithallison/3472604344/">00064735</a> from <a href="https://www.flickr.com/photos/keithallison/">Keith Allison</a> used under licence <a href="https://creativecommons.org/licenses/by-sa/2.0/">CC BY-SA</a>

</p>

</div>

## Goalie projections

These are a little different and a touch more complicated than my skater models. I used a slightly more thorough feature set,
 and instead of LASSO I used [gradient tree boosting][Wikipedia GTB]. I'm planning on writing a follow-up piece with
more details on that.

These stats are new. They're also infuriating. As [Matt Cane][Matt Cane] apparently said, "[Goalies are voodoo and hate statistical
analysts.][Voodoo twitter]"

I couldn't agree more.

I have an academic background in economics (I know, I know...) and I've heard the following nerdy joke a few times.

> Three econometricians went out hunting, and came across a large deer. The first econometrician fired, but missed, by a
> meter to the left. The second econometrician fired, but also missed, by a meter to the right. The third econometrician
> didn't fire, but shouted in triumph, "We got it! We got it!"

What happens when you predict something that has a lot of noise in it? You (using most 
[common][Wikipedia MSE] [loss][Wikipedia LAD] [functions][Wikipedia Huber]) end up with predictions that are highly
regressed to the league average. Because that actually makes sense. It's totally possible that Braden Holtby puts up
even better numbers next year than his Vezina year last season, but it's also totally possible that his save percentage 
and goals against average [drop 15 points and jump by 0.3, respectively][Rinne stats]. So we end up with something in between.


![Bambi]({{ site.baseurl }}/img/nhl_pred_201617/bambi.jpg){: .center-image }

<span class="caption text-muted">Bambi likes economists</span>

So in the end, we end up no extreme values in the predictions. Last year, 8 goalies got 35 or more wins. The highest in
my predictions? 34 (Braden Holtby). 8 goalies (minimum 10 games) ended up with a GAA below 2.20. Lowest in my dataset? 
2.32 (Carey Price). For save percentage, that most fluctuating of major stats, the highest I have is 0.918 (Matt Murray). 
A third of the league did better than that last year!

So while I know many goalies will put up better numbers (or worse numbers) than my extremes, for no one goalie do I
predict extreme values.

These also suffer from the same issues as the skater projections, which is probaby more damaging in the case of goalies.
The models don't know who the starters and the reserves are. They aren't constrained to make them consistent by team.
You can manually scale the wins and shut-out projections to match the number of games you expect.

Without further ado, here's 20.

| player_name       | year | p_GP   | p_W    | p_SO  | p_GAA | p_SV% |
|-------------------|------|--------|--------|-------|-------|-------|
| Braden Holtby     | 2017 | 59.697 | 33.521 | 4.542 | 2.344 | 0.914 |
| Jonathan Quick    | 2017 | 62.109 | 31.199 | 4.663 | 2.361 | 0.913 |
| Pekka Rinne       | 2017 | 58.053 | 30.868 | 4.073 | 2.46  | 0.912 |
| Marc-Andre Fleury | 2017 | 58.656 | 30.328 | 4.354 | 2.389 | 0.913 |
| Ben Bishop        | 2017 | 57.048 | 30.174 | 4.246 | 2.346 | 0.913 |
| Henrik Lundqvist  | 2017 | 56.242 | 29.904 | 3.946 | 2.46  | 0.912 |
| Corey Crawford    | 2017 | 55.906 | 29.57  | 3.669 | 2.415 | 0.912 |
| Martin Jones      | 2017 | 56.686 | 28.42  | 4.471 | 2.408 | 0.913 |
| Roberto Luongo    | 2017 | 55.108 | 27.547 | 3.71  | 2.461 | 0.913 |
| Devan Dubnyk      | 2017 | 56.89  | 27.33  | 3.419 | 2.537 | 0.915 |
| Petr Mrazek       | 2017 | 55.551 | 26.857 | 3.779 | 2.534 | 0.913 |
| Cory Schneider    | 2017 | 57.048 | 24.967 | 3.824 | 2.353 | 0.914 |
| Tuukka Rask       | 2017 | 56.393 | 24.745 | 4.19  | 2.424 | 0.915 |
| Semyon Varlamov   | 2017 | 56.301 | 24.468 | 3.383 | 2.632 | 0.915 |
| Cam Ward          | 2017 | 56.72  | 23.865 | 3.004 | 2.576 | 0.907 |
| Jake Allen        | 2017 | 48.043 | 23.797 | 3.867 | 2.442 | 0.913 |
| Craig Anderson    | 2017 | 50.236 | 22.972 | 2.973 | 2.726 | 0.91  |
| Steve Mason       | 2017 | 56.014 | 22.93  | 3.431 | 2.512 | 0.915 |
| Antti Niemi       | 2017 | 47.639 | 22.461 | 3.577 | 2.427 | 0.91  |
| John Gibson       | 2017 | 45.651 | 21.999 | 2.836 | 2.495 | 0.913 |

## Final words

So there you have it, some no-holds-barred nothing-to-hide projections. Full tables are in my [github link][Github dir].
I'll use them as a starting point, but by no means an ending point, on my opinions and pool draft this year. 

Remember, they're horribly wrong.

Enjoy!
