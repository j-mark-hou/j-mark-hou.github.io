---
layout: post
title:  "Building decentalized institution"
date:   2018-12-18 20:00:00 -0400
categories: philosophy
---


The recent surge of general interest in blockchain has resulted in my having many conversations with people about building decentralized institutions.  

Here, I'll:
- Define institutions and give some examples
- Make two straightforward-but-underappreciated points:
    - Decentralized institutions won't be that intelligent.
    - Institutions that do desirable things will probably be bad at surviving.
- Vaguely discuss some implications for actually building decentralized institutions.


### 0. Background
#### 0.a. Institutions
We're often interested in doing some thing.  So, it would be nice if we could build an institution that:
1. does the thing (Implementation) 
2. for a long time (Survival)

These two conditions provide a trivially broad definition of institutions that we'll use here, in order to draw attention to commonalities among all types of institutions:
- **Institution** := a wrapper that implements some behaviors, minimally survival.

Examples:
- Some 'designed' institutions that explicitly implement some intended behavior:
    - A guard dog is an institution that implements property protection, survives by compelling owner to give it food / shelter.
    - Google is an institution that implements online search, survives by selling ads associated with its search content.
    - USA is an institution that implements some vaguely defined set of 'American interests', survives by appropriating a portion of the economic activity occurring under its purview to fund defense.
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
            - Compare with central planning, which requires e.g. a literal central Walrasian auctioneer running tatonnement.
        - DNA uses decentralized sexual reproduction to continually optimize itself for reproduction.
            - Compare with intelligent design, which requires a literal god to design animals for particular purposes.
        - Laws of physics define local rules of interation, which then aggregate up to global phenomenon.
            - Compare with a video game world, where global phenomena are centrally defined in code, with local behavior following as a consequence.
- But these decentralized institutions are all major forces of nature, rather than human implementations.
- That is, we don't know how to build decentralized institutions.
    - Blockchain is hype because it offers a glimmer of hope on this front.



### 1. Decentralized institutions won't be that intelligent
Let's define 'intelligence' as the ability to quickly optimize against unforeseen circumstances.
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
- Two examples of this model:
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
    - But, serious AI is still quite far away (I'm not optimistic about neural networks being *that* universal of a function approximator).
    - And all of our current methods are too rigid / brittle to stand up to concerted human intelligence.



### 2. Institutions that do desirable things will probably be bad at surviving
- Trivially, if you want to maximize some combination of Implementation and Survival, this will result in a (weakly) lower performance on Survival than optimizing purely for that.
    - Absent some theory telling us why this constraint should be generically non-binding.
    - Which would be quite surprising.
- Some examples of tension between Implementation and Survival:
    - (Note: all of these examples are somewhere between highly speculative and irresponsibly naive, but should serve to fix intuition.  Please don't take them too seriously!)
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
    - Capitalism and poverty:
        - Desired goal to provide overall economic welfare.
        - Must incentivize people to actually work to provide stuff.
        - Thus, safety net must not be too generous.
        - Results in some number of people being quite poor despite plentiful resources.
    - Biology and pain:
        - Desired goal of providing a pleasant life to all organism.
        - But, in order for the DNA to survive, it must be able to motivate organisms to survive and reproduce.
        - Use pain to motivate organism to avoid stuff counter to these goals.
        - Results in some number of organisms having quite painful lives.

- Heart of the issue:
    - Survival is (tautologically) a minimal condition for any institution to exist.
    - Tendency for things that are not purely optimized for survival to not survive.
    - Implementation of some desired behavior will probably handicap the institution on the Self-Propagation front.
- So, must be careful that:
    - Institution doesn't die.
    - Institution doesn't wiggle itself away from Implementing the desired outcome.


### 3. Some implications for building decentralized institutions
- The above two points points have some implications for what institutions we might hope to build and how we might go about building them. 
- Relative to the last two sections, my thinking is on this is relatively more imprecise.
    - As in, I just don't concretely understand the mechanics of building decentralized institutions.
        - Though I think this a general problem for our species as a whole, rather than just me.
- Hopefully, some of these points are still interesting.

#### 3.a. In what situations could decentralized institutions be useful?
- Incumbent parties are extracting a lot of value / imposing a lot of inefficiency, to the detriment of the rest of the market.
    - A decentralized institution could presumably more easily commit to not extracting value.
    - Many blockchain projects seem to be motivated at addressing this sort of situation.  
    - Overall, this point seems to be understood fairly well.
- The problem setting has some natural barriers to entry, e.g. network / information effects.
    - Decentralized institutions that implement some desirable property will typically be not so great at survival, so that it will need some sort of exogenous edge in order to not be out-competed by more adaptive centralized institutions.
    - This setting is pretty correlated with settings where incumbents are able to extract significant rent.
- The problem feels like it has a pretty 'natural' decentralized implementation.
    - The more hacky the decentralized implementation is, the more it feels like there will be a bigger cost in Survival/Implementation that needs to be paid.
    - Overall, we don't really know much about building decentralized institutions, and it doesn't seem like just anything can be implemented in a decentralized manner.
    - Many blockchain projects seem to ignore this, instead opting for "$ARBITRARY_THING, but on the blockchain".
        - This strategy of picking a random problem and hoping that it has some decentralized implementation may have made sense in the late 2017 / early 2018 funding environment, but it's unclear how successful this approach will be.
        - Maybe at some point we'll have some Church-Turing-style theory that tells us we can generically implement anything decentralizedly, but that seems at least far away (and probably isn't true).
- The problem setting is fairly static and well understood.
    - Because building intelligent decentralized institutions seems pretty fundamentally hard, it's probably better to focus on building dumb ones.  Such institutions obviously not work well in fast evolving environments.
    - Many blockchain projects seem to ignore this constraint.  E.g. projects of the form "$TRENDY_CENTRALIZED_STARTUP, but on the blockchain" 
        - These trendy centralized startups tend to operate in somewhat newer, less well understood environments.
        - So there's probably significant work that needs to go into discovering the right approach for the environment.
        - Even after converging to a correct solution, the process of extracting rents might require a long period of innovation before it becomes sufficiently mechanical to easily decentralize.

#### 3.b. Some challenges
- We don't really know very much about how to build decentralized institutions.
    - Making great progress here will likely require long-term financial and cultural commitment.
    - It's not entirely clear if there's enough appetite for that, given that much of the recent crypto hype has been driven by a get-rich-quick kind of mentality.
    - Hopefully, the current correction stabilizes interest in the space at a lower-but-still-significant-enough level.
- The work of actually building and rolling out a decentralized institution can currently only be done by centralized institutions.
    - We *certainly* don't know how to build decentralized institutions that can reproduce themselves.
    - Thus, the success of these decentralized institutions in the near term critically depends on the centralized development organizations being honestly interested in seeing the decentralization through to the end.
    - Again, some questions here, as many projects in the space seem to be too focused on short-term gain rather than serious long-term work.
- There are many centralized institutions that could be unwilling to cede power.
    - It's not entirely clear on where to find situations that won't face significant challenges of this form.
    - Maybe rely on the same sort of mechanism as regular startups: hope that the incumbent is too slow to respond.
        - This is more difficult for decentralized institutions, as building one is quite hard and will almost certainly take longer than building a centralized institution instead.
    - Or, maybe there are certain strategic situations in which centralized institutions both benefit from a decentralized solution as a form of e.g. 'making peace', if they're currently engaged in a costly both-lose equilibrium.