---
layout:     post
title:      "And the winner is..."
subtitle:   "Hockey Pool Part 4: Season wrap-up"
categories: ["hockey pool"]
description: "For a long time I was further ahead of second place than second was from last. That gave me the freedom to play patiently.
But even I knew it would end. Good luck is dangerous, when it balances out with bad."
tags:       ["hockey", "hockey pool", "analytics"]
date:       2016-04-19 12:00:00
author:     "RDJ"
header-img: "img/frontier.jpg"
header-img-title: "Frontière/Border/Frontera"
header-img-link: "https://www.flickr.com/photos/elf-8/9492146155/"
header-img-author: "Christian Barrette"
header-img-author-link: "https://www.flickr.com/photos/elf-8/"
header-img-license: "CC BY-NC-ND"
header-img-license-link: "https://creativecommons.org/licenses/by-nc-nd/2.0/"
---

It’s over! After months of eager reader anticipation (as I imagine it, at least) the hockey pool is finished and I can
share results.

![Cherry]({{ site.baseurl }}/img/cherry2.jpg){: .center-image }

<span class="caption text-muted">This silly article can be the cherry on the top of my hockey pool series</span>

<div class="citation">

<p>

<a href="https://www.flickr.com/photos/santos/4650054828/">taotaomona sundae</a> from <a href="https://www.flickr.com/photos/santos/">chotda</a> used under licence <a href="https://creativecommons.org/licenses/by-nc-nd/2.0/">CC BY-NC-ND</a>

</p>

</div>

Enough suspense. I won! I dominated the regular season, and was fortunate enough to win the three playoff rounds and be
crowned champion. In this piece I will describe some of the action, and my analysis of it. 

## The draft

This did not go exactly as expected. A wrench was thrown into my delicately arranged plans: I had to travel for work
directly through the draft. Uncannily, although perhaps not surprisingly, this is the same scenario I was in the year
before. So what to do?

Ren&eacute;, being the wonderful and glorious man that he is, offered to draft on my behalf. The league commissioner also
extended such an offer, but I can't help but associate any commissioners with the ever shifty tsar of the NHL, Gary
Bettman.

I ordered by my rankings, but had to set my simulation engine aside, except for running some test drafts to try to 
perfect the order. I also included a rudimentary algorithm, instructing Ren&eacute; on when to follow the list and where he should deviate.

Here are the results:

| Pick | Player           | Position | Note   | 
| ---- | ---------------- | -------- | ------ |
| 1    | P.K. Subban      | D        | Keeper |
| 2    | Patrice Bergeron | C        | Keeper |
| 3    | Henrik Lundqvist | G        | Keeper |
| 4    | Ryan Kesler      | C, RW    |        |
| 5    | Pavel Datsyuk    | C, LW    |        |
| 6    | Tomas Plekanec   | C        |        |
| 7    | Blake Wheeler    | RW       |        |
| 8    | Alexander Steen  | C, LW    |        |
| 9    | Justin Faulk     | D        |        |
| 10   | Brandon Dubinsky | C, LW    |        |
| 11   | Bobby Ryan       | LW, RW   |        |
| 12   | Andrej Sekera    | D        |        |
| 13   | Brian Elliot     | G        |        |
| 14   | Drew Stafford    | LW, RW   |        |
| 15   | Evgeny Kuznetsov | C, LW    |        |
| 16   | Jack Johnson     | D        |        |

I picked Pavel Datsyuk high in my rankings, despite him being injured at the time. I was confident that I would
do well enough in the regular season that I could wait a while until he healed, and then hopefully he would be as
good as new (or as good as a 37 year old could reasonably expect to be). 

![Datsyuk]({{ site.baseurl }}/img/old.jpg){: .center-image }

<span class="caption text-muted">You're only as old as you feel, and no this isn't a close-up of Pavel Datsyuk</span>

<div class="citation">

<p>

<a href="https://www.flickr.com/photos/babymellowdee/1019455992/">Opa</a> from <a href="https://www.flickr.com/photos/babymellowdee/">babymellowdee</a> used under licence <a href="https://creativecommons.org/licenses/by-nc-nd/2.0/">CC BY-NC-ND</a>

</p>

