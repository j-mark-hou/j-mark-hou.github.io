---
layout: post
title:  "structural over-optimism in evaluation of AI impact"
date:   2026-02-17 00:00:00 -0800
categories: AI
---

TLDR: our inability to imagine the world in sufficient detail leads to over-optimism in our evaluation of AI impact in a fast-moving world


### structure-free evals in a slow-moving world

the idea is that you can estimate AI efficiency impact by:
1. sampling a representative set of tasks from the economy
1. look at AI's efficiency impact for each task
1. take a weighted average
    - this gives you an estimate of the first-order impact on total factor productivity via Hulten's theorem
1. repeat this over time (e.g. yearly), measuring incremental efficiency gain vs last time, and accumulate this into an overall cumulative impact

[OpenAI's GDPval](https://openai.com/index/gdpval/) is probably the highest-profile eval that's philosophically in this camp

I call these **structure-free evals**, because they **don't require explicitly modeling the future**:
1. no need to model the production function, as you're just computing a first-order approximation 
1. no need to model the set of tasks, just use the set of tasks today

the downside is that the per-task efficiency gains must not be too big in order for the first-order approximation to be plausible:
1. so that you can ignore the nonlinearities in the production function (e.g. because of bottlenecks)
    - e.g. if all of your tasks are twice as efficient, except for a single 'stakeholder alignment' step at the end, then weak links / Amdahl's law kicks in and your overall improvement is going to be far less than 2x
2. so that you can hold the set of tasks fixed by appealing to an envelope-theorem type argument
    - e.g. maybe the tasks that we think are bottlenecks today just get eliminated as a consequence of major efficiency gains, so who cares if AI provides 0 efficiency gain for 'stakeholder alignment'?

thus, the structure-free approach to evals is good in an environment where the impact of AI is slow enough that you can safely look at the first-order approximation over human-scale time periods (e.g. once per year), but kind of fundamentally hard to interpret in a world where things move fast



### structural evals in a fast-moving world
and it certainly feels like things in AI are moving very fast (e.g. if you're a software engineer who's watched AI go from being a mostly incoherent intern to writing 90%+ of your code over the past year)

so, if the world is moving too fast for the first-order approximation to be useful, then the structure-free approach is implausible, and we may be forced to do **structural evals** that **explicitly take a position on how the future is going to look**:
1. by modeling the set of tasks that will actually be relevant to the future
1. and how they will interact to produce output

for example, stories of 'recursive self-improvement' would fall into this camp:
1. the set of tasks that matter is whatever it takes to iteratively improve AI models
    - I'm sure the leading AI labs have versions of this where they just use the set of tasks that their researchers do today as a proxy
1. the production function is just "infinite output, once we achieve recursive self-improvement"

**I expect these kinds of structural evals to be too optimistic about future AI impact**:
- you're trying to predict an infinite dimensional object, i.e. 'all potential tasks that will be required for recursive self-improvement'
- whatever picture of the world we come up with will be much coarser than reality, lacking a bunch of fine-grained tasks that might be bottlenecks in the production, because we literally can't imagine what it would look like ahead of time
- so, even if the eval gets saturated, actual impact may be much lower


some of the hype around the [METR time-horizon eval](https://metr.org/time-horizons/) exemplifies this:
1. this eval has a bunch of software-related tasks, but far from comprehensive in terms of covering everything (not that the authors are targeting comprehensiveness)
1. it seems to be growing super-exponentially
1. if you don't think about this too carefully, you might conclude that this implies economic productivity is going to go to infinity fairly soon
1. whereas if in reality there's even a single bottleneck task that fails to see major efficiency gains, then overall economic impact will be far more modest

*note: this isn't a knock on METR: this sort of narrative is an organic consequence of e.g. there potentially not being anything better + people getting hyped without thinking too hard, rather than something that the authors explicitly advocate for*

this feels like a hard problem to overcome: **any picture of the world we build will always be incomplete, and this incompleteness will cause the eval to be too optimistic**
