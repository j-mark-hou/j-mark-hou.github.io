---
layout: post
title:  "Exponential smoothing and its discontents"
date:   2018-12-16 22:00:00 -0400
categories: statistics
---

[Exponential smoothing](https://en.wikipedia.org/wiki/Exponential_smoothing) is a pretty convenient way to produce forecasts for time series data.  The basic idea is that you take some (exponentially) weighted averages of your historical observations, and then project that forward to forecast the future behavior of your time series.  You can also incorporate growth trends and seasonality patterns in the same framework.  If all you want to do is forecast a single time series based purely on the historical values of that time series itself without worrying too much about stuff (e.g. [stationarizing your data](https://en.wikipedia.org/wiki/Box%E2%80%93Jenkins_method)), then exponential smoothing is a fairly reasonable choice.

Probably the most commonly used version of exponential smoothing is Holt-Winters.  It's quite a versatile algorithm and appears to work quite well for many applications.  However, it isn't quite flexible enough to cover at least one use case that sometimes arises in practice.  Here, I will:
- explain what Holt-Winters is
- demonstrate a failure case
- discuss how to slightly extend the model to account for this failure
- discuss how to implement this extension



### Exponential smoothing
I'll do a quick overview of what exponential smoothing is and do some demonstrations using the [ets package](https://cran.r-project.org/web/packages/forecast/vignettes/JSS2008.pdf) in R.  The code for all of the examples in this section is located [here](https://github.com/j-mark-hou/eazyes/blob/master/es_demo.R):
#### 1. Vanilla
Given a time series $$ y_1, ..., y_T$$, you can take an exponentially weighted average of this and use it as a forecast for how this series will evolve going forward.  Precisely:

- For smoothing parameter $$\alpha\in[0,1]$$ and initial state $$l_0$$, we can recursive define a 'rolling weighted level':

$$\begin{align}
l_t &= \alpha y_t+(1-\alpha)l_{t-1} \newline
\hat{y}_{T+h} &= l_T ,\quad h>0
\end{align}$$

- Interpretation:
  - Today's level is an average of today's realized value and yesterday's level.
  - Forecasts for any point in the future is just... today's level.

- $$\alpha$$ measures how 'present-biased' your exponential averages are (as in, if $$\alpha=1$$, then your forecast is just last period's $$y$$).  
- Given $$\alpha$$ and $$l_0$$, the rest of the sequence can be recursively computed.
- $$l_0$$ is the initial level, and typically you'll choose this by optimizing for 1-period-ahead forecast RMSE or likelihood or AIC or whatever.
- You can also optimize for ($$\alpha$$, $$l_0$$) jointly, or you can stipulate $$\alpha$$ and then optimize over $$l_0$$.

If you do this vanila smoothing, you might get something that looks like this:
![vanilla]({{ "/assets/images/2017_12_17_vanilla.png" | absolute_url }})
In this figure, we're optimizing both $$\alpha$$ and $$l_0$$, using data up until $$T=50$$ (red points).  The forecast (dotted black line) seems like it has some issues.  In particular, it's the same for all periods going forward, whereas based on the data we've seen already, we might expect some growth as well as some seasonality patterns.

#### 2. Trend
To do exponential smoothing with a trend, we simply just add another time series $$b_t$$ to capture the slope, and then do an exponential weighted average of that:
- For smoothing parameters $$\alpha, \beta \in[0,1]$$, and initial states $$l_0, b_0$$, we recursively define:

$$\begin{align}
l_t &= \alpha y_t+(1-\alpha)(l_{t-1}+b_{t-1}) \newline
b_t &= \beta (l_t-l_{t-1})+(1-\beta)b_{t-1} \newline
\hat{y}_{T+h} &= l_T +hb_T , \quad h>0
\end{align}$$

- Interpretation is straightforward:
  - Today's level $$l_t$$ is a weighted sum of the realized $$y_t$$ and the projected $$y_t$$ based on yesterday's level and slope
  - Today's slope $$b_t$$ is a weighted sum of today's implied slope $$(l_t-l_{t-1})$$ and yesterday's slope $$b_{t-1}$$.
  - To forecast, you just take latest level and add in slope times number of periods ahead.
- $$\alpha$$, as before is how present-biased your averaging of the level is.
- Similarly, $$\beta$$ represents how present-based your averaging of the slope is.
- Initial level and slope $$l_0, b_0$$ are generally set by optimizing for 1-period-ahead forecast perforamnce.
- You can also optimize both/either/none of $$(\alpha, \beta)$$ and together with $$l_0, b_0$$.

Applying this to the same example as above:
![trend]({{ "/assets/images/2017_12_17_trend.png" | absolute_url }})
here, we're optimzing for all of $$(\alpha, \beta, l_0, b_0)$$.  This does a bit better than before, but still doesn't account for the seasonal patterns.

#### 3. Seasonality
It looks like that the seasonal variations roughly get bigger as the levels get bigger, so we'll posit that seasonality is a factor that multiplies the baseline levels. To do this mulitplicative seasonality formulation, we just need to define a third series $$s_t$$ that we'll update in an exponentially weighted fashion:
- For smoothing parameters $$\alpha, \beta, \gamma \in[0,1]$$, seasonality period $$m$$, and initial states $$l_0, b_0, s_0, s_{-1},...,s_{-m+1}$$, we recursively define:

$$\begin{align}
l_t &= \alpha (y_t / s_{t-m})+(1-\alpha)(l_{t-1}+b_{t-1}) \newline
b_t &= \beta (l_t-l_{t-1})+(1-\beta)b_{t-1} \newline
s_t &= \gamma (y_t / l_t)+(1-\gamma)s_{t-m} \newline
\hat{y}_{T+h} &= (l_T + hb_T)s_u, \quad u = \max[u'<T \text{ s.t. } (T+h=u)\text{ mod}(m)], \quad h>0
\end{align}$$

- Interpretation is straightforward:
  - Today's level is an average of today's realized outcome (after normalizing for seasonality) with yesterday's projected level.
  - Today's slope is an average of today's change in level and yesterday's slope.
  - Today's seasonal adjustment is an average of today's ratio between actuals and level, averaged with last week's seasonal adjustment.
  - Forecast by extrapolating out the level and trend, and then multiply that by the most recent observed seasonality adjustment corresponding to the time we're forecasting for.
- $$\gamma$$ measures how present-biased your averaging of the seasonality term is.  Closer to 1 means more present biased, as with $$\alpha$$ and $$\beta$$.
- There's now a bunch more initial states: you need to initialize seasonality adjustments for each of the first $$m$$ periods, in addition to the initial level and slope.
- The initial states will be set by optimizing 1-period-ahead forecasts, and the $$\alpha, \beta, \gamma, m$$ may be fixed or estimated.

Continuing with the example above, now with a seasonality component:
![trend]({{ "/assets/images/2017_12_17_seasonal.png" | absolute_url }})
Here, we specififed the seasonality period $$m=7$$, and optimized $$\alpha, \beta, \gamma$$ together with $$l_0, b_0, s_0, s_{-1},...,s_{-m+1}$$.  Things finally look good!


### Holt-Winters exponential smoothing
The models in all 3 of the examples above were special cases of this more general class of models called Holt-Winters exponential smoothing.  This class of models also covers situations where we would want multiplicative trends (instead of additive as in the examples above) and/or additive seasonality patterns (as opposed to multiplicative in the examples above).  In these cases, the recursion equations would be a bit different than the ones in the examples above, but the basic idea would still be the same:
- Define some smoothing parameters $$(\alpha, \beta, \gamma)$$ in $$[0,1]$$.
- Define some initial states for the trend, slope, seasonality $$(l_0, b_0, s_0,...,s_{-m+1})$$.
- Use the relevant recursion equations to compute $$y_t$$ for all the $$t$$s in your data.
- Optimize the values of your initial states and all/some/none of your smoothing parameters by using the in-sample $$y_t$$s you computed above.
- Use the optimized values to generate forecasts for times beyond the end of your data.

This Holt-Winters thing is really nice because often you can just literally throw your data into some package for doing this (e.g. ETS in R) and very quickly get forecasts that look ok.  In addition, the model is fairly flexible, and can fit quite a lot of the time series you might see in practice fairly well.


#### One limitation of Holt-Winters
There's at least one situation that doesn't fall within the set of things covered by Holt-Winters.  Holt-Winters requires that the seasonality either not scale with the level of the series (as in the case with additive seasonal patterns), or that it scales linearly (as in the mulitplicative case above).  That is, in the Holt-Winters setup, the amplitude of the seasonal variation must be either constant, or a linear function of the level.  

In the examples above, we generated data where the seasonal variation was proportional to the level of the series.  Thus, in example 3, the multiplicative seasonality Holt-Winters model worked quite well.  However, if we just uniformly add some large number to the example above, then Holt-Winters becomes incapable of capturing the growth in seasonality.  For example, if we add 1000 uniformly to the example series and then try to fit a Holt-Winters model, we get something that looks like this:
![trend]({{ "/assets/images/2017_12_17_fail1000.png" | absolute_url }})

The reason for this is clear: the level of our series only varies from 1000 to 1050 or so, and since Holt-Winters forces either no seasonality scaling or linear seasonality scaling wtih the level, it's unable to capture the growth patterns in the seasonality seen here.

To give a motivation for how a time series like this might arise in practice, you could think of a situation of like this:
- think of some tourist attraction
- there's some baseline level of people visiting this place year around
- during holidays there's some extra visitors on top
- the people running the attraction have been ramping up holiday advertising
- thus, the seasonal variation is increasing in proportion with the holiday advertising, not with the baseline visitor levels year round


### Slightly extending Holt-Winters 
To be fair, the particular failure cases of Holt-Winters diagnosed above should manifest largely in situations where the baseline levels are large relative to the size of the seasonal variation.  If the seasonal variation is small relative to the baseline, then even if this seasonal component is growing over time, there's some sense in which it doesn't really matter if you just... don't model that growth.  But nonetheless, it's fairly instructive and not very hard to just implement a fix, and there's some small fraction of cases where it'll make stuff easier, so we'll just do it.