---
layout:     post
title:      "NBA March Madness"
subtitle:   "How to bring the world's best tournament to the world's top basketball league"
categories: ["basketball"]
description: "For sports fans, March Madness is an event like no other. It’s where the top 64+ teams in college
basketball get together to play a win-or-go-home single elimination tournament. Every year I wonder
why the NBA doesn’t get in on the action." 
tags:       ["basketball", "tournament"]
date:       2015-09-07 12:00:00
author:     "RDJ"
header-img: "img/toronto_rokni.jpg"
header-img-title: "Toronto & the moon"
header-img-link: "https://www.flickr.com/photos/roozbeh11/2848374705/"
header-img-author: "Roozbeh Rokni"
header-img-author-link: "https://www.flickr.com/photos/roozbeh11/"
header-img-license: "CC BY-NC-ND"
header-img-license-link: "https://creativecommons.org/licenses/by-nc-nd/2.0/"
---

[march madness]: http://espn.go.com/mens-college-basketball/tournament/bracket "ESPN: NCAA Tournament Bracket"
[schedule1]: http://espn.go.com/blog/truehoop/post/_/id/19219/how-to-build-the-nba-schedule "ESPN: How to build the NBA schedule"
[schedule2]: http://bleacherreport.com/articles/2552322-as-nba-schedule-maker-departs-he-takes-with-him-an-era-league-wont-see-again "Bleacher Report: As NBA Schedule-Maker Departs, He Takes with Him an Era League Won't See Again"
[Coase Theorem]: https://en.wikipedia.org/wiki/Coase_theorem "Wikipedia: Coase Theorem"
[upsets]: https://www.washingtonpost.com/news/early-lead/wp/2015/03/19/here-are-the-top-upsets-in-ncaa-tournament-history/ "WaPo: Here are the greatest upsets in NCAA tournament history"

For sports fans, March Madness is an event like no other. It's where the top 64+ teams in college basketball (NCAA
Division I) get together to play a win-or-go-home [single elimination tournament][march madness]. The format lends itself to [upsets][upsets], and
having the games on overlapping time periods makes it exciting to flip between games and catch the ones coming down to
the wire.

Every year I try to set aside some time in March (and early April) to follow the tournament, and like millions of other
people I join a pool and make a totally uninformed guess at how the games will play out. Other than the tournament, I
don't really follow the NCAA. I follow the NBA. Every year I wonder why the NBA doesn't get in on the action. There are
a lot of obstacles to an NBA March Madness, which has probably precluded taking up the idea seriously. But never fear –
I've now figured them all out and am ready to present my comprehensive solution below, totally free of charge (Except
for my share of broadcasting revenue, that is...). Let's dig into those problems and my proposed solutions.

## #1 How do you make teams want to participate?

Are teams really going to risk injuring their players in extra games? Is this happening in March, in the closing stretch
of the season? How do we reward the teams?

It's not actually March Madness – it's *November Madness*. Do it to start the season, before we really know how good any
teams are. 

Here's the big trick to making the teams try: **Make the games count**. Every win counts as a win in your record, and
losing creates a loss. In any game your incentive is to win. 

In later points I'll explain how I make this work with the schedule, and a secondary benefit to winning.

## #2 How to make the tree work?

The NBA doesn't have 64 teams. It doesn't even have 32 teams.

This is true. But you know what it does have? 30 teams. Give the NBA finalists from the prior year a bye, and now a try
can be made that's just a round shorter than the NCAA.

## #3 How do we set the seeds?

That's the fun part. Here's one idea I really like: in each conference, order the teams by their playoff finish and then
by their standing. Then, swap every second seed in each conference with the other. So Houston, by virtue of making it to
the Western Conference finals, swaps with Atlanta, who lost in the East finals. Now we get to watch match-ups that we 
rarely see, while also doing something about conference imbalance. Here's what this would look like based on the 2014-15
NBA season: 

![NBA 2015 Tree]({{ site.baseurl }}/img/NBA_2015_tree.png){: .center-image }
<span class="caption text-muted">How 2015 would look</span>

The cross-conference format could lead to some totally unexpected results. Further, the potential of Warriors-Thunder
and Cavs-Pelicans games seem enticing.

Another way to do it would be to just have entirely random seeding. You'd have a lot of lucky and unlucky teams, but it
would be a lot of fun guessing how it would play out.

## #4 Where are the games played?

Play the first round at the arena of the higher seeded team. The seeding would be deterministic from the end of the
prior year, so that gives the schedulers time to figure it out. Using two days for the first round (7 games each,
because of the bye), most arenas should be able to make one of those days work.