</div>

Justin Faulk was particularly underrated. My numbers had him way higher, but I purposely asked Ren&eacute; to wait on
him, anticipating he would survive a few rounds. 

After Brandon Dubinsky, Ren&eacute; took charge and filled out my roster, and did so very well. Did you notice Evgeny 
Kuznetsov at the bottom? What a steal! 

Except, I promptly cleared him out of my lineup in my post-draft clean-up.

![Potatoes]({{ site.baseurl }}/img/potatoes.jpg){: .center-image }

<span class="caption text-muted">We all make mistakes. Some mistakes give you potatoes.</span>

<div class="citation">

<p>

<a href="https://www.flickr.com/photos/schippie32/22500625562/">Woops</a> from <a href="https://www.flickr.com/photos/schippie32/">Cees Schipper</a> used under licence <a href="https://creativecommons.org/licenses/by-nd/2.0/">CC BY-ND</a>

</p>

</div>

## The wicked hot streak

I started the season by winning. And then winning again. And then again and again. 11-1, 9-1, 7-2, 8-3. After four
weeks, I could have comfortably taken a week off and still been in first. And it didn't end there. All in all, I won my
first 15 matchups.

![The Mighty Ocean]({{ site.baseurl }}/img/ice_beats_boat2.jpg){: .center-image }

<span class="caption text-muted">Like the mighty ocean, I am unstoppable. And kind of a dick.</span>

<div class="citation">

<p>

<a href="https://www.flickr.com/photos/cardijo/6740113363/">M/V Ever Transport III</a> from <a href="https://www.flickr.com/photos/cardijo/">Harald Kobler</a> used under licence <a href="https://creativecommons.org/licenses/by-nc/2.0/">CC BY-NC</a>

</p>

</div>

A lot went well for me at that point. Tomas Plekanec and P.K. Subban were picking up big numbers during Montreal's great start.
Henrik Lundqvist and Brian Elliot (when he played) were solid in net. Bobby Ryan and Jarome Iginla were turning back the clock
from the bottom of my line-up. This win streak put me so far up in the standings that I could comfortably cruise to the
playoffs and still win the first seed. I (mostly) didn't have to do desperate moves to win match-ups. I was able to 
leave players on the injured reserve (IR) even when they weren't injured, to hog players and see how well they played
after recovery.

## The goalie problem

My most persistent problem was goaltending. Specifically, getting enough starts. Lundqvist was a rock, but Elliot split
goaltending duties in St. Louis with Jake Allen. There was one week where I had to pick up Jimmy Howard and then Cam
Ward to try to get my third start. After that I picked up Antti Niemi and dropped Elliot, getting myself that second
starter. In hindsight I should have kept Elliot one way or another. 

Later I tried to upgrade from Niemi to Sergei Bobrovsky, who had started poorly but then improved immensely. Of course,
he got injured right away, resulting in my picking up Curtis McElhinney (yes, really) to get a third goalie start, and
then bringing back Niemi right after. If I ever have a heart attack, it will probably follow some rough goalie luck.

I eventually added Cam Talbot, who played well this year. Overall my goalie numbers were bad, but not crushing.

## We all lose some

For a long time I was further ahead of second place than second was from last. That gave me the freedom to play patiently. But
even I knew it would end. Good luck is dangerous, when it balances out with bad.

> Most of us regard good luck as our right, and bad luck as a betrayal of that right.  
> &mdash;William Feather

The Canadiens crashed, Bobby Ryan went
cold, and a slew of injuries brought my team down to earth.  Justin Faulk, Alex Steen, P.K. Subban, and Michael Del Zotto all
missed lots of time. Near the end of my winning streak I could see it coming, with the last four wins on the streak
coming by close scores of 5-4, 6-4, 6-3, and 6-4. After that I lost four of my next five match-ups, including an 8-1
drubbing at the hands of last year's champion. It felt like anybody could beat me, and that my 1st place seed would be
worthless.

Luckily, things improved. Subban, Steen, and Faulk all eventually came back. I shuffled my line-up a bit. Then I won my
last two match-ups, and my three playoff rounds.

