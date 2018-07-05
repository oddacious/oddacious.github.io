---
layout:     post
title:      "Aiming for generalization with Hockey Hall of Fame models"
subtitle:   "On complexity and overfit in hockey models"
article-type: "long"
categories: ["hockey", "data", "hhof"]
description: "We can fit the data perfectly, but we shouldn’t. This is what’s known as the bias-variance trade-off.
The more precise we try to be in fitting the data at hand, the more likely we memorize effects that are due to random variation in the
training data that do not generalize to other datasets."
tags:       ["hockey", "NHL", "data"]
date:       2017-05-06 12:00:00
author:     "RDJ"
header-img: "img/complexity/rocket.jpg"
header-img-title: "Where the Dinosaurs Went"
header-img-link: "https://www.flickr.com/photos/baxterboy/7177983506/"
header-img-author: "timechaser (photo), David Random (artwork)"
header-img-author-link: "https://www.flickr.com/photos/baxterboy/"
header-img-license: "CC BY-NC-ND"
header-img-license-link: "https://creativecommons.org/licenses/by-nc-nd/2.0/"
---

[HHoF article]: {{ site.baseurl }}/hall-of-fame-model
[Top 100 article]: {{ site.baseurl }}/aspiring-to-greatness
[Effective DF]: https://arxiv.org/abs/1312.7851
[Model search DF]: https://arxiv.org/abs/1402.1920
[Wikipedia BIC]: https://en.wikipedia.org/wiki/Bayesian_information_criterion
[Wikipedia regularization]: https://en.wikipedia.org/wiki/Regularization_(mathematics)
[Wikipedia bias-variance]: https://en.wikipedia.org/wiki/Bias%E2%80%93variance_tradeoff
[Wikipedia generalization error]: https://en.wikipedia.org/wiki/Generalization_error
[xgboost]: https://github.com/dmlc/xgboost

I spent a lot of time thinking about overfit for my [Hockey Hall of Fame][HHoF article] and [NHL Greatest 100][Top 100 article]
modeling. This is almost a
textbook scenario where overfit is possible. I have many features to put into the models, but relatively few positive
cases to classify. It would be very easy to build a model that fits the data perfectly not because it has identified the
salient features of hockey glory, but because it has memorized the specific cases seen in the past. When building
classification models, the size of your minority class is key. In my sample I had only 221 members of the Hockey Hall
of Fame inducted as players who played in the NHL.

## Complexity in model building

There is a large and old literature on complexity, of which I have only casually perused over the years (yes, this is my
idea of fun). In a typical
linear or logistic regression we use the concept of degrees of freedom. The degrees of freedom are the number of free
values in your system: the number of observations minus the number of fit parameters. In linear and logistic regression,
it's the sample size minus the number of predictors, minus one more value for the intercept. If you have enough
parameters, you can perfectly fit your data, regardless of what that data is, and you have no degrees of freedom.

Degrees of freedom applies to other types of models, but not always with such a simple calculation. If your model
involves determining splines, for example, it has fewer degrees of freedom, but you may not realize that. Decision trees
can have substantial depth and use many arbitrary parameters. If you use boosted models (e.g. boosted decision trees, ala
[xgboost][xgboost]), then the number of fit parameters grows substantially. Even though there are problems with the
literal use of effective degrees of freedom in some domains (see [this paper][Effective DF]), the concept is important
to keep in mind when model building.

A related problem to model complexity is model search complexity. This is a topic that I believe is gaining in
importance yet is substantially under studied. There are many popular model search methodologies, and in many cases we
use automated hyperparameter optimization. Searching through possible models, such as searching through variable
combinations, increases the likelihood that we of a better fit to observed data, because more models are being
attempted. However this simultaneously increases the likelihood of finding a model that fits the data purely due to the
extensiveness of the search space. This is what Ryan Tibshirani (note: not Robert Tibshirani) has called "[model degrees
of freedom][Model Search DF]."

Further, not only does the model search procedure use up search degrees of freedom, but so do all decisions we make
based on the data. This includes:

- Choosing well-fitting feature transformations beforehand based on observing the data
- Changing sample inclusions/exclusions while building possible models
- Evaluating how the model does on a holdout sample and changing anything
- Deciding to switch from one type of model to another

Every choice we make based in some way on the data gives us an opportunity to fit the data better in a way that will not
generalize.

![Henrik Lundqvist]({{ site.baseurl }}/img/complexity/stormies.jpg){: .center-image }

<span class="caption text-muted">This photo has nothing to do with model complexity, but I love it.</span>

<div class="citation">

<p>