Schedule the remaining rounds in any cities of interest. Choose possible future NBA locations or huge college towns. I
bet Seattle would love it. There would be a few stories every year about players going back to their home town or their
school, and having extra motivation to do well in the tournament.

## #5 How to make the schedule add up?

Here's where the details get ugly. Really ugly. If you're not interested, you can [skip this part](#conclusion) and just trust that
I've (sort of) figured something out.

The challenge is that teams are going to play one to five (bye teams can only play up to four) games, and how many they
play is non-deterministic. Yet we still want every team to play 82 games and have an even share of home and away games.

If we follow the above proposal of having every round after the first hosted in a neutral location, we actually cannot
guarantee that an even balance of home and away games will work out. Some teams will play an odd number of neutral
games, meaning that their remaining game count is not divisible by two and they will have one more or less home game
than away games. If we're willing to accept this, I'll explain how we can make the rest of it work out alright.

Before the season, for every team we schedule 77 regular games, plus the first game of the tournament. For teams who
play their first tournament game at home, we schedule 38 other home games and 39 away games. For teams who play on the
road, we schedule 39 other home games and 38 away games. This way, for every team except the bye teams, we have a
balanced 78 games, with four more to allocate between home, away, and neutral. Teams will have up to two more home games
and up to two more away games which are not deterministic at this time.


| Seed         | Status                             | More Home | More Away |
| ------------ | ---------------------------------- | ----------| --------- |
| Home or Away | Lose 1st round                     | 2         | 2         |
| Home or Away | Win, lose 2nd round                | 1 or 2    | 1 or 2    |
| Home or Away | Win, win, lose 3rd round           | 1         | 1         |
| Home or Away | Win, win, win, lose in semis       | 0 or 1    | 0 or 1    |
| Home or Away | win, win, win, win, play in finals | 0         | 0         |
| Bye          | Lose 2nd round                     | 2         | 2         |
| Bye          | Win, lose 3rd round                | 1         | 2         |
| Bye          | Win, win, lose in semis            | 1         | 1         |
| Bye          | Win, win, win, play in finals      | 0         | 1         |

I propose that the bye teams are scheduled 39 home games and 38 away games, so that if they do lose in either the 2nd
round or the semis, they end up with one more home game than away games. Another perk of winning the conference.

In that initial schedule, we reserve dates for these games, and we'll reserve them all on the same dates. For example, take a
Wednesday and a Saturday one week, and a Wednesday and a Saturday from another week. For each team, book the arena for
one day in each week, trying to make the Wednesdays and Saturdays add up. These are flex dates where the opponent is
(before the tournament) unknown and the game itself is not guaranteed to happen.

If this sounds like a scheduling nightmare for the [people][schedule1] [creating][schedule2] the NBA schedule, that's because it is. But it also
has one perk for the teams: they can package the extra one or two home games as special events, and sell them after
they've already put the other games of the season on the market.

Here's the nice part: Put these two weeks near the end of the season, and if teams go far enough in the tournament to
not need the games, they get the nights off and the arena can book other events. Put the weeks near each other, maybe
with one week separating them so the teams do not get stale. By having these games near the end of the season, it's an
extra incentive to win in the tournament: you'll win yourself recovery time near the end of the season. This gives
players more time to recuperate and prepare for the playoffs. 

## #6 How do we make this profitable for all the teams?

There's a remaining problem that teams now have less home games and thus less ticket revenue. However, as long as total
revenue from November Madness exceeds the lost revenue from later games, we can divide it up such that everyone is
better off (although just because we *can* do that does not mean we *will* do that). Fans get less home games, but also a
great tournament to watch.

This entire proposal relies on the
assumption that TV ratings would be very high, and that live attendance during the tournament would also be substantial,
and that putting these two together can increase total profits. If that is the case, then we can scale the shares by how
many home games each team is foregoing, and thus by how far each team survives in the tournament. If the revenues are
sufficiently high, [we can negotiate a structure such that we can make every team better off][Coase Theorem], but make the 
winners even more better off.

## Conclusion

There you have it. That's my proposal. I think it would accomplish a few things:

- Create an incredibly fun and wild NBA tournament to kick off the season
- Bring NBA exposure to more cities and markets 
- Incentive every year to do well, through
    - The games count towards their record
    - Winning creates rest time late in the season
    - Winning increases your share of the profits

All of this can be done with only small impacts to the existing NBA schedule, but with huge benefits for the fans and
league exposure.
