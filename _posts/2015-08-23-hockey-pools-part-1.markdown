---
layout:     post
title:      "Thinking about hockey pools"
subtitle:   "Hockey Pool Part 1: Getting my head around the problem"
categories: ["hockey pool"]
description: "
I'd never been in a hockey pool before. Not a real one. I had done a couple of simple ones, with Ren&eacute; and other classmates, but those were pick-em-and-leave-em. That was by design. We all wanted to focus on grad school (and drinking – two non-mutually exclusive concepts) and didn't want the winner to be the person who slacked off on studying the most. Most of my effort then was drafting. I played with no bench, no lineup changes, no trades. Now I was invited to a real pool. How was that going to work out?" 
tags:       ["hockey", "hockey pool", "analytics", "predictive modeling", "simulation", "optimization"]
date:       2015-08-23 12:00:00
author:     "RDJ"
header-img: "img/lawnchairs.jpg"
header-img-title: "Lawn Chairs"
header-img-link: "https://www.flickr.com/photos/rogersmj/2818051093/"
header-img-author: "Matthew Rogers"
header-img-author-link: "https://www.flickr.com/photos/rogersmj/"
header-img-license: "CC BY-NC"
header-img-license-link: "https://creativecommons.org/licenses/by-nc/2.0/"
---

[lundqvist]: https://en.wikipedia.org/wiki/Henrik_Lundqvist "Wikipedia: Henrik Lundqvist" 
[bergeron]: https://en.wikipedia.org/wiki/Patrice_Bergeron "Wikipedia: Patrice Bergeron"
[bergeron-faceoffs]: http://espn.go.com/nhl/statistics/player/_/stat/faceoffs/sort/faceoffsWon/year/2015 "ESPN: Faceoff Statistics"
[shg]: http://www.hockey-reference.com/leaders/goals_sh_season.html "Hockey-Reference: Records for Short-Handed Goals"

It started a year ago. 

> “Two things, thinking about doing a hockey pool this year. Would you be interested?” 

That's how Ren&eacute; recruited me. I'd never been in a hockey pool before. Not a real one. I had done a couple of simple ones, with Ren&eacute; and other classmates, but those were pick-em-and-leave-em. That was by design. We all wanted to focus on grad school (and drinking – two non-mutually exclusive concepts) and didn't want the winner to be the person who slacked off on studying the most. Most of my effort then was drafting. I played with no bench, no lineup changes, no trades. Now I was invited to a real pool. How was that going to work out? I know what I'm doing, right?

