---
layout:     post
title:      "NBA win predictions 2019-2020"
subtitle:   "Adapting my NBA season model for 2019-20"
article-type: "long"
categories: ["basketball"]
description: "Per my annual tradition, here are NBA playoff odds generated using the model that I shared last year, the
year before, and the year before that."
tags:       ["basketball"]
date:       2019-10-20 12:00:00
author:     "RDJ"
header-img: "img/baller.jpg"
header-img-title: "Baller"
header-img-link: "https://www.flickr.com/photos/guiseiz/8045463232/"
header-img-author: "Gul Selz"
header-img-author-link: "https://www.flickr.com/photos/guiseiz/"
header-img-license: "CC BY-SA"
header-img-license-link: "https://creativecommons.org/licenses/by-sa/2.0/"
---

[Last year]: {{ site.baseurl }}/NBA-predictions-2019
[One before]: {{ site.baseurl }}/NBA-predictions-2018
[First year]: {{ site.baseurl }}/NBA-predictions-2017
[Last year retro]: {{ site.baseurl }}/NBA-wrapup-2019
[github]: https://github.com/oddacious/data/blob/master/NBA/201920/ "Github link"

Per my annual tradition, here are NBA playoff odds generated using the model that I shared [last year][Last year],
[the year before][One before], and the [year before that][first year].

At this point I only have limited faith in the model (despite decent performance last year, [out-pacing
FiveThirtyEight][Last year retro]). The baseline predictive models could be improved, which would lower the variability
in the simulations. Other forecasters are moving to more nuanced models while mine is still based on BPM.

# Gimme them predictions

Fetch the CSV from [github][github].

### Eastern Conference

| Team                | Projected Wins | 2017-18 Wins | Improvement | Playoff Probability |
|---------------------|----------------|--------------|-------------|---------------------|
| Philadelphia 76ers  | 51.7           | 51           | 0.7         | 90%                 |
| Toronto Raptors     | 51.6           | 58           | -6.4        | 89%                 |
| Boston Celtics      | 51.0           | 49           | 2.0         | 86%                 |
| Milwaukee Bucks     | 50.1           | 60           | -9.9        | 88%                 |
| Miami Heat          | 44.4           | 39           | 5.4         | 67%                 |
| Indiana Pacers      | 41.9           | 48           | -6.1        | 62%                 |
| Brooklyn Nets       | 41.8           | 42           | -0.2        | 60%                 |
| Orlando Magic       | 39.1           | 42           | -2.9        | 51%                 |
| Charlotte Hornets   | 38.1           | 39           | -0.9        | 48%                 |
| Detroit Pistons     | 38.1           | 41           | -2.9        | 47%                 |
| Washington Wizards  | 36.9           | 32           | 4.9         | 45%                 |
| Atlanta Hawks       | 30.9           | 29           | 1.9         | 22%                 |
| Chicago Bulls       | 28.7           | 22           | 6.7         | 14%                 |
| New York Knicks     | 26.2           | 17           | 9.2         | 9%                  |
| Cleveland Cavaliers | 24.7           | 19           | 5.7         | 8%                  |

### Western Conference

| Team                   | Projected Wins | 2018-19 Wins | Improvement | Playoff Probability |
|------------------------|----------------|--------------|-------------|---------------------|
| Golden State Warriors  | 55.9           | 57           | -1.1        | 91%                 |
| Houston Rockets        | 52.5           | 53           | -0.5        | 88%                 |
| Denver Nuggets         | 50.2           | 54           | -3.8        | 82%                 |
| Utah Jazz              | 50.0           | 50           | 0.0         | 79%                 |
| Los Angeles Clippers   | 47.8           | 48           | -0.2        | 74%                 |
| Portland Trail Blazers | 45.2           | 53           | -7.8        | 62%                 |
| Dallas Mavericks       | 41.4           | 33           | 8.4         | 50%                 |
| Los Angeles Lakers     | 40.6           | 37           | 3.6         | 46%                 |
| Minnesota Timberwolves | 40.1           | 36           | 4.1         | 45%                 |
| San Antonio Spurs      | 38.9           | 48           | -9.1        | 41%                 |
| New Orleans Pelicans   | 38.1           | 33           | 5.1         | 36%                 |
| Oklahoma City Thunder  | 38.0           | 49           | -11.0       | 37%                 |
| Sacramento Kings       | 34.4           | 39           | -4.6        | 25%                 |
| Phoenix Suns           | 31.6           | 19           | 12.6        | 15%                 |
| Memphis Grizzlies      | 30.0           | 33           | -3.0        | 15%                 |

# Notable results

- Interesting to see GSW as the favourite, somehow, yet again. Steph Curry is very, very good. BPM likes him - but it
  also likes Draymond, Russell, Cauley-Stein, and Looney. The model also has some preference for prior season
  performance.
- Although everyone (including my own intuition) is forecasting Milwaukee and Philly to dominate the East, the regular
  season standings might not work out that way. Toronto and Boston have a lot of talent, and Milwaukee might regress a
  little bit. BPM isn't high on any Milwaukee players other than the Giannis Antetokounmpo. They were great last
  year, but they were also healthy. Philly is a strong team, but it's a top-heavy one, which makes them vulnerable to
  injury.
- The regular season might not be as sunny as forecasted in LA. The Clippers are strong, but Paul George and Kawhi
  Leonard are not projected to play ironman minutes. The Lakers have some players on the wrong side of the ageing curve.
- Balance. Most of the league has at least an outside shot of making the playoffs or missing the playoffs. This should
  make for some exciting basketball!

# If I were a betting man...

I would hesitate to bet on this model. This year I'm shadow betting: calculating optimal bets based off of the model, so
that I can evaluate its performance after the season. I took over-under odds for win totals from one site and calculated
average expected returns, according to the simulations.

I came up with three NPV-positive **OVER** bets:

- Charlotte over 23.5 wins
- Golden State over 48.5 wins
- Washington over 26.5 wins

And four **UNDER** bets:

- Chicago under 31.5 wins
- Lakers under 51.5 wins
- Milwaukee under 57.5 wins
- San Antonio under 46.5 wins

Charlotte doesn't have many great players to work with, but 24 wins isn't a big number to reach, and they're in the
junior conference. Same goes for Washington. Washington might be more path-dependent than Charlotte, in the sense that
they have more talent to trade away if they decide to be less competitive.

I love the Spurs, but 47 wins is a lot. 58 is a lot for Milwaukee too - that would be nearly no regression to the mean,
despite losing Malcolm Brogdon.

I'm looking forward to watching this season. It's a year-long celebration of the Raptors' championship!
