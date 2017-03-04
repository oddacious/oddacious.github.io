---
layout:     post
title:      "A hand on the thermostat"
subtitle:   "Interpretations of inflation evidence" 
article-type: "short"
categories: ["curmudgeon", "economics"]
description: "If we wanted to test the impact of unemployment and expectations on inflation, we could study data from a regime where
inflation is not a goal of policymakers."
tags:       ["economics"]
date:       2017-03-03 12:00:00
author:     "RDJ"
header-img: "img/ends.jpg"
header-img-title: "."
header-img-link: "https://www.flickr.com/photos/carmendcluj/13677246453/"
header-img-author: "carmen_d_cluj"
header-img-author-link: "https://www.flickr.com/photos/carmendcluj/"
header-img-license: "CC BY-NC"
header-img-license-link: "https://creativecommons.org/licenses/by-nc/2.0/"
---

[Inflation 538]: https://fivethirtyeight.com/features/the-feds-favorite-inflation-predictors-arent-very-predictive/
[Paper Booth]: https://research.chicagobooth.edu/igm/usmpf/usmpf-paper
[Sumner]: http://econlog.econlib.org/archives/2015/10/a_theory_of_hou.html
[Rowe]: http://worthwhile.typepad.com/worthwhile_canadian_initi/2013/01/did-inflation-targeting-make-inflation-stickier.html
[Friedman]: http://www.msjc.edu/danpynn/documents/thefedsthermostat.pdf
[The Fed]: https://en.wikipedia.org/wiki/Federal_Reserve_System
[Endogeneity]: https://en.wikipedia.org/wiki/Endogeneity_(econometrics)

Today, researchers Stephen G. Cecchetti, Michael E. Feroli, Peter Hooper, Anil Kashyap and Kermit L. Schoenholtz 
released a paper, [Deflating Inflation Expectations: The Implications of Inflation’s Simple Dynamics][Paper Booth]
and a corresponding summary of it posted on FiveThirtyEight,
[The Fed’s Favorite Inflation Predictors Aren’t Very Predictive.][Inflation 538]

While there is lots of good content in both of these, I feel that they suffer from a serious issue that the authors have
entirely failed to address. A lot of people may reach an unfortunate conclusion.

Their argument is that the key metrics used by the [Federal Reserve][The Fed] to anticipate inflation, unemployment and
inflation expectations, are not predictive of inflation.

In their own words:

> In fact, once we account for that trend, neither labor market slack nor expectations help forecast inflation — they
> provide little information that isn’t already accounted for by the trend. The low predictive value of unemployment has
> been noted before, but the fact that expectations are also irrelevant is more surprising.

What they fail to discuss is that inflation is [endogenous][Endogeneity]. Inflation is part of the Fed's mandate. The Fed uses the
tools at its disposable to keep inflation near target. We shouldn't expect to see strong correlation between economic
conditions and inflation, because the Fed is trying to keep inflation steady. The better the Fed is, the less
correlation we should observe.

In the extreme case where the Fed was able to ensure constant inflation, then we would see 0 correlation between
economic conditions (or anything else) and inflation. That would not prove that unemployment and expectations are not
causal, but instead that the Fed is sufficiently capable of counterbalancing them.

I am not alone in making this argument. Here is Nick Rowe, an economist specializing in monetary policy, from a [blog
post back in 2013][Rowe]:

> One possible answer is that inflation targeting made inflation stickier than it used to be. Which means that inflation
> targeting became a victim of its own success. By making inflation sticky at 2%, it destroyed the very signal of
> deficient-demand recessions that monetary policy was supposed to respond to. The thermostat destroyed its own negative
> feedback mechanism.
>
> You can't test that hypothesis just by looking at inflation data. For example, the Canadian Phillips Curve does look a
> lot flatter over the last 20 years of inflation targeting than it used to. But of course it does. The whole point of
> inflation targeting means the Bank of Canada does its best to keep inflation at 2%. So if you put inflation on the
> vertical axis, and anything else whatsoever on the horizontal axis, the Bank of Canada is trying to make that curve look
> perfectly flat. Any lack of flatness reflects only the Bank of Canada's mistakes.

If we wanted to test the impact of unemployment and expectations on inflation, we could study data from a regime where
inflation is not a goal of policymakers.

[Scott Sumner][Sumner] also took on this topic. Both Rowe and Sumner were inspired by the
[thermostat analogy][Friedman] used by Milton Friedman. 

Given that, I don't see why Cecchetti et al. should be surprised. If unemployment and expectations are the inputs that the Fed uses,
then we shouldn't see significant inflation deviation correlated with their movements. Otherwise the Fed is either
unable or unwilling to counter their effect on inflation. That's a whole different can of worms, and very possible, but
it's not an issue that the authors identify. Their paper doesn't even include any variation on the word “endogenous.”

The topic of short-term changes in inflation around its trend due to changes in these factors is still
a relevant one, but the endogeneity issue is relevant, and we shouldn't simply compare the coefficients to each other
without considering it.

Other variables that are identified in regression may actually be capturing the residual inflation impact after the much
more powerful variables of unemployment and expectations are accounted for. The authors state “we conclude that
policymakers should pay attention to a broader array of factors rather than just focusing on expectations and slack.”
Well, maybe. Or maybe the mostly weak and insignificant coefficients that the authors find suggest that policymakers are
doing a good job with the variables they have. As usual, we can describe any story we want around the statistics.
