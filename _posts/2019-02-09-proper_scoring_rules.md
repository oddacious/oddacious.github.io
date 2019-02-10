---
layout:     post
title:      "Proper scoring rules"
subtitle:   "How should we evaluate probabilistic forecasts?"
article-type: "long"
categories: []
description: "I love how this literature, and our entire understanding of probability, has either been about predicting rainfall of profiting through gambling."
tags:       ["basketball", "probability"]
date:       2019-02-08 12:00:00
author:     "RDJ"
header-img: "img/green_rain.jpg"
header-img-title: "rain"
header-img-link: "https://www.flickr.com/photos/quietpictures/189356146/"
header-img-author: "Mig Bardsley"
header-img-author-link: "https://www.flickr.com/photos/quietpictures/"
header-img-license: "CC BY"
header-img-license-link: "https://creativecommons.org/licenses/by/2.0/"
---

[nba2018]: {{ site.baseurl }}/NBA-predictions-2018
[nba2019]: {{ site.baseurl }}/NBA-predictions-2019
[scoringrules]: https://en.wikipedia.org/wiki/Scoring_rule
[gneiting]: https://www.stat.washington.edu/raftery/Research/PDF/Gneiting2007jasa.pdf "Gneiting and Raftery 2007 (PDF)"
[brier]: ftp://ftp.library.noaa.gov/docs.lib/htdocs/rescue/mwr/078/mwr-078-01-0001.pdf "Brier 1950 (PDF)"
[murphy]: https://journals.ametsoc.org/doi/pdf/10.1175/1520-0434%281998%29013%3C0005%3ATEHOPF%3E2.0.CO%3B2 "Murphy 1997 (PDF)"
[kelly]: https://www.princeton.edu/~wbialek/rome/refs/kelly_56.pdf 
[roulston]: https://journals.ametsoc.org/doi/10.1175/1520-0493%282002%29130%3C1653%3AEPFUIT%3E2.0.CO%3B2 "Roulston and Smith 2001" 
[selton]: http://www.eecs.harvard.edu/cs286r/courses/fall12/papers/Selten98.pdf "Selton 1998 (PDF)"
[tao]: https://terrytao.wordpress.com/2016/06/01/how-to-assign-partial-credit-on-an-exam-of-true-false-questions/ "Tao 2016"

## Background

I've been thinking a lot lately about how to evaluate probabilistic forecasts. The specific context is that I generate
playoff probabilities for each NBA team at the onset of each NBA season (see forecasts for the [current season][nba2019]
and [last year][nba2018]). Other people do this too. Ex post, how do we decide if my forecasts are better or worse than theirs?

If my forecasts had higher playoff probabilities for every team that ended up making the playoffs, and lower
probabilities for every team that missed them, then this isn't a challenge, since almost any reasonable way we approach
the problem will lead us to conclude that my forecast was better. But reality is rarely that simple. Compared to smart
forecasters, some of my probabilities will be directionally better, and some worse. How do we weigh these? The most
common choice is mean squared error (MSE, or *Brier* scores, after [\[Brier 1950\]][brier]), but this is only one of many potential
options, and may be more arbitrary than you expect.

The term for this field of study is [*scoring rules*][scoringrules], and it has a rich literature. I don't have anything to add at the
moment that extends the literature, but it might be helpful for me to run through some basics and explain my thinking.
I'll restrict to the binary case because it fits my use case and it makes the explanation simpler.

## One agreed upon principle: that we should only use proper scoring rules

A proper scoring rule is one which incentivizes the forecaster to always forecast correct probabilities. This might seem
obvious to the point of being unnecessary, but it actually excludes many rules. For example, mean absolute error (MAE)
is not a proper scoring rule. If we are evaluated on mean absolute error, then we are actually incentivized to always
report probabilities of 100% or 0%, depending on which is closer to our probability. We are incentivized to lie.
*Strictly Proper Scoring Rules, Prediction, and Estimation* [\[Gneiting and Raftery 2007\]][gneiting] is a great article that quite
comprehensively but succinctly summarizes many issues in scoring rules.

There are many proper scoring rules. All of them incentivize forecasters to give correct probabilities, yet they differ
in how they penalize incorrect probabilities. MSE is a proper scoring rule. By that standard, it works. But it is far
from the only proper scoring rule. Why do we use it?

Consider a motivating example. Let's say two forecasters are predicting a repeatable event, which will have a particular
positive outcome with some probability and a different outcome with the remaining probability, such that the two
outcomes sum to 100%. Forecaster A predicts a 0% probability of the positive outcome. Forecaster B predicts a 20%
probability. We test the event a great number of times, and observe the positive outcome 10% of the time. If we evaluate
the two forecasters by MSE, they both are equally wrong, and get an error score of 0.1. This makes sense, since they
were both off by by the same amount on average. But another way of looking at it suggests we should favour forecaster B.
The model used by forecaster B could still be correct, although with a likelihood that is diminishing as we increase
sample. But forecaster A cannot possibly be correct once we have observed a single occurrence of the positive outcome,
because they reported a 0% probability. Forecaster B is probably wrong, but forecaster A is definitely wrong. When we
say something will happen 0% of the time, and it ever happens, or we say it will happen 100% of the time, and it ever
fails to happen, we are fundamentally incorrect.

## The logarithmic scoring rule

Thankfully, I stumbled upon Terence Tao's very clear approach in [his blog][tao]. This saved me from working my way through the
math myself. Tao derives the logarithmic scoring rule through first principles. The logarithmic scoring rule applies
penalties to being wrong, according to the log of how correct the probability was. 

Tao picks a particular transformation such that a prediction of 50% gets
credit of 0 and a correct prediction with 100% confidence gets credit of 1. An incorrect prediction that has 100%
confidence gets negative infinity, as happens with all logarithmic scoring rules. The math is relatively easy to derive.
Leave it to Terence Tao to set aside the most debatable part of his logic as an exercise to the reader.

