---
layout: post
title:  "Building decentalized institution"
date:   2018-12-18 20:00:00 -0400
categories: philosophy
---

When I was younger, I wanted to be a 'quantitative philosopher of institutions' (whatever that means).  As a result, there were a few years where I spent very large fraction of my time thinking about institutions.

The recent surge of interest in blockchain has resulted in my having many conversations with people about building decentralized institution.  

Here, I'll:
- Make two straightforward-but-underappreciated points:
    - Decentralized institutions won't be that intelligent.
    - Institutions that do desirable things will probably be bad at surviving.
- Discuss implications for what sorts of decentralized institutions we might expect to build.


### 0. Background
#### 0.a. Institutions
We're often interested in doing some thing.  So, it would be nice if we could build an institution that:
1. does the thing (Implementation) 
2. for a long time (Survival)

These two conditions provide a trivially broad definition of institutions that we'll use here, in order to draw attention to commonalities among all types of institutions:
- **Institution** := a wrapper that implements some behaviors, minimally survival.

Examples:
- Some 'designed' institutions that explicitly implement some intedend behavior:
    - A guard dog is an institution that implements property protection, survives by compelling owner to give it food / shelter.
    - Google is an institution that implements online search, survives by selling ads associated with its search content.
    - USA is an institution that implements some vaguely defined set of 'Amercan interests', survives by appropriating a portion of the economic activity occurring under its purview to fund defense.
- Some 'natural' institutions where it's unclear if they implement anything (beyond survival):
    - Capitalism is an institution that survives by incentivizing people to engage in market transaction / wage war on other people who don't engage in market transactions.
    - DNA is an institution that survives by instantiating organisms and then incentivizing them to create more organisms.
    - Laws of physics is an institution that survives by... I don't know, it just kind of does?

#### 0.b. Decentralization
- Our primary ways of building institutions have been pretty centralized, e.g.:
    - Dogs (and other animals) appear to have an 'ego' that functions as a centralized control center for the organism.
    - Google (and other companies) concentrates a lot of power in its executives, though many functions are decentralized throughout the organization.
    - USA (and other democracies) concentrates a lot of power in some elected officials, though typically for short periods of time and subject to popular approval.
- This centralization leads to some weaknesses when it comes to Implementation and Survival:
    - Centralization often allows some parties to flexibly not implement 'desired' outcomes.
        - A guard dog is free to stop guarding the property if it wants.
        - Google can show more ads to increase revenue at the cost of worse search quality.
        - USA's elected officials can try and enrich themselves with taxpayer money.
    - Centralization often also makes these institutions quite brittle:
        - A guard dog typically ceases to exist within ~20 years.
        - Google can be easily shut down by e.g. a government by just removing its servers.
        - USA can be debilitated by e.g. compromising the integrity of powerful elected officials.
- It feels like decentralization could help address these weaknesses.
    - Certainly, many of the longest-lasting and most powerful institutions in our world are decentralized:
        - Capitalism leverages decentralized exchange of goods to converge on fair market prices.
            - Compare with central planning, which requires e.g. a literal central Walrasian auctioneer runing tatonnement.
        - DNA uses decentralized sexual reproduction to continually optimize itself for reproduction.
            - Compare with intelligent design, which requires a literal god to design animals for particular purposes.
        - Laws of physics define local rules of interation, which then aggregate up to global phenomenon.
            - Compare with a video game world, where global phenomena are centrally defined in code, with local behavior following as a consequence.
- But these decentralized institutions are all major forces of nature, rather than human implementations.
- That is, we don't know how to build decentralized institutions.
    - Blockchain is hype because it offers a glimmer of hope on this front.



### 1. Decentralized institutions won't be that intelligent
Let's define 'intelligence' as the ability to quickly optimize against unforseen circumstances.
- Suggestive empirical evidence that higher centralization seems to correlate with higher intelligence:
    - Single engineer overseeing a project can just push product changes immediately, whereas if there are many stakeholders, then lots of communication necessary, need to worry about internal politics, etc.
    - Startups are often able to out-maneuver larger corporations.
        - Less communication overhead and better aligned incentives => startup act more like a single centralized entity.
    - Corporations in general are fairly centralized, as corporate survival requires optimizing against changing market environments.
    - Democratic forms of government are by design quite slow to adapt to novel circumstances, whereas autocracies have the potential to move quickly (e.g. US vs China on energy policy).
    - Military organizations are all highly centralized, as winning wars requires being very adaptive.
