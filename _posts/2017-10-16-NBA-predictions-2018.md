---
layout:     post
title:      "NBA win predictions 2017-2018"
subtitle:   "Adapting my NBA season model for 2017-18"
article-type: "long"
categories: ["basketball"]
description: "Some of these teams will be much better than expected, and some will be much worse, but right now we don't know which."
tags:       ["basketball"]
date:       2017-10-16 12:00:00
author:     "RDJ"
header-img: "img/baller.jpg"
header-img-title: "Baller"
header-img-link: "https://www.flickr.com/photos/guiseiz/8045463232/"
header-img-author: "Gul Selz"
header-img-author-link: "https://www.flickr.com/photos/guiseiz/"
header-img-license: "CC BY-SA"
header-img-license-link: "https://creativecommons.org/licenses/by-sa/2.0/"
---

I realize that I'm cutting it a bit close before the season starts. The league took a week away from me relative to last
year! I've been busy, but I wanted to generated and publish playoff probabilities before the season actually starts.

# Get straight to it

Once again, these come with decimals, because *math is forever*.

### Eastern Conference

|  Team                 |  Projected Wins  |  2016-17 Wins  |  Improvement  | Playoff Probability |
|-----------------------|------------------|----------------|---------------|---------------------|
|  Boston Celtics       | 51.2             | 53             | -1.8          | 89%                 |
|  Toronto Raptors      | 49.9             | 51             | -1.1          | 87%                 |
|  Cleveland Cavaliers  | 47.9             | 51             | -3.1          | 87%                 |
|  Charlotte Hornets    | 43.7             | 36             | 7.7           | 72%                 |
|  Miami Heat           | 42.8             | 41             | 1.8           | 68%                 |
|  Washington Wizards   | 42.8             | 49             | -6.2          | 69%                 |
|  Milwaukee Bucks      | 41.3             | 42             | -0.7          | 62%                 |
|  Detroit Pistons      | 36.7             | 37             | -0.3          | 44%                 |
|  Indiana Pacers       | 36.0             | 42             | -6.0          | 42%                 |
|  Chicago Bulls        | 35.2             | 41             | -5.8          | 40%                 |
|  Atlanta Hawks        | 34.6             | 43             | -8.4          | 38%                 |
|  Orlando Magic        | 31.4             | 29             | 2.4           | 23%                 |
|  Philadelphia 76ers   | 30.7             | 28             | 2.7           | 23%                 |
|  New York Knicks      | 30.4             | 31             | -0.6          | 22%                 |
|  Brooklyn Nets        | 30.1             | 20             | 10.1          | 20%                 |


### Western Conference

|  Team                    |  Projected Wins  |  2016-17 Wins  |  Improvement  | Playoff Probability |
|--------------------------|------------------|----------------|---------------|---------------------|
|  Golden State Warriors   | 61.2             | 67             | -5.8          | 98%                 |
|  Houston Rockets         | 53.8             | 55             | -1.2          | 89%                 |
|  San Antonio Spurs       | 52.0             | 61             | -9.0          | 85%                 |
|  Oklahoma City Thunder   | 51.5             | 47             | 4.5           | 83%                 |
|  Los Angeles Clippers    | 47.7             | 51             | -3.3          | 72%                 |
|  Denver Nuggets          | 45.0             | 40             | 5.0           | 62%                 |
|  Utah Jazz               | 43.8             | 51             | -7.2          | 56%                 |
|  Minnesota Timberwolves  | 41.8             | 31             | 10.8          | 49%                 |
|  Memphis Grizzlies       | 41.1             | 43             | -1.9          | 46%                 |
|  New Orleans Pelicans    | 41.1             | 34             | 7.1           | 45%                 |
|  Portland Trail Blazers  | 38.0             | 41             | -3.0          | 33%                 |
|  Dallas Mavericks        | 35.2             | 33             | 2.2           | 25%                 |
|  Sacramento Kings        | 32.6             | 32             | 0.6           | 20%                 |
|  Los Angeles Lakers      | 30.6             | 26             | 4.6           | 12%                 |
|  Phoenix Suns            | 29.9             | 24             | 5.9           | 11%                 |

# The Method

These models are slightly different than what I used last year. I designed these models for a different project, focused
around estimating playoff probabilities given the possibility of injuries or other correlated shocks. The simulation
involves stochastically simulating player quality and minutes, so every team has a high variance around their actual
performance.

# Only 61 wins for the Warriors? Say what?!?

Yeah. That's a low number. It's much lower than I expected. I personally think there's a value to continuity. The
Warriors kept all their key players and added a couple of other handy pieces.

The model thinks the Warriors are by far the most talented team. But it considers them as a worse team than last year,
probably in large part because of how bad Nick Young's BPM has been over his career, and how many minutes he plays. If
he plays a lot, and takes any minutes away from any of Golden State's far superior players, this team might not be quite
as good. I think there is a great chance his BPM will look a lot better on the Warriors, and his minutes end up vastly
reduced from last year. The model doesn't know any of that. It also doesn't know that Steve Kerr and the Warriors can
always backtrack away from using him, and revert to their existing fantastic line-ups, if need be.

Similarly, adding Derrick Rose, combined with aging, makes the Cavaliers look a lot worse. For them I see less options.

However, Nick Young is not the only reason the model predicts the Warriors will come in under expectations.

# The West got better

After the Warriors, the Thunder and the Rockets are the next best teams in the league, by minute-weighted BPM. The
Spurs, Nuggets, and Clippers also land in the top 10. This summer Paul George, Carmelo Anthony, Jimmy Butler, and Paul
Millsap all went West, with only Gordon Hayward going the other direction. Not to mention good supporting pieces like
Patrick Patterson and P.J. Tucker, who were pried away from my Raptors.

# The model likes averages

Minimizing loss and adding in high variance to both player quality and playing time results in few outliers. Teams
aren't projected to win 70 games or 10 games, because for any given team that's (usually) unlikely. The distribution of
actual wins is always wider than the distribution of predictions should be. For example, the model sees Boston as a much
improved team, yet still conservatively predicts a drop in wins. Likewise it sees the Knicks as a highly
degraded team due to Carmelo's departure, yet still predicts a similar quantity of wins. It's not a very exciting model.

Some of these teams will be much better than expected, and some will be much worse, but right now we don't know which.