What all logarithmic scoring rules have in common is that as the prediction becomes more wrong, the penalty increases
exponentially, asymptotically approaching a negative infinity term in the case where the forecaster predicted with
absolute confidence and was incorrect.

The logarithmic scoring rule has a strong foundation in information theory, described in detail in [\[Roulston and Smith
2001\]][roulston]. It's also closely tied to formulations of how a gambler should optimize their bets for long-term profit, as
famously described in the [\[Kelly 1956\]][kelly].

## MSE versus log loss

MSE is a popular rule, but there isn't a strong fundamental basis for it. In Brier's original paper he proposes it and
describes its property of being proper, but without any backing for why it should be chosen over other proper scoring
rules. Philip E. Tetlock uses it for his long-running Good Judgment Project, so perhaps MSE is best-by-test.

As best I can find, *Axiomatic Characterization of the Quadratic Scoring Rule* [\[Selton 1998\]][selton] is the paper which
establishes a positive case for MSE, and offers a critical comparison versus the logarithmic scoring rule.

Selton offers two critiques of the logarithmic scoring rule. Both are related to the asymptotic property, where the
penalty for being confident and incorrect approaches an infinite asymptote. The first critique is the *insensitivity
property*, which is essentially about how once a scorer has been penalized by infinity, it doesn't matter how well they
perform on the rest of their predictions. The second critique is *hypersensitivity*, which is that the asymptote becomes
very extreme very quickly. Selton writes that this "implies the value judgment that small differences between small
probabilities should be taken very seriously and that wrongly describing something extremely improbable as having zero
probability is an unforgivable sin."

He's right to claim that the scoring rule is normative, but normative is a necessary property here - we choose which
grounds upon which we judge these scoring rules. Fittingly, his critique is very normative too. Selton frankly doesn't
like how extreme the differences can be for very small probabilities, and he doesn't like infinite penalties. 

Selton describes four axioms that are collectively satisfied by MSE but not by several other rules. In particular, his
fourth axiom, of neutrality, excludes the other rules. Neutrality is where a being wrong in either direction should be
equivalent - in his formulation, the expected loss of predicting p when q is true should be the same as predicting q
when p is true. But it's exactly this neutrality that, in probabilistic evaluations, I disagree with. Predicting 10% for
an event that is actually 0% likely should not be penalized as strongly as predicting 0% when it is actually 10% likely!
Selton writes that "the severity of the deviations between [two theories] should not be judged differently depending on
which of them is true or false."

![that just, like, your opinion, man]({{ site.baseurl }}/img/youropinion.jpg){: .center-image }
<span class="caption text-muted">My thoughts on that.</span>

But really, that's partially the point. Other than the property of being proper, we don't have universally accepted
axioms to weigh these scoring rules. Which means that individuals need to choose them, and argue for them on some
grounds.

## Practical ideas for the insensitivity property

We could adapt the logarithmic rule to support a lexicographic comparison. If we are comparing two forecasters, choose
the forecaster with the fewer number of infinite penalties. If they have the same number of infinite penalties
(including having 0 each), then evaluate on logarithmic loss of the remaining predictions. In this way we effectively
"cancel out" the infinite penalties. This breaks our likelihood interpretation and ruins the ratio of likelihoods, but
at least we would still have a rule for comparisons.

## Conclusion

I've warmed up to MSE as a practical choice, but I still prefer log loss in probabilistic settings. It has a strong
information theory foundation. It also fits a gambler's use case, which is one of the historical foundations of
probability and a key way we think about sports probabilities. As Roulston and Smith describe, about a log loss
formulation that they label *ignorance*, "a house setting
odds based on a minimum Brier score model will be expected to lose money to a gambler using the model with lower
ignorance". I'll stay on the side of the gamblers who don't lose money.

For a highly interesting paper on the early history of scoring rules, going back to at least 1793, see [\[Murphy and Brown
1997\]][murphy]. I love how this literature, and our entire understanding of probability, has either been about
predicting rainfall of profiting through gambling.

## References

Brier, G.W. (1950) Verification of Forecasts Expressed in Terms of Probability. Monthly Weather Review, 78, 1-3. 
http://dx.doi.org/10.1175/1520-0493(1950)078<0001:VOFEIT>2.0.CO;2

L. Kelly Jr, J. (1956). A New Interpretation of Information Rate. Information Theory, IRE Transactions on. 35. 185-189. 10.1109/TIT.1956.1056803. 

Gneiting, Tilmann & Raftery, Adrian. (2007). Strictly Proper Scoring Rules, Prediction, and Estimation. Journal of the
American Statistical Association. 102. 359-378. 10.1198/016214506000001437. 

H. Murphy, Allan & Brown, Barbara. (1998). The Early History of Probability Forecasts: Some Extensions and
Clarifications. Weather and Forecasting. 13. 5-15. 10.1175/1520-0434(1998)013<0005:TEHOPF>2.0.CO;2. 

S. Roulston, Mark & Smith, Leonard. (2002). Evaluating Probability Forecasts Using Information Theory. Monthly Weather
Review - MON WEATHER REV. 130. 10.1175/1520-0493(2002)130<1653:EPFUIT>2.0.CO;2. 

Selten, Reinhard. (1998). Axiomatic Characterization of the Quadratic Scoring Rule. Experimental Economics. 1. 43-61.
10.1023/A:1009957816843. 

Tao, Terence. (2016). How to assign partial credit on an exam of true-false questions?.

Tetlock, Philip &Gardner, Dan. (2015). Superforecasting: The Art and Science of Prediction. Crown Publishing Group,
New York, NY, USA. 