The finals was particularly tense, and couldn't be closer. We both made substantial line-up changes to fit the schedule,
both before and during the week. The categories themselves were mostly one sided, with each of us winning five. The tie
breaker? Head-to-head results...in which we split our match-ups 1-1 with category totals of 10-10-4. The second tie
breaker? Regular season record. All of those match-up wins matter.

## What worked  

* Weighing categories by predictability. I consistently dominated face-offs, hits, and blocks, making it
hard for me to lose match-ups. Likewise I did very well in shots on goal, assists, and powerplay points.
* Picking predictable skaters over unpredictable goalies. Goaltending is crucial, yet you can't guarantee
it. For every elite goalie who played up to expectations, there was another who was injured or inconsistent.
* Trusting the models and picking veterans. Players like Bergeron, Kesler, Datsyuk, Dubinsky, and Iginla could see their
legs give out on them at any time (sorry guys). But, it's not going to happen to them all at once, and they've played
well for a long time, so we have more certainty on their play than we do for rookies.
* Investing in the draft and not relying on any kind of trading efficiency. The league only had four trades all year.

## Where to go from here

Frankly, I'm not sure what to do next. There are so many ways I could improve my analytics:

* Per-game models, incorporating the opponent. This way I could optimize my line-up for any given roster, and it would
prepare me much better for the playoffs, when temporary roster moves can make a huge difference.
* Optimize the relative counts of forwards, defencemen, and goalies. I should have stuck with
Brian Elliot and been willing to pick-up a temporary goalie when he didn't get starts.
* Directly model goalies, or find a source. Save percentage is going to be hard to predict, but wins and goals against
average should have a much more persistent team effect.
* Build an age curve for predictions on young players.

I'm not sure if I'll do any of that, or instead play casually and put my efforts elsewhere. *We'll see*. It was fun while
it lasted!

![Adios]({{ site.baseurl }}/img/adios.jpg){: .center-image }

<span class="caption text-muted">Until next time!</span>

<div class="citation">

<p>

<a href="https://www.flickr.com/photos/phunk/362036424/">Adios</a> from <a href="https://www.flickr.com/photos/phunk/">Steve Rotman</a> used under licence <a href="https://creativecommons.org/licenses/by-nc-nd/2.0/">CC BY-NC-ND</a>

</p>

</div>

## Appendix

### Full schedule:

| Week     | Opponent  | Result | Score  |
|----------|-----------|--------|--------|
| 1        | Player 1  | Win    | 11 - 1 |
| 2        | Player 2  | Win    | 9 - 1  |
| 3        | Player 3  | Win    | 7 - 2  |
| 4        | Player 4  | Win    | 8 - 3  |
| 5        | Player 5  | Win    | 6 - 3  |
| 6        | Player 6  | Win    | 9 - 3  |
| 7        | Player 7  | Win    | 9 - 3  |
| 8        | Player 8  | Win    | 7 - 2  |
| 9        | Player 9  | Win    | 8 - 4  |
| 10       | Player 10 | Win    | 7 - 3  |
| 11       | Player 11 | Win    | 8 - 3  |
| 12       | Player 1  | Win    | 5 - 4  |
| 13       | Player 2  | Win    | 6 - 4  |
| 14       | Player 3  | Win    | 6 - 3  |
| 15       | Player 4  | Win    | 6 - 4  |
| 16       | Player 5  | Loss   | 4 - 7  |
| 17       | Player 6  | Win    | 8 - 3  |
| 18       | Player 7  | Loss   | 4 - 5  |
| 19       | Player 8  | Loss   | 1 - 8  |
| 20       | Player 9  | Loss   | 4 - 6  |
| 21       | Player 10 | Win    | 6 - 4  |
| 22       | Player 11 | Win    | 6 - 5  |
| Quarters | Player 9  | Win    | 6 – 4  |
| Semis    | Player 11 | Win    | 7 – 4  |
| Finals   | Player 5  | Win    | 5 – 5  |

### Match-up records:

