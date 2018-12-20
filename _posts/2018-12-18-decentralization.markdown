---
layout: post
title:  "Institutions, decentralization, blockchain"
date:   2018-12-18 20:00:00 -0400
categories: soft
---

The recent surge of interest in blockchain has resulted in my having many conversations with people about building decentralized institution.  

Here, I'll:
- Make two fairly straightforward points on decentralized institutions:
    - Decentralized institutions probably won't be that intelligent.
    - Institutions that do stuff we like will probably need some help staying alive.
- Discuss implications for what sorts of decentralized institutions we might expect to build.


### 0. Background
#### 0.a. Institutions
We're often interested in doing some thing.  So, it would be nice if we could build an institution that:
1. does the thing (Implementation) 
2. for a long time (Survival)

These two conditions provide a trivially broad definition of institutions that we'll use here, in order to draw attention to similarities:
- **Institution** := a wrapper that implements some behaviors, minimally survival.

Examples:
- Some 'designed' institutions that explicitly implement some intedend behavior:
    - A guard dog is an institution that implements property protection, survives by compelling owner to give it food / shelter.
    - An engineer is an institution that implements building-some-product, survives by compelling company to give them money.
    - Google is an institution that implements online search, survives by selling ads associated with its search content.
    - MIT is an institution that implements research/teaching, survives by soliciting donations / applying for grants.
- Some 'natural' institutions where it's unclear if they implement anything (beyond survival):
    - Capitalism is an institution that survives by incentivizing people to engage in market transaction / wage war on other people who don't engage in market transactions.
    - Christianity is an institution that survives by incentivizing people to accept certain beliefs / tell other people to accept similar beliefs.
    - DNA is an institution that survives by creating organisms and then incentivizing them to produce more DNA.
    - Laws of physics is an institution that survives by... I don't know, it just kind of does?

#### 0.b. Decentralization
- Our primary ways of building institutions have been pretty centralized, e.g.:
    - Dogs are centralized institutions that are pretty good at survival, and can implementing a restricted set of tasks.
    - Humans are centralized instittuions that are pretty good at survival, and can implementing a somewhat less resticted set of tasks.
    - Companies are somewhat less centralized institutions that are quite good at survival, can implement an even larger set of tasks.
    - Countries that  representative democracy 
    - Less centralized forms (e.g. representative democracy) still have elected officials with significant power.
- This leads to some weaknesses on the two points above (Implementation and Self-Propagataion)
    - Centralization often allows the people at the center to enrich themselves at the expense of others (weakness in Implementation of desired outcome).
    - Centralization often leads issues with robustness due to single points of failure (weakness in Self-Propagataion).
- Decentralization would address both of these weaknesses, though it has many other issues (that we'll discuss below).
- Blockchain is relevant here because it *might* offer a way to build highly decentralized institutions.
