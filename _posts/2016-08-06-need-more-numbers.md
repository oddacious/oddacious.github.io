---
layout:     post
title:      "In which a correlation test is not enough"
subtitle:   "538 could have made a better case against intra-team balance"
article-type: "short"
categories: ["curmudgeon"]
description: "The details that are needed to have an intelligent opinion on the matter simply are not
present. I don't know whether the claim is right or wrong, but this doesn't bring me any closer to that."
tags:       ["MLB", "FiveThirtyEight", "538"]
date:       2016-08-06 12:00:00
author:     "RDJ"
header-img: "img/ends.jpg"
header-img-title: "."
header-img-link: "https://www.flickr.com/photos/carmendcluj/13677246453/"
header-img-author: "carmen_d_cluj"
header-img-author-link: "https://www.flickr.com/photos/carmendcluj/"
header-img-license: "CC BY-NC"
header-img-license-link: "https://creativecommons.org/licenses/by-nc/2.0/"
---

[Source Text]: http://fivethirtyeight.com/features/mlb-teams-should-go-for-talent-not-balance-at-the-trade-deadline/
[BR]: http://basketball-reference.com
[Statistical Power]: https://en.wikipedia.org/wiki/Statistical_power

## Conclusions based on weak statistics

In [MLB Teams Should Go For Talent, Not Balance, At The Trade Deadline][Source Text], Neil Paine (Note: one of my
favourite sports writers out there, dating back to his [basketball-reference][BR] days), argues that it's pointless for
baseball teams to aim for balance at the trade deadline.

He could very well be right. But his article does very little to back up that claim.

As far as I can tell, here's what he did:

1. Calculate balance as the difference between a team's offense and their defense (relative to league average)
2. Calculate this separately for before and after the trade deadline
3. Take the difference
4. Calculate the correlation between change in balance and future winning, across a few specifications

Paine's correlation coefficients are not statistically significant, thus he reaches the conclusion that teams should not
particularly be aiming for balance.

First off, I could use a lot more details, where the article is vague:

- When looking at balance after the trade deadline, is this judging off of the entire remainder of the season? Which is
  also the outcome variable that it correlates against?
- Is this including all teams or just teams that made moves at the deadline?
- I'd like to see distributions of balance from before and after the trade deadline. Are they wider after, because it's
  a shorter window? Or less wide, because teams make adjustments to address their greatest weaknesses?
- What kind of confidence intervals could be put around a team's balance stat? Is this a high variance metric,
  especially on a subset of the season?

## Statistical power, or the lack thereof

This is a perfect example of when we should use [power analysis][Statistical Power]. Showing a statistically insignificant stat is not proof.
The power of a test is how likely we would be able to reject the null hypothesis when it is actually false. If you don't 
have enough sample size, you will have low test power.

Let me give an extreme example. Say I wanted to measure the correlation between human height and weight, but I did so on a
sample of three people. My correlation coefficient is going to be insignificant. That doesn't mean that height and
weight have no statistically significant relationship. It means my test did not have the power to measure that
relationship, if it existed. My test is useless. Worse, it's giving false confidence, an aura of scientific backing.

That could be a problem here. The balance metric could be highly unstable. Secondly, sure, there are hundreds of data 
points. But how many of them even made specific moves at the deadline? If it's few, then we're muting the relationship 
by including a bunch of points that have balance changes due to randomness. Run the stats on just the ones who 
made moves specifically targetted to increase balance. Then calculate how significant the true effect would have to be 
to pick it up given the sample size, considering the variance of the balance metric.

This article would have been better if it calculated power (caveat: here be dragons).

## Chasing a moving target

More data should be given on the moves teams made. Did some of the teams get more balanced, yet a lot worse, as they
traded off their best players during losing seasons? Out of the teams that got more balanced, how many specifically aimed
to get better and how many were purposely getting worse? Show the same for the teams who got less balanced. Look at
(pre-trade) performance of the players traded (and the distribution of minor league assets).

In a more detailed view, I'd like to control for how much better teams should expect to get based on the talent they
acquired or jettisoned at the trade deadline, and then see if teams over- or under-perform that in a way that correlates
with balance changes. I'd also try study truly exogenous events (such as injuries) that forced teams into balance
changes.

## Conclusions

This article is an example of throwing a couple of numbers at the reader and reaching broad conclusions that could be
wrong in a number of ways. The details that are needed to have an intelligent opinion on the matter simply are not
present. I don't know whether the claim is right or wrong, but this doesn't bring me any closer to that.

I like the question and I like the ideas, I just think this needed to be stewed on for a while longer before
publishing. More openness (more results, more data, more code even) would have helped in our shared quest for sports truth.
