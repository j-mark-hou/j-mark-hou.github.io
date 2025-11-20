---
layout: post
title:  "per-capita GDP is a terrible metric for AI progress"
date:   2025-10-11 00:00:00 -0700
categories: statistics, machine learning
---

TLDR: you don't want a metric that goes to infinity in the case of human extinction



There's a fun graph in this [FT article](https://www.ft.com/content/60dfa917-c5e6-4b9b-9cdb-a30692a29527), which is from a Dallas Fed paper on what might happen to per-capita GDP growth with AI.  The point the authors make is that there's a lot of potential upside as well as downside: the future could be quite good (very fast per-capita GDP growth in the "end-of-scarcity" case), or quite bad (per-capita GDP goes to 0 in the human extinction case)

The problem is that the graph is wrong?  GDP growth should also go to infinity in the human extinction case?

`per-capita-GDP = (amount of stuff produced by economy) / (number of humans in existence)`

If skynet produces a bunch of nukes that then results in human extinction, the top stays nonzero (>0 nukes) but the bottom goes to 0 (0 humans) = infinity?

So I've gone ahead & modified the graph from the FT article to more accurate reflect this point:

![linear]({{ "/assets/images/aigrowth_mod.jpg" | absolute_url }})

In conclusion: instead of per-capita GDP growth (which actively promotes human extinction), maybe just focus on overall GDP growth (which is merely indifferent to it). 