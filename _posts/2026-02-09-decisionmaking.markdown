---
layout: post
title:  "corporate decision-making and the company brain"
date:   2026-02-11 00:00:00 -0700
categories: AI
---

TLDR: corporate decision-making today is highly inefficient due to human cognitive constraints, and in the future this function might be largely performed by a "company brain" (with human oversight)


### limitations of the present
here's a pretty typical example of how corporate decision-making works at a big company (based on true events):
1. CEO of the company needs to make a decision, tasks it to the chief revenue officer (CRO)
1. CRO staffs one of his VPs on it, who then has one of her Directors to pull together an analysis
1. the Director gets their team together, where each team member analyzes some data, or does some market research, or interviews some people
1. the team members put together a presentation for the Director, who provides some feedback based on their understanding of the world & of the preferences of the VP & CRO & CEO (repeat a few times)
1. the Director & team then takes the presentation to the VP, who provides some feedback based on her understanding of the world & of the preferences of the CRO & CEO (repeat a few times)
1. the VP & Director & team then take this to the CRO, who provides some feedback based on his understanding of the world & of the preferences of the CEO (repeat a few times)
1. the CRO then talks to the CEO & CFO, using this presentation as a basis, maybe ask for some more follow-up analyses (go back to step 3, repeat a few times)
1. CEO makes a decision, based on his updated understanding of the world 

this is a particular solution to an optimization problem, which is just to pick the utility-maximizing decision given available info: 

$$\displaystyle\arg\max_{\text{decision} \in \text{options}}\mathbb{E}[\text{utility}(\text{decision}) \mid \text{best model of the world, all available information}] $$

on the basis of this formulation, we can discuss some inefficiencies with how corporate decision-making works today:
1. "all available information": everyone in this process has an imperfect subset of the relevant information, and communicating this is slow and lossy
1. "best model of the world": the models largely live in various peoples' heads, and these heads are pretty constrained in size, and so the model may be quite wrong or lacking in nuance
1. suboptimal computation of $$\arg\max\mathbb{E}$$: humans are very cognitively limited, and thus can only contemplate a quite limited number of possible actions & potential outcomes
1. suboptimal utility model: company executives are bottlenecked on their ability to deeply understand the preferences of their shareholders, and so their model of what utility function to optimize may be suboptimal
1. speed: human communication is very low-bandwidth, and this process is highly bottlenecked on communications 

the reason that things are the way they are is entirely due to human cognitive limitations:
1. if the CEO could just understand everything relevant to the company, ingest all pieces of information, and make decisions that way, he would do so
1. but he is cognitively constrained, and must allocate his mental faculties to the highest priority stuff
1. this means delegating some tasks to a CRO
1. who then delegates things to a number of VPs, and so on and so forth



### corporate decision-making might look a lot more organismic
here's how AIs stack up vs humans on these constituent sub-parts of decision making:
1. accounting for "all relevant information":
    - LLMs are already able to ingest and process way more information way more quickly than humans
    - they're also getting increasingly good at integrating this information to derive relevant conclusions (e.g. see how GPT5.2 has been able to solve a number of Erdos problems by finding relevant lemma proofs in past literature & putting them together)
1. computation of $$\arg\max\mathbb{E}$$: 
    - machines are parallelizable in a way that humans are not, and so this sort of optimization procedure can be arbitrarily scaled, vs a human who has to do everything sequentially
1. speed:
    - machine communication can be much higher throughput than human communication
    - also, there's less need to communicate, because the models of the world & utility function aren't distributed across people
1. "best model of the world":
    - here's a place where humans might still have an advantage: the implicit world models that AIs build may still be bad
    - but there's a significant probability that AI continues improving here
1. "utility()":
    - AI may be able to integrate a lot more information about preferences of the company's shareholders, and thus develop a more coherent notion of what the correct utility function to optimize should be
    - but, alignment issue may loom larger here: humans might be better equipped to understand & optimize for the preferences of other humans


on the basis of this, here's a view of how the future might look:
1. the best model of the world + utility function is externalized into a "company brain" (e.g. implemented as an LLM), rather than implicitly living in the heads of a bunch of senior executives
1. this company brain is hooked up to every possible data feed the company has access to
1. decisions will be made by literally having this company brain think really hard a bunch of times in parallel & then aggregating up the results
1. subject to final oversight by humans, at least in the near term

the role of human decision-makers in this world would be largely to guardrail the company brain:
1. continually evaluating company brain's quality & coherence
1. checking the decisions made by the company brain against their internal understandings of the world
1. (and doing a bunch of tasks not related to decision-making that we're not going to discuss in more detail)


as in: if the corporation is the right entity for achieving certain outcomes in the world, then the optimal way to implement decision-making for this entity is to centralize its cognition, give it access to data, and have it optimize

the resulting entity might look a lot more like a single coherent organism vs the kind of organizations we have today that are very much agglomerations of humans weakly bound together




### some counter-arguments to this view
the core contention above is just that there are various advantages to centralizing decision-making into a company brain vs how things are today, and so we might end up there

but:
1. just because something is better doesn't mean it's going to happen:
    1. maybe the improvement in decision-making speed & quality are kind of minor, and so there's not that much benefit to this company brain approach => limited market pressure to move in this direction
    1. maybe the market is inefficient, due to e.g. incumbents having large network effects or other moats, and the moat zeroes out any pressures to innovate on corporate decision-making
1. maybe it's not even better
    1. it's entirely possible that all the advancements in AI capabilities we've seen only apply to strictly verifiable domains (e.g. math & coding), and corporate decision-making is too unverifiable & will remain a human-specific domain
        - e.g. maybe AI will continue being hugely sample inefficient, and corporate decision-making is an area that requires making correct inferences from very few ambiguous pieces of information => humans continue being essential
    1. maybe alignment ends up being really hard, and it thus becomes infeasible to ever hand off decision-making to a company brain, even with extensive human guardrails