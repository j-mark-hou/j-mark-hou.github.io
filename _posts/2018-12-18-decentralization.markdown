---
layout: post
title:  "Institutions, decentralization, blockchain"
date:   2018-12-18 20:00:00 -0400
categories: soft
---

The recent surge of interest in blockchain has resulted in my having many conversations with people about building decentralized institution.  

Here, I'll:
- Make two straightforward-but-underappreciated points:
    - Decentralized institutions probably won't be that intelligent.
    - Institutions that do stuff we like will probably need some help staying alive.
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
- Blockchain relevant as a way to potentialy build highly decentralized institutions.