| Team Name            | G       | A       | PPP     | SHG    | SOG     | FW      | HIT     | BLK     | W       | GAA     | SV%     | SHO     |
|----------------------|---------|---------|---------|--------|---------|---------|---------|---------|---------|---------|---------|---------|
| Bring Back Gilmour   | 9-13-3  | 16-8-1  | 14-11-0 | 7-3-15 | 14-10-1 | 24-1-0  | 18-6-1  | 19-5-1  | 8-11-6  | 13-12-0 | 14-11-0 | 7-3-15  |
| m.............       | 14-6-2  | 6-14-2  | 9-11-2  | 3-3-16 | 14-8-0  | 6-16-0  | 3-19-0  | 8-14-0  | 5-12-5  | 6-16-0  | 8-14-0  | 5-6-11  |
| Kar............      | 15-9-1  | 13-11-1 | 15-7-3  | 5-3-17 | 12-11-2 | 13-12-0 | 22-3-0  | 19-5-1  | 6-15-4  | 12-13-0 | 11-14-0 | 3-10-12 |
| S..............      | 13-9-3  | 10-13-2 | 11-14-0 | 8-2-15 | 17-7-1  | 16-9-0  | 18-5-2  | 9-14-2  | 12-11-2 | 10-15-0 | 12-13-0 | 5-6-14  |
| Kan................. | 12-10-3 | 10-13-2 | 14-11-0 | 7-3-15 | 9-14-2  | 7-17-1  | 10-14-1 | 7-18-0  | 18-3-4  | 14-11-0 | 16-9-0  | 10-7-8  |
| R.....               | 10-10-2 | 8-12-2  | 6-13-3  | 1-5-16 | 12-9-1  | 11-11-0 | 3-19-0  | 8-13-1  | 6-8-8   | 12-10-0 | 11-11-0 | 3-4-15  |
| D............        | 11-9-5  | 17-7-1  | 17-6-2  | 3-5-17 | 11-14-0 | 4-21-0  | 3-22-0  | 8-16-1  | 10-10-5 | 17-8-0  | 17-8-0  | 9-8-8   |
| F................    | 11-13-1 | 15-8-2  | 10-13-2 | 3-3-19 | 14-11-0 | 15-10-0 | 12-10-3 | 14-11-0 | 9-9-7   | 12-13-0 | 10-15-0 | 7-5-13  |
| Be................   | 10-10-5 | 14-9-2  | 7-14-4  | 4-3-18 | 13-11-1 | 18-7-0  | 18-7-0  | 10-15-0 | 9-14-2  | 11-14-0 | 9-16-0  | 2-5-18  |
| M.............       | 9-14-2  | 8-14-3  | 9-13-3  | 2-8-15 | 10-15-0 | 3-21-1  | 9-16-0  | 15-10-0 | 17-4-4  | 15-10-0 | 14-11-0 | 8-5-12  |
| Ba......             | 7-10-5  | 9-11-2  | 9-9-4   | 3-4-15 | 6-16-0  | 14-8-0  | 15-6-1  | 10-12-0 | 8-11-3  | 9-13-0  | 10-12-0 | 3-6-13  |
| H..............      | 5-13-4  | 7-13-2  | 11-10-1 | 1-5-16 | 8-14-0  | 12-10-0 | 8-12-2  | 14-8-0  | 9-9-4   | 13-9-0  | 12-10-0 | 6-3-13  |

### Totals: 

