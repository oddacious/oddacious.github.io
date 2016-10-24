---
layout:     post
title:      "NBA win predictions 2016-2017"
subtitle:   "Building new player and game-level models to project wins for every team"
article-type: "long"
categories: ["basketball"]
description: "Where will the Warriors land? Will the Heat flame out? Are the Lakers back?!?"
tags:       ["basketball"]
date:       2016-10-23 12:00:00
author:     "RDJ"
header-img: "img/baller.jpg"
header-img-title: "Baller"
header-img-link: "https://www.flickr.com/photos/guiseiz/8045463232/"
header-img-author: "Gul Selz"
header-img-author-link: "https://www.flickr.com/photos/guiseiz/"
header-img-license: "CC BY-SA"
header-img-license-link: "https://creativecommons.org/licenses/by-sa/2.0/"
---

[BPM]: http://www.basketball-reference.com/about/bpm.html
[Plausible projections]: http://nyloncalculus.com/2016/09/27/highly-plausible-win-projections-2016-2017/
[Possible projections]: http://nyloncalculus.com/2016/10/03/hopefully-possible-win-projections-2016-2017/
[Ferrigan projections]: https://twitter.com/NBAcouchside/status/784210843240062976
[Pelton MP projections]: http://apbr.org/metrics/viewtopic.php?f=2&t=9211
[Win Shares]: http://www.basketball-reference.com/about/ws.html
[BR player advanced]: http://www.basketball-reference.com/leagues/NBA_2016_advanced.html
[SRS]: http://www.pro-football-reference.com/blog/index4837.html?p=37
[RAPM]: http://apbr.org/metrics/viewtopic.php?f=2&t=8964
[Miami stats]: http://www.basketball-reference.com/teams/MIA/2016.html#advanced::none

I wanted to make sure I get my NBA predictions out there before the season starts. Once again I am foolishly discarding
my mantra as an economist to only attempt to predict the past. It's all from new shiny models.

# Get straight to it

As usual, these come with decimals, because *math*.

### Eastern Conference

| Team                | Projected Wins | Projected Losses | 2015-16 Wins | Improvement |
|---------------------|----------------|------------------|--------------|-------------|
| Cleveland Cavaliers | 55.9           | 26.1             | 57           | -1.1        |
| Toronto Raptors     | 50.2           | 31.8             | 56           | -5.8        |
| Boston Celtics      | 50.0           | 32.0             | 48           | 2.0         |
| Atlanta Hawks       | 46.7           | 35.3             | 48           | -1.3        |
| Charlotte Hornets   | 44.3           | 37.7             | 48           | -3.7        |
| Detroit Pistons     | 39.6           | 42.4             | 44           | -4.4        |
| New York Knicks     | 40.4           | 41.6             | 32           | 8.4         |
| Chicago Bulls       | 39.5           | 42.5             | 42           | -2.5        |
| Indiana Pacers      | 39.0           | 43.0             | 45           | -6.0        |
| Washington Wizards  | 37.6           | 44.4             | 41           | -3.4        |
| Miami Heat          | 35.8           | 46.2             | 48           | -12.2       |
| Orlando Magic       | 35.1           | 46.9             | 35           | 0.1         |
| Milwaukee Bucks     | 32.3           | 49.7             | 33           | -0.7        |
| Philadelphia 76ers  | 22.4           | 59.6             | 10           | 12.4        |
| Brooklyn Nets       | 27.5           | 54.5             | 21           | 6.5         |

### Western Conference

| Team                   | Projected Wins | Projected Losses | 2015-16 Wins | Improvement |
|------------------------|----------------|------------------|--------------|-------------|
| Golden State Warriors  | 64.9           | 17.1             | 73           | -8.1        |
| San Antonio Spurs      | 64.4           | 17.6             | 67           | -2.6        |
| Oklahoma City Thunder  | 55.5           | 26.5             | 55           | 0.5         |
| Los Angeles Clippers   | 49.2           | 32.8             | 53           | -3.8        |
| Utah Jazz              | 45.9           | 36.1             | 40           | 5.9         |
| Houston Rockets        | 44.8           | 37.2             | 41           | 3.8         |
| Portland Trail Blazers | 45.1           | 36.9             | 44           | 1.1         |
| Denver Nuggets         | 41.9           | 40.1             | 33           | 8.9         |
| Memphis Grizzlies      | 40.9           | 41.1             | 42           | -1.1        |
| Minnesota Timberwolves | 39.6           | 42.4             | 29           | 10.6        |
| Dallas Mavericks       | 39.8           | 42.2             | 42           | -2.2        |
| Sacramento Kings       | 31.9           | 50.1             | 33           | -1.1        |
| Phoenix Suns           | 26.1           | 55.9             | 23           | 3.1         |
| New Orleans Pelicans   | 23.0           | 59.0             | 30           | -7.0        |
| Los Angeles Lakers     | 20.5           | 61.5             | 17           | 3.5         |

