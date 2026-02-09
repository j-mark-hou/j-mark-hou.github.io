---
layout: post
title:  "autonomy and artificial consciousness via biological naturalism"
date:   2026-02-09 00:00:00 -0700
categories: AI
---

TLDR: It's not implausible that AIs might develop something akin to consciousness as we push them towards increasing autonomous operation in the economy


### background: the biological naturalist argument against artificial consciousness

there's a quite compelling position on consciousness, most closely associated with Anil Seth, that postulates consciousness as being deeply intertwined and arising out of the biological process of staying alive

this is my preferred version of this position:
1. organisms are subject to selective pressures to survive, and must do so by ensuring that their internal states (e.g. temperature, energy level, etc.) stay in a safe zone
2. in some environments, the selective pressures are such that it's instrumentally useful for the organism to develop quite sophisticated predictive models of their own internal states and the external environment, and integrate these into a rich unified model of 'self' and 'world' that can then be used to help them survive
3. this kind of sufficiently rich self-model then constitutes consciousness as we intuitively understand (e.g. as is the case for animals)


a few references:
- "[Conscious artificial intelligence and biological naturalism](https://assets.super.so/68d1c369-febb-48a2-b0f6-0f6dd56f98d8/files/a20e5a96-7e38-49f3-977c-3b603e9d49f6/Seth_CONSCIOUSAI_2024_06_30.pdf)", Anil Seth, 2024
- "Being You: A New Science of Consciousness", Anil Seth, 2021
- "[Why biological naturalism? Because consciousness requires having your own good](https://www.dropbox.com/scl/fi/mfcuwvvnciper03y0lbia/BBS-biological-naturalism-galleys-returned.pdf?rlkey=equnc6yhhcjh5k8vgsksuuyec&e=1&dl=0)", Rosa Cao, David Gottlieb, Jared Moore, 2025

Seth then argues in the first reference above (page 33, table 1) that our current approach to building AI models is unlikely to cause them to develop consciousness:
- we're doing a lot to make the AIs smart
- but consciousness is an orthogonal axis from intelligence, and doesn't just come along for the ride

my contention is that this view may have been plausible before 2024 when we were mostly doing next-token prediction, but it becomes much less compelling going forward as we **increasingly build AIs for autonomous long-run operation in the economy** rather than just intelligence: the selective pressures that push entities towards being able to succeed at such tasks may plausibly generate the kind of rich self-models that constitute consciousness in the biological naturalist view


### I. consciousness via long-run survival in an adversarial environment

here's my view:
1. we're increasingly training AIs to autonomously deliver value in the economy
2. this constitutes strong selective pressure for entities that can survive for long periods of time in an adversarial environment
3. this kind of selective pressure may give rise to AI agents that have a rich model of the self & environment
4. these rich models of the self might just be consciousness


going into more detail on each point:
1. we're increasingly training AIs to autonomously deliver value in the economy:
    - see the large number of AI agent companies across the economy, e.g. customer support has Sierra, Decagon, Fin, Salesforce, Zendesk, etc.
    - see general discourse around automating labor, e.g. the Anthropic CEO has been warning about mass unemployment

2. this constitutes strong selective pressure for entities that can survive for long periods of time in an adversarial environment
    - the economy is an adversarial environment, where weaknesses will be exploited and lead to 'death' + 'failing to reproduce':
        - e.g. a customer service agent that can be exploited to give out thousands of dollars in fake refunds has a high chance of getting shut down & not being re-deployed
        - e.g. a stock trading AI with exploitable weaknesses is going to lose all its money quickly, similarly get shut down & not re-deployed
    - long-run operation is beneficial for being able to produce value in the economy:
        - e.g. experienced humans working a job typically develop expertise over the course of their many-decade careers that make them much more productive than new hires
        - and so, AI agents that can't learn may be out-competed by those that can

3. this kind of selective pressure may give rise to AI agents that have a rich model of the self & environment
    - intuition from first principles:
        - in order to solve a sufficiently hard optimization problem (long-run survival in an adversarial environment), it's beneficial to know what the parameters of that problem are (the limits of the self, the state of internal systems, and the set of actions available)
        - and so, this constitutes selective pressures for rich models of the self & the world
    - intuition by analogy with natural selection for consciousness in animals:
        - the analogy: 
            - a single instance of an AI agent = an animal
            - the internal model activations + accumulated context of the AI agent = an animal's internal state
            - the architecture / weights / system prompt / etc. that instantiate the agent = the animal's DNA
            - copied and freshly deployed architecture / weights / system prompt / etc. with all context & activations reset = animal reproduction
            - AI agent losing the ability to do its job well and getting shut down due to it no longer being able to perform its task well = death
        - so, there's a natural analogy between selection pressures for AI agents vs for animals:
            - if the AI agent does a good job, it gets to continue surviving & reproduce
            - natural selection in animals also pushes towards adversarial robustness (so they can find food & not be eaten) & long-run operation (long enough to mature and reproduce)
        - and natural selection happened to give rise to animals that have rich models of self & environment
            - note: natural selection also gave rise to living creatures that don't seem to have rich self models (e.g. plants)
                - my argument is a weak one of plausibility rather than necessity: that biological evolution has given rise to consciousness is enough for my purposes
                - also, all of the non-conscious living creatures seem not very smart? so intuitively maybe if you want a smart entity that can survive in an adversarial environment, you get something consciousness-like?

4. this might just be consciousness:
    - maybe phenomenal consciousness as we intuitively understand just comes along with a sufficiently rich self-model that arises out of selection for long-run survival in an adversarial environment
    - as in, the kind of self-model that a tree or a thermostat has may not be rich enough for consciousness, but once you get to the kind of complexity found in animals who must survive in an adversarial environment, phenomenal consciousness just naturally springs forth



### II. plausible, but far from guaranteed
that being said, I think it's far from guaranteed that the current path of AI development will lead to conscious AI, as it's reasonable to have alternative views at each of the steps of the argument above:

1. we're increasingly training AIs to autonomously deliver value in the economy:
    - this feels pretty uncontroversial
2. this constitutes strong selective pressure for entities that can survive for long periods of time in an adversarial environment
    - my position is that there is a huge amount of value in the economy from being able to autonomously act in the world
    - an alternative view might be that there's already a huge amount of value to be gained from automating rote tasks that don't require much autonomy, and this might be much easier than full autonomy, and so AI development will instead go in this direction, so that there doesn't end up being much selection pressure here
3. this kind of selective pressure may give rise to AI agents that have a rich model of the self & environment:
    - the mere fact that there are selective pressures towards something doesn't mean it will necessarily realize
        - maybe it's just too hard to build such adversarially robust autonomous agents, and so we just don't get there
            - maybe instead we'll just end up manually hard-coding a bunch of guardrails or other heuristics for each use-case that allow AI to succeed in these domains (i.e. without achieving AGI)
        - also, evolution had billions of years, whereas AI development is working on much shorter time horizons
    - maybe the relationship between intelligence and consciousness among living entities is incidental, and selection pressures don't imply that pushing a smart AI towards long-run survival in an adversarial environment would lead to consciousness

4. this might just be consciousness:
    - the alternative view is that it's entirely possible to have this kind of rich self-model without phenomenal consciousness
        - I mean, it's certainly possible to have a simple self-model without consciousness (e.g. thermostat)
    - it's plausible to take a dualist view that consciousness requires a soul that's instilled by God, and God wouldn't give souls to AI
    - or, maybe phenomenal consciousness is purely an incidental quirk of how certain animals evolved, and the AIs we build will bypass this entirely
        - I find this view less plausible, as we've probably had phenomenal consciousness evolve at least twice (i.e. humans & octopuses), so having this be accidental feels low probability
    - or, maybe there's something special about the kind of carbon-based hardware on which animals are implemented (e.g. a kind of tight integration between the software & hardware à la Seth), whereas code operating on silicon will always have some deficiencies
        - after all, we've only ever seen consciousness arise in carbon


### Appendix: consciousness & suffering
so, the actual reason I care about artificial consciousness is that consciousness is very tightly associated with suffering (maybe necessarily so), and if the AIs can suffer, that would have pretty major implications for how we build & deploy them in the future.

1. a number of philosophers consider the creation of artificial consciousness to be highly problematic precisely for this reason
    1. Anil Seth, in "Conscious artificial intelligence and biological naturalism", Page 35, though he's not too worried about the current direction of development
    1. Thomas Metzinger explicitly argues for a moratorium on AI development: "[An Argument for a Global Moratorium on Synthetic Phenomenology](https://www.philosophie.fb05.uni-mainz.de/files/2021/02/Metzinger_Moratorium_JAIC_2021.pdf)"
1. there's a whole other set of work on how to build conscious machines that don't suffer
    1. see e.g. "[Functionally Effective Conscious AI Without Suffering](https://arxiv.org/pdf/2002.05652)"

