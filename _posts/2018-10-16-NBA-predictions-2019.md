---
layout:     post
title:      "NBA win predictions 2018-2019"
subtitle:   "Adapting my NBA season model for 2018-19"
article-type: "long"
categories: ["basketball"]
description: "A lot of these teams are really dragged down by having a few weak players, especially if they're expected to play significant minutes."
tags:       ["basketball"]
date:       2018-10-16 12:00:00
author:     "RDJ"
header-img: "img/arena_scene.jpg"
header-img-title: "Arena"
header-img-link: "https://www.flickr.com/photos/bartb_pt/2289459378/"
header-img-author: "bartb_pt"
header-img-author-link: "https://www.flickr.com/photos/bartb_pt/"
header-img-license: "CC BY-NC-ND"
header-img-license-link: "https://creativecommons.org/licenses/by-nc-nd/2.0/"
---

[Last year]: {{ site.baseurl }}/NBA-predictions-2018
[github]: https://github.com/oddacious/data/tree/master/NBA/201819 "GitHub link"
[Without Butler]: https://github.com/oddacious/data/blob/master/NBA/201819/predictions_no_butler_201819.csv "Predictions without Jimmy Butler"
[Jamal Crawford]: https://www.basketball-reference.com/players/c/crawfja01.html "Jamal Crawford's stats at basketball-reference.com"
[Zach Lowe predictions]: http://www.espn.com/nba/story/_/id/24944590/zach-lowe-nba-tiers-rankings-best-worst-teams-2018-19 "Zach Lowe NBA tiers"
[Danny Green injury]: https://www.si.com/nba/2018/07/24/danny-green-groin-injury-spurs-medical-staff "Danny Green played through injury"

Here we go! I realize that I'm a day late, but I'm not cheating. I made sure to get the tables on github last night, so you
can, like, totally [verify][github] that. It's almost like the season starts earlier every year.

# Gimme them predictions

Here we go. The method is exactly the same as [last year][Last year]. In fact, I only dug into this code again yesterday. I sure am glad it
worked...

### Eastern Conference

| Team                | Projected Wins | 2017-18 Wins | Improvement | Playoff Probability |
|---------------------|----------------|--------------|-------------|---------------------|
| Toronto Raptors     | 57.6           | 59           | -1.4        | 99%                 |
| Philadelphia 76ers  | 49.4           | 52           | -2.6        | 88%                 |
| Boston Celtics      | 48.7           | 55           | -6.3        | 86%                 |
| Washington Wizards  | 42.4           | 43           | -0.6        | 65%                 |
| Indiana Pacers      | 42.2           | 48           | -5.8        | 65%                 |
| Milwaukee Bucks     | 41.6           | 44           | -2.4        | 63%                 |
| Detroit Pistons     | 40.8           | 39           | 1.8         | 59%                 |
| Miami Heat          | 40.6           | 44           | -3.4        | 58%                 |
| Cleveland Cavaliers | 39.4           | 50           | -10.6       | 54%                 |
| Charlotte Hornets   | 38.7           | 36           | 2.7         | 50%                 |
| Brooklyn Nets       | 37.0           | 28           | 9.0         | 42%                 |
| Orlando Magic       | 31.7           | 25           | 6.7         | 25%                 |
| New York Knicks     | 28.8           | 29           | -0.2        | 15%                 |
| Atlanta Hawks       | 28.5           | 24           | 4.5         | 14%                 |
| Chicago Bulls       | 23.9           | 27           | -3.1        | 4%                  |

### Western Conference

| Team                   | Projected Wins | 2017-18 Wins | Improvement | Playoff Probability |
|------------------------|----------------|--------------|-------------|---------------------|
| Golden State Warriors  | 62.6           | 58           | 4.6         | 98%                 |
| Houston Rockets        | 55.0           | 65           | -10.0       | 90%                 |
| Oklahoma City Thunder  | 51.4           | 48           | 3.4         | 85%                 |
| Utah Jazz              | 48.6           | 48           | 0.6         | 77%                 |
| Minnesota Timberwolves | 48.0           | 47           | 1.0         | 73%                 |
| Denver Nuggets         | 47.6           | 46           | 1.6         | 73%                 |
| San Antonio Spurs      | 44.1           | 47           | -2.9        | 60%                 |
| Los Angeles Lakers     | 43.8           | 35           | 8.8         | 58%                 |
| Portland Trail Blazers | 41.2           | 49           | -7.8        | 47%                 |
| New Orleans Pelicans   | 40.0           | 48           | -8.0        | 43%                 |
| Dallas Mavericks       | 37.4           | 24           | 13.4        | 32%                 |
| Los Angeles Clippers   | 36.3           | 42           | -5.7        | 28%                 |
| Memphis Grizzlies      | 31.5           | 22           | 9.5         | 14%                 |
| Sacramento Kings       | 26.2           | 27           | -0.8        | 5%                  |
| Phoenix Suns           | 24.9           | 21           | 3.9         | 5%                  |

# The Warriors are very good

Yeah. Isn't that wonderful.

# Minnesota might still be solid

The tables here assume Jimmy Butler stays in Minnesota. I also [ran the numbers][Without Butler] without him (but not placing
him on any other team). Minnesota drops 3 wins and 10% on their playoff
probability. Even without Butler, they're a good team. They might improve by subtraction, since [Jamal Crawford][Jamal
Crawford] put up poor BPM numbers last year in substantial minutes.

Except, as Zach Lowe [said][Zach Lowe predictions], Minnesota needs "an alternate reality where everything isn't always ruined there". Who knows what will happen here.

# Bad players are as damaging as good players are beneficial

A lot of these teams are really dragged down by having a few weak players, especially if they're expected to play
significant minutes. The few teams that lack bad players really gain in the rankings. That's partially how Toronto has
such a great ranking. They don't have any bad players. Danny Green is an underrated pick-up, who had a weak year last
year while [playing through injury][Danny Green injury]. Having a line-up full of good players makes a team resilient to injuries.
Since the simulation takes into account minute variation, such as
if injuries occur, this doesn't hurt Toronto as much as other teams because weak players can't gain those minutes.

I was very surprised to see San Antonio this high up. They lack top talent now. But they also lack BPM bottom dwellers.
DeMar DeRozen and Jakob Poeltl might not be Kawhi Leonard, but they're solid players. The Spurs made the playoffs last year
without Kawhi Leonard. Maybe they can do it again. Although, I'm skeptical. I think the model underrates New Orleans,
because of how weak they are behind Anthony Davis and Jrue Holiday.

# Log jam in the middle

Especially in the East, half the teams in the conference are only separated by a few predicted wins. This could lead to
some close playoff races again. Even Cleveland has a chance. Maybe.
