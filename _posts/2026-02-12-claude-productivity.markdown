---
layout: post
title:  "selection bias and AI productivity measurement"
date:   2026-02-11 00:00:00 -0700
categories: AI
---

TLDR: measuring AI productivity from usage data overestimates current impact but underestimates rate of improvement


### background
recently, Anthropic released some work on the potential economic impact of AI, using internal Claude usage data, where they find that AI technology as it exists today might be able to double US labor productivity growth:
- [2025 paper on estimating productivity gains](https://www.anthropic.com/research/estimating-productivity-gains)
- [2026 paper where section 4 discusses the same topic](https://www.anthropic.com/research/anthropic-economic-index-january-2026-report)

the basic idea of the methodology is to:
1. look at a bunch of conversations where people use Claude to solve some problem
1. measure the efficiency gains for each conversation
1. match each conversation with a standardized task category (e.g. "modifying software to correct errors")
1. compute the speedup for each task category using the median of the speedups across the associated Claude conversations
1. aggregate this up to a global impact number based on relative importance of these tasks to the economy


I'm going to focus on the selection bias from using Claude conversations here:
- the authors rightly point out that this methodology produces an upper bound on impact
- I'm going to further make the observation that this type of methodology would under-estimate the rate of model improvement
    - so that future iterations of this work might invite mistaken pessimism on AI progress



### estimates are an upper bound on productivity gains
this work:
1. groups conversations users have had with Claude into a bunch of 'tasks'
    - via O\*NET's taxonomy, which has 19000 categories of tasks
    - e.g. "modifying software to correct errors"
1. measures speedup for each conversation by asking Claude (see Appendix)
1. for each O\*NET task, uses efficiency gains for these Claude conversations as a proxy for efficiency impact for all problems in the economy associated with that O\*NET task
1. this is obviously not a representative sample: users are more likely to ask Claude about things that Claude can do, even within a task
    - the authors acknowledge this and characterize their estimates as an upper bound (in part) for this reason

it's worth noting that in theory, this can be a *very loose* upper bound
1. as the 2026 paper indicates: 'A debugging task in O*NET could refer to Claude fixing a small error in a function or comprehensively refactoring a codebase'
1. consider this hypothetical:
    1. consider the O\*NET task of "modifying software to correct errors"
    1. suppose Claude can only solve well-specified debugging problems that aren't too hard
    1. users intuitively understand what this category looks like, and mostly just ask Claude about these well-specified-not-too-hard problems
    1. median speedup of Claude for these Python debugging conversations is 5x
    1. => conclude that Claude makes debugging overall 5x faster
    1. whereas in the economy as a whole, the bulk of the things that count as "debugging" are more ambiguous and difficult
    1. so, this 5x number could be a quite major overestimate: it's 5x for a small subset of this O\*NET debugging task, and 0 for everything else
1. if the tasks were quite fine grained, this would be less of a concern, but they're often quite coarse
    - e.g. the authors mention that this debugging O\*NET category accounted for 6% of Claude usage

this is a pretty deep problem that feels hard to solve: I'm sure the authors would have taken a different approach were it available
- the most direct approach would be to sample problems from the economy, rather than from Claude conversations
- I'm not sure anyone knows how to do this, which seems hard for both theoretical and practical reasons
    - i.e. how do you sample a problem from the economy?  just pick a random person at a random company and ask them to tell you what they're doing at that moment?
    - i.e. what even constitutes a 'problem'?


### the flip side: growth in this measure over time would under-estimate rate of progress
1. consider this follow-up hypothetical to the example above
    1. again, consider the O\*NET task on "modifying software to correct errors"
    1. Claude 5 comes out, and it can solve debugging problems that are much more ambiguous & difficult
    1. users start using it on these new problems they couldn't before
    1. these new problems get a 5x speedup, just like the old debugging problems
    1. estimate of speedups for the O\*NET debugging task stays unchanged at 5x, despite major capability improvements
1. so, it's possible for such an approach to measuring productivity gains to vastly underestimate true progress
    - I think this is a pretty realistic concern
    - intuitively, if a problem can be done by AI, then going from human->AI is a huge speedup, but model improvements might push this much less (there might even be slowdowns due to e.g. longer reasoning)
    - so, as models improve, the main axis of improvement is on the set of problems within each O\*NET task the model can handle, rather than incremental speedups for tasks that the older model generation could already do
1. given how much interest there is in, e.g. the METR time duration eval, my expectation is that people are going to be interested in interpreting this kind of measure in that way, which could lead to quite misleading conclusions




### appendix: this analysis is pretty fun
1. so, this paper estimates time savings for each conversation by asking Claude about how much impact it thinks Claude had on speeding up that conversation
1. Claude thought that on average, it sped things up by 80%, which then gets aggregated up and distilled into an exec-friendly soundbite like **"Claude has the potential to double US labor productivity growth"**
1. this has great meme potential:

![linear]({{ "/assets/images/obama_claude.jpg" | absolute_url }})

though I do think doing something like this was probably the correct decision, given how quickly the field is moving:
- frontier AIs are probably the best distillation of all human knowledge that we have
- so if you don't know something, maybe just ask it to fill in the gaps, acknowledge it, and move on?
- instead of spending 3 years on a more robust analysis that passes academic journal standards, but is already irrelevant when it's done