# The Method

Feel free to skip this and scroll below if you're more entertained by some points to debate me on.

For every player, I predict their [Box Plus-Minus (BPM)][BPM] and minutes played (MP) for the upcoming season. My
models seem quite effective at predicting these, and my MP predictions align fairly nicely against [Kevin
Pelton's][Pelton MP projections]. I then calculate team BPM by putting those together by team, and adjusting such
that each team has the same aggregate MP. This is predicted team quality. I used BPM because
[BR][BR player advanced] has it, and it was working better for me than [Win Shares][Win Shares] or VORP, without
any quality loss by cutting the others out.

This composite expected team quality becomes a leading input for my game-level model, alongside who the home team is,
the [SRS][SRS] of those teams last season, the amount of rest each team has, and the age of the teams. All three models
use stochastic gradient boosting.

It seems like other people wouldn't have the lagged team term (SRS) in there, when they're already predicting player
quality and player minutes. Likewise, age is a predictor of player BPM and thus team BPM. Why also have these on top? I
expect both have to do with imperfect models. I cannot perfectly predict BPM, and even if I could, BPM is not a perfect
predictor of team success. Likewise my MP predictions won't be perfect either, especially since I predict it
independently of the other players on the same team. As well, age can interact with schedule difficulty, and appears to
hurt the away team more.

I then simulate the season out (many times) to get point estimates for team wins.

Advantages:

- Everything is automated, including data collection, except for future line-ups. In theory this should be easy to re-run
next year.
- None of my models use forward-looking data, so I don't suffer from the biases that commonly plague models that do. 

Disadvantages:

- There is very little incorporation of expert knowledge.
- I pretend rookies don't exist.
- [RAPM][RAPM] would be a nice improvement.

# Where will the Warriors land?

My model sees the Warriors as an improved team that should win less games, and that feels right to me. Although smart
people with [more][Plausible projections] [thoughtful][Possible projections] [models][Ferrigan projections] disagree with me,
I'm going to stick with my model.

- The Warriors have improved substantially by adding Kevin Durant, but I don't think it's enough to win 73 games
- Last year they were excellent but also lucky, managing to win many of the games they could have narrowly lost. 
- They were also healthy. An extended injury to any of Steph Curry, Kevin Durant, Draymond Green, or Klay Thompson could cost them some wins.
- They lost Andrew Bogut (an exceptional defender and good passer), Festus Ezeli, and Harrison Barnes.
- They face a tough schedule. 
- They will take time to get the most out of their talent.
- They don't need to chase the record. They'll have their sights on the title.

On the other hand, my model probably underestimates how good they are because of how many games last year they
essentially took the fourth quarter off. So the truth may be somewhere between my model and last year.

For them to win more games many things need to go right for them. They are more likely to regress to the mean.

# Will the Heat flame out?

One team that stood out for me is the Miami Heat, tenacious second-round opponents of my Toronto Raptors. I have them
struggling hard. It turns out Vegas agrees with that, although not to the extent that my model has them (although
generally I would trust Vegas over myself). 

They lost Dwayne Wade, Luol Deng, Chris Bosh, and Joe Johnson, who all had [strong seasons][Miami stats] last year.
In particular, I didn't realize that Bosh played that much last year or that well: Win Score, VORP, and BPM all had him
as having an excellent season. New additions Derrick Williams, Dion Waiters, and James Johnson are all mediocre to bad
players. It's a totally different team.

# What's happening in Chicago?

My model sees Chicago as getting worse with Pau Gasol leaving. I'm curious to see who loses playing time to Dwayne Wade
– hopefully not the much superior Jimmy Butler. Rajon Rondo is a step up from Derrick Rose, and Robin Lopez is a solid centre, so it's
hard for me to imagine them being that bad with that many good players (Butler, Wade, Nikola Mirotic, Taj Gibson, Lopez) and an
improvement at their weakest position (Rondo instead of Rose and Kirk Hinrich).

# Are the Lakers back?!?

No. The Lakers should be better (but still bad) now that Kobe's hobble tour is over. The youth should improve a bit, and
they have added some non-horrible players.

# Most improved team?

I don't even know who will get a lot of playing time for the 76ers this year, or what crippling injuries they'll endure.
But almost by default they will be better than last year's 10 wins.
