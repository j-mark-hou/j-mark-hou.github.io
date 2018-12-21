---
layout: post
title:  "Institutions, decentralization, blockchain"
date:   2018-12-18 20:00:00 -0400
categories: soft
---

The recent surge of interest in blockchain has resulted in my having many conversations with people about building decentralized institution.  

Here, I'll:
- Make two straightforward-but-underappreciated points:
    - Decentralized institutions won't be that intelligent.
    - Institutions that do stuff we want will need help staying alive.
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
    - DNA is an institution that survives by instantiating organisms and then incentivizing them to produce more DNA.
    - Laws of physics is an institution that survives by... I don't know, it just kind of does?

#### 0.b. Decentralization
- Our primary ways of building institutions have been pretty centralized, e.g.:
    - Dogs (and other animals) appear to have an 'ego' that functions as a centralized control center for the entire animal.
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
    - Certainly, many of the most ancient institutions in our world are decentralized:
        - Capitalism leverages decentralized exchange of goods to converge on fair market prices.
            - Compare with central planning, which requires e.g. a literal central Walrasian auctioneer runing tatonnement.
        - DNA uses decentralized sexual reproduction to continually optimize itself for reproduction.
            - Compare with intelligent design, which requires a literal god to design animals for particular purposes.
        - Laws of physics define local rules of interation, which then aggregate up to global phenomenon.
            - Compare with a video game world, where global phenomena are centrally defined in code, with local behavior following as a consequence.
- But these decentralized institutions are all major forces of nature, rather than human implementations.
- We don't really know how to build decentralized institutions.
    - Blockchain is hype precisely because it offers a glimmer of hope on this front.



### 1. Decentralized institutions won't be that intelligent
Let's define 'intelligence' as the ability to solve ex-ante un-specified problems.
- Currently, only humans and certain other biological life-forms are 'intelligent' in this sense.
- Fundamental problem: our *only existing model of intelligence is centralized*:
    - The 'ego' (:= subjective feeling of being a unified single entity) is just DNA's way of implementing a smart institution that helps DNA self-propagate:
        - DNA creats this 'ego' to be the centralized controlling party.
        - DNA then aligns the ego's incentives with DNA reproduction via coarse controls through pleasure / pain.
        - DNA provides the ego with computational resources to optimize.
        - (Unclear if this is true, but it sounds believable)
    - Corporations bear some strong similarities:
        - Investors centralize control with CEO.
        - Investors align CEO incentives with investors ones via properly structure compensation plans.
        - CEO goes ahead and does optimization.
        - (This is a very stylized description, but the intuition is there)

- There's also plenty of empirical evidence that more decentralized institutions tend to adapt more optimize more slowly:


- Examples of institutions that are less smart:
    - Representative democracy is designed to be slow at everything.
    - Capitalism is pretty slow at solving certain problems (e.g. resource overconsumption)
    - DNA as well.
- So, decentralized institutions probably won't be that smart
    - Artificial general intelligence doesn't seem to be anywhere close to being as smart as people for general optimization purposes.
    - So we're kinda left with trying to implement some way to leverage human intelligence.
    - There's a lot of suggestive evidence that this is hard, e.g.:
        - Observing that every non-centralized human institution we're aware of is slow.
        - Results in social choice theory on how preference aggregation is necessarily fraught with political conflict (which typically causes slowness).
- Fundamental problem: the *only existing model of intelligence is centralized*:
    - Not-entirely-unbelievable story: the subjective feeling of being a self-conscious human (call this thing 'ego') is just DNA's way of implementing a smart institution that helps DNA self-propagate:
        - DNA creats this 'ego' to be the centralized controlling party.
        - DNA then aligns the ego's incentives with its own via coarse emotional controls.
        - DNA provides the ego with computational resources to do whatever optimization it wants.
    - So, connection between intelligence and centralization feels pretty fundamental.