<a href="https://www.flickr.com/photos/23950335@N07/5513197198/">Image</a> from <a href="https://www.flickr.com/photos/23950335@N07/">W_Minshull</a> used under licence <a href="https://creativecommons.org/licenses/by/2.0/">CC BY</a>

</p>

</div>

## Bias-variance trade-off in hockey models

If the model you implement is sufficiently flexible, it could easily capture all of the data. In the Hockey Hall of Fame
case you could start with a rule that says “If the player has scored at least 1099 points and isn’t named Dave
Andreychuk or Vincent Damphousse or Jeremy Roenick or Pierre Turgeon, they’re in the Hall of Fame.” You don’t have to
put name in the model for this to happen: with enough features and enough flexibility, the algorithm can find a way to
exclude those players individually. There is practically no limit on the number of models I could build and compare. I
defined over 70 features. Even if those features were all binary, that would still be 2^70 possible distinct
permutations, far larger than the 221 members I need to identify or the over 7500 players who have played in the NHL, so
maybe I could even fit them all. In terms of variable selection, that’s over 2^70 different possible models, not
counting the choices made about type of model and sampling.

We can fit the data perfectly, but we shouldn’t. This is what’s known as the [bias-variance trade-off][Wikipedia
bias-variance] (which is a
horrible name for the situation it’s trying to describe, but it is the name used, so I’ll go with it). The more precise
we try to be in fitting the data at hand, the more likely we memorize effects that are due to random variation in the
training data that do not generalize to other datasets.

This is not a problem we can entirely optimize across observationally. If you use a holdout sample, you’ll end up
iterating through models that fit well on the training and holdout, indirectly optimizing against both. If you use
cross-validation, the same thing is possible. As long as we allow some selection, some choice of features or impacts or
samples based on observed data, we can end up choosing models that fit the data and will have high
[generalization error][Wikipedia generalization error].

I treated active and not yet eligible players as a natural out-of-time holdout (hypothesizing on who is HHoF worthy),
but if I started making model choices based on that small set, I would be fitting on that sample. It’s too easy to build
a model that fits the data, fits any in-time evaluation (e.g. holdout samples or cross validation), and fits our
expectations about which active or recently retired players will make the HHoF.

Worse, if the model is overfit, how will we know? New sample is generated at too slow a rate for us to identify problems
quickly. If we've looked at what the model says for recent batches and active players (and who wouldn't, that's the
fun part!) then we don't really have new sample until after that. We need new players to enter the NHL, play long
successful careers, and retire. Then for many of them, especially the borderline cases, we may have to wait years or
decades to see how it plays out.

Some people would take advantage of this: they would show off highly overfit models that (by design) look great any way
you look at them. It would be decades until they look wrong.

*That's not my approach.*

## Building HHoF and top 100 players models

I used three methods to reduce overfit: limiting memorization by limiting how particular the models can get, limiting
the impact of individual coefficients through L2 [regularization][Wikipedia regularization], and comparing models on
penalized metrics of model fit (specifically, [BIC][Wikipedia BIC]).

I didn't actually start with the HHoF model. The entire reason I arrived on this topic was because I was very intrigued
by the NHL's list of 100 greatest players. Making a list gives us so much to debate. Unlike the HHoF, which has been
populated over time by different groups, the top 100 list is populated all at once (presumably, although the NHL
released the earlier 33 names first), making the ultimate comparison across generations. Voters had to decide, all at
once, who were and were not the greatest 100 players. It's even tougher than HHoF admission because the marginal
players left off the list are so good that it can shock you to not see them on it.

I held back my anticipation and built the HHoF model first as a safeguard against overfit. With 221 players instead of
100, the HHoF can be less easily overfit. I built it first, and then restricted the top 100 model to subsets of the
variables used in the HHoF model, rather than using as thorough of a search space as the HHoF model had.

Within the HHoF model, I imposed limitations on myself ahead of time. Essentially I wanted to make my effects monotonic,
limit or eliminate interaction terms, avoid discontinuities in effect impact, avoid coefficients with unintuitive signs,
limit the number of evaluated models, and avoid effects that applied to too few players. This basically ruled our neural
networks or boosted decision trees and made logistic regression a suitable choice, with a restricted number of variable
sets possible. 

Then I mostly resisted the urge to make changes to fit my residuals. I know there are a few cases where the model's
predictions do not seem to make a lot of sense. But maybe getting too specific on fixing these, with sparse interaction
terms, would make the model wrong on future players in ways we cannot anticipate now. It's easy to spot the cases where
the model did not work, but miss the trends of where it worked dependably. The model has known weaknesses, but it is
fair. And that's about where I wanted to end up.