| Team Name            | G   | A   | PPP | SHG | SOG  | FW   | HIT  | BLK  | W  | GAA  | SV%   | SHO |
|----------------------|-----|-----|-----|-----|------|------|------|------|----|------|-------|-----|
| Bring Back Gilmour   | 236 | 439 | 224 | 7   | 2564 | 4515 | 1468 | 1137 | 59 | 2.60 | 0.912 | 7   |
| D............        | 279 | 434 | 252 | 4   | 2359 | 1680 | 857  | 800  | 62 | 2.38 | 0.92  | 10  |
| m.............       | 270 | 338 | 179 | 5   | 2370 | 1564 | 909  | 785  | 59 | 2.60 | 0.914 | 9   |
| R.....               | 264 | 395 | 194 | 2   | 2504 | 2206 | 741  | 751  | 50 | 2.52 | 0.909 | 4   |
| S..............      | 257 | 368 | 161 | 8   | 2430 | 2823 | 1389 | 762  | 53 | 2.53 | 0.916 | 6   |
| Be................   | 251 | 414 | 200 | 5   | 2570 | 3264 | 1534 | 876  | 57 | 2.44 | 0.915 | 7   |
| Kar............      | 240 | 445 | 218 | 6   | 2413 | 2489 | 1450 | 1106 | 48 | 2.36 | 0.916 | 6   |
| F................    | 234 | 438 | 212 | 4   | 2367 | 2633 | 1125 | 976  | 66 | 2.46 | 0.913 | 11  |
| Kan................. | 231 | 360 | 203 | 7   | 2329 | 1800 | 1086 | 772  | 95 | 2.40 | 0.919 | 10  |
| m.............       | 215 | 418 | 195 | 3   | 2389 | 1648 | 1188 | 1001 | 59 | 2.60 | 0.914 | 9   |
| Ba......             | 205 | 407 | 197 | 3   | 2234 | 2607 | 1381 | 885  | 46 | 2.70 | 0.912 | 4   |
| H..............      | 203 | 357 | 184 | 1   | 2308 | 2198 | 1108 | 930  | 63 | 2.20 | 0.924 | 8   |

### My relative rank by category:

| Team Name          | G | A | PPP | SHG | SOG | FW | HIT | BLK | W | GAA | SV% | SHO |
|--------------------|---|---|-----|-----|-----|----|-----|-----|---|-----|-----|-----|
| Bring Back Gilmour | 7 | 2 | 2   | 2   | 2   | 1  | 1   | 1   | 7 | 11  | 10  | 8   |

### My transactions:

| Date    | Dropped             | Added               | Notes                                             |
|---------|---------------------|---------------------|---------------------------------------------------|
| Sept 26 | Drew Stafford       | Michael Del Zotto   |                                                   |
| Sept 26 | Evgeny Kuznetsov    | Mikko Koivu         | Kuznetsov ended up having an amazing season       |
| Sept 26 | Andrej Sekera       | Cody Franson        | Sekera had a decent season                        |
| Oct 4   | Cody Franson        | Erik Johnson        |                                                   |
| Oct 5   |                     | Jarome Iginla       |                                                   |
| Oct 22  | Mikko Koivu         | Ryan Nugent-Hopkins |                                                   |
| Oct 27  | Jack Johnson        | Jimmy Howard        | Here I become desperate for goalie starts         |
| Oct 31  | Jimmy Howard        | Cam Ward            |                                                   |
| Nov 2   | Cam Ward            | Francois Beauchemin |                                                   |
| Nov 6   | Brian Elliot        | Antti Niemi         |                                                   |
| Dec 6   | Ryan Nugent-Hopkins |                     |                                                   |
| Dec 8   | Antti Niemi         | Sergei Bobrovsky    | Bobrovsky came off the injured reserve            |
| Dec 10  |                     | Curtis McElhinney   | ...and promptly went back on it                   |
| Dec 11  | Curtis McElhinney   | Antti Niemi         | ...leaving his backup as my only guaranteed start |
| Jan 15  |                     | Alex Goligoski      |                                                   |
| Feb 20  | Jarome Iginla       | Kyle Palmieri       |                                                   |
| Feb 20  | Alex Goligoski      | Michael Stone       |                                                   |
| Feb 21  | Michael Del Zotto   |                     | Injured for the season                            |
| Feb 21  |                     | Mikkel Boedker      |                                                   |
| Mar 4   | Mikkel Boedker      | Cam Talbot          | Talbot actually put up great numbers for me       |
| Mar 23  | Antti Niemi         |                     |                                                   |
| Mar 24  | Brandon Dubinsky    | Brayden Schenn      |                                                   |
| Mar 29  | Michael Stone       |                     | Injured for the season                            |
| Apr 3   | Bobby Ryan          | Scott Hartnell      |                                                   |
| Apr 7   | Sergei Bobrovsky    | Dmitry Orlov        | Got another defenceman                            |
| Apr 7   | Kyle Palmieri       | Frans Nielson       | Purely a tactical move by schedule and categories |
| Apr 8   | Tomas Plekanec      | Ryan Murray         | Desperately trying to get more hits               |
| Apr 8   | Justin Faulk        | Josh Georges        | Very desperate for hits                           |