- Fundamental problem: it seems like **our only model of intelligence is centralized**, and it's something like this:
    1. Centralize control with a single entity.
    2. Constrain this entity's preferences to be somewhat correlated with desired ones.
    3. Give the entity some resources to do various kinds of optimization.
- Some examples of this model:
    - Corporations:
        - Investors centralize control with CEO.
        - Investors align CEO incentives with investors' via conditional stock grants.
        - CEO goes ahead and leverages company resources to do optimization.
        - (This is a very stylized description, but the intuition is there)
    - The 'ego' (:= subjective feeling of being a single unified entity) could just be DNA's way of implementing a smart institution that helps DNA survive:
        - DNA creats this 'ego' to be the centralized controlling party.
        - DNA then aligns the ego's incentives with DNA reproduction via coarse controls through pleasure / pain.
        - DNA provides builds a brain, gives ego access to do whatever with it.
        - (This is a somewhat fanciful description, but it doesn't sound implausible)
- As a result, intelligent institutions probably need to be built out of aggregates of people.
    - Given some negative results on preference aggregation, this problem is theoretically hard (e.g. arrow, gibbard-sattherwaite).
    - Impossible to construct decentralized preference aggregation rules that satisfy some basic requirements.
    - As a result, decentralized human institutions are almost necessarily fraught with incentive conflicts.
    - Incentive conflicts seem to make institutions less intelligent.
- So we'll probably have to come up with a new model of intelligence...
    - Serious artificial intelligence might be such a model
        - This would allow us to have intelligence without the corresponding incentive issues.
        - Incentive issues is a major reasons for conflict between decentralization and intelligence.
    - But, seriousl AI is still quite far away (I'm not optimistic about neural networks being *that* universal of a function approximator).
    - And all of our current methods are too rigid / brittle to stand up to concerted human intelligence.




### 2. Institutions that do desirable things will probably be bad at surviving
- Trivially, if you want to maximize some combination of Implementation and Survival, this will result in a (weakly) lower performance on Survival than optimizing purely for that.
    - Absent some theory telling us why this constraint should be generically non-binding.
    - Which would be quite surprising.
- Empirically, many examples tension between Implementation and Survival:
    - (Note: these examples are all naive caricatures, but should serve to fix intuition.)
    - Universities and preference for children of alumni:
        - Desired goal of promoting intellectual meritocracy.
        - Need money to self-propagate.
        - Can incentivize alumni to provide funding by cultivating loyalty via looser standards for children.
    - Political lobbying:
        - Desired goal to limit special interest in politics.
        - But, not really feasible to create policies without domain experts' assistance.
        - Have to provide some incentive for domain experts to exist.
        - Thus, allow special interests to extract some rents in exchange for providing domain expertise.
    - Buddhism and reincarnation: 
        - Desired goal to reducing suffering.
        - Natural way to reduce suffering is to have fewer people.
        - Incentivizing followers to not have children is a great way for institution to die out, so can't do that.
        - Thus, this whole weird thing about reincarnation.
        - Unclear if this characterization is accurate, but it doesn't seem totally insane.
    - Capitalism and poverty:
        - Desired goal to provide overall economic welfare.
        - Must incentivize people to actually work to provide stuff.
        - Thus, safety net must not be too generous.
        - Results in some number of people being quite poor in spite of plenty of resources.
    - Biology and pain:
        - Desired goal of providing a pleasant life to all organism.
        - But, in order for the DNA to survive, it must be able to motivate organisms to survive and reproduce.
        - Thus, must cause pain if organism operates counter to these goals.
        - Results in some number of organisms having quite painful lives.

- Heart of the issue:
    - Survival is (tautologically) a minimal condition for any institution to exist.
    - Tendency for things that are not purely optimized for survival to not survive.
    - Implementation of some desired behavior will probably hadicap the institution on the Self-Propagation front.
- So, must be careful that:
    - Institution doesn't die.
    - Institution doesn't wiggle itself away from Implementing the desired outcome.