![I'm in trouble]({{ site.baseurl }}/img/NHL3.jpg){: .center-image }
<span class="caption text-muted">Not so much.</span>

<div class="citation">
<p>
<a href="https://www.flickr.com/photos/dugspr/2355994458/in/album-72157604216116798/">Image</a> from <a href="https://www.flickr.com/photos/dugspr/">Douglas Sprott</a> used under licence <a href="https://creativecommons.org/licenses/by-nc/2.0/">CC BY-NC</a>
</p>
</div>

I had no idea what I was doing. Halfway through the season I was mired near the bottom, way ahead of the absentee players (and probably Ren&eacute; too – sorry bud), but far behind the leaders and with no plan of how to catch up. That's when I decided _**it's time to get good at this**_. This is the story of how it happened.

To begin with, I have to explain hockey pools. You don't need to know much about hockey or pools in general. You can approach this as any game, like a board game even. The hockey game could be played out with dice. Or you could approach it like a businessman: you have assets to manage, and structured decisions to make. Your decisions will have ramifications in the short term and the long term. You don't have to play hockey to be in a hockey pool.

My approach has shades of different perspectives, and reflects how my thinking was shaped through my education and experience. From game theory I have concepts of dynamic equilibria and repeated games. From applied statistics I've taken optimization and predictive modelling. Simulation and a distinct empirical bent come from my time programming. I'd like to say that my understanding of the interaction between strategy and tactics comes from business studies and is hardened through case competitions, but it really comes from chess. 

If you somehow didn't already think I was a nerd, it should be getting a lot clearer.

## The Concept of a Hockey Pool

Hockey: A beautiful friction-defying game whose players push a sliding piece of rubber around with sticks in an attempt to slip it past opponents who look like they've been eaten up by foam rectangles. There are parallels between concepts in a hockey pool and concepts in the NHL (or the "real world" as some might call it). In the NHL there are teams. Likewise, I have a team. In the NHL, teams choose lineups to play in games. Likewise, I choose a lineup. The NHL has a season, and I have a season. The hockey pool is a game, where you manage a team and reap the benefits (or consequences) of your management. You have strategic and tactical choices to make, just as a general manager or a coach would in the NHL. You will be the beneficiary and the victim of blind luck. You are pitted against your friends in a struggle for glory.

In a hockey pool, you have a team. In my hockey pool, each team consists of up to 16 players. For example, [Henrik Lundqvist][lundqvist], the stud goaltender on the New York Rangers, is on my team. This means he's not simultaneously on any other team – he's just on my team. Henrik Lundqvist is a real person, but in our league he is on my team and my team alone. I'm lucky to have him and gave up the opportunity to have another great player in his place. My team has an eclectic selection of hockey players across all positions, as does every other team. Although there will probably be changes to your team over the season, you make them at your discretion. I never have to lose Lundqvist if I don't want to (and I really don't want to).

![Henrik Lundqvist]({{ site.baseurl }}/img/clyde 2.jpg){: .center-image }

<span class="caption text-muted">You're my boy, Blue!</span>

<div class="citation">

<p>

<a href="https://www.flickr.com/photos/clydeorama/5618716532/">Image</a> from <a href="https://www.flickr.com/photos/clydeorama">clyde</a> used under licence <a href="https://creativecommons.org/licenses/by-nc/2.0/">CC BY-NC</a>

</p>

</div>

What do you do with these players? You insert them into your lineup and face other teams. What I describe below is a “category” style of league. There are other types of hockey pools, and they all can configure specific rules, but this is how mine worked. In any given week during the hockey pool season, my team is going head-to-head with a specific opponent's team, in what we call a match-up. In our match-up we are fighting over 14 categories of performance: 

* Goals (G)
* Assists (A)
* Plus/Minus (+/-)
* Penalty Minutes (PIM)
* Powerplay Points (PPP)
* Shorthanded Goals (SHG)
* Shots on Goal (SOG)
* Faceoffs Won (FW)
* Hits (HIT)
* Blocks (BLK)
* Wins (W)
* Goals Against Average (GAA)
* Save Percentage (SV%)
* Shutouts (SHO)

Yes, I copied that from Yahoo's website.

The amount of goals my team gets during the week is (with a caveat) the number of goals my players score, in the real world, in that week. If [Patrice Bergeron][bergeron] scores a pair of goals, then those two goals add up towards my total. The real Patrice Bergeron will likely play in 2-4 NHL games in that week. If he has a quiet week, he won't score any goals, the Boston Bruins in the real world might be losing, the fans in Boston will be complaining, and he doesn't help me much. Alternatively, he might have a great week and provide several goals, which makes everyone happy except for fans of opposing teams in the real world and the owners of my opposing teams in the hockey pool. If the real Bergeron is injured, well, he's injured on my team too and I'm in trouble.

Whether or not Patrice Bergeron scores any goals, he's likely to contribute to a variety of categories. He moves the play and picks up a lot of assists. He takes faceoffs (and is actually [one of the best at doing so][bergeron-faceoffs]), so he'll contribute a lot of faceoff wins to my team. Although he's not known for physicality, he will pick up some hits. Across the 10 of the 14 categories that pertain to skaters (not goalies), he might contribute to many. For each category, if my team as a whole has a higher count than my opponent's team, I win that category. If my players combine for 15 goals and my opponent's players combine for 10, then I've won the goal category for that week. I might win a handful, my opponent might win a handful, and we might tie in a couple of cases (probably neither of us will have any shorthanded goals, because they are [so rare][shg]). If I win the most categories, great, I've won the match-up. For this week I get a win and my opponent tallies a loss. 

Every week my opponent rotates, so we all face each other team a number of times. Although in any one week I might win or lose by fluke, riding the ups and downs of hot and cold streaks by my players and the teams they are on, over the course of the season my rank should correlate well with how productive my players have been, and how well I've managed my team (more on that to come). This aligns with how teams in the real world perform. I lost my first match-up, and my second, managed to win my third, etc.

There's a lot more to it than that, but I wanted to get the general idea across.

## Where does strategy come in?

Everywhere. Don't be fooled by the sports: this is actually a highly complex game, much more complex than most board games. It cannot be very simply optimized. 

Here are some of ways you can influence the game:

* You can get rid of your players and pick new players, as long as these new players are not on any other team. There are 800+ players in the NHL, but we were in a 12 team league with 16 roster spots, implying only 12x16 = 192 players are in use. Presumably, these are most of the best ones. The remaining players are free agents, and the best of them are probably not much worse than your worst players
* You can trade players with other teams. Some trades might be mutually beneficial (for reasons that I have not explained yet, but probably should at some point) but many of them will involve one of you getting fleeced by the other, which creates good material for trash talk
* You don't actually play your whole team at once. You have 16 roster spots (players you've claimed and which are exclusively yours), but you play only up to 12 of them at a time. Specifically, you can only have 2 centres, 2 left wings, 2 right wings, 4 defencemen, and 2 goalies. You can change your lineup every day (called setting a lineup), picking a different allocation of players. For starters, you want to pick players who have games that day. Although the NHL has some busy nights (most teams play on Tuesdays, Thursdays, and Saturdays), there are usually a few games on the other nights too. Further, on those busy nights you may have too many players to choose from, so you have to choose wisely (but how? Read on!)
* Combined with the first point, this implies that you can drop and add players to get more games in during a match-up. The players at the margin of your team could be dropped and replaced with ones who will fit into more games for your lineup in a given week
* You pick the team in the first place. I've glossed over that so far, but it's a major part of the strategy. You pick a team through the draft

To find out how I did in my first season, read the next article in this series, [{{page.next.subtitle}}]({{page.next.url}})
