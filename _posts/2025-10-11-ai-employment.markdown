---
layout: post
title:  "is AI actually replacing younger tech workers?"
date:   2025-10-11 00:00:00 -0700
categories: statistics, machine learning
---

TLDR: a more mundane explanation for why more AI-exposed sectors are seeing a decline in younger workers: lower overall hiring + the younger workers get older


### I. context
this 2025 August paper from the Stanford digital economy lab has gotten quite a lot of press recently: [Canaries in the Coal Mine? Six Facts about the Recent Employment Effects of Artificial Intelligence](https://digitaleconomy.stanford.edu/wp-content/uploads/2025/08/Canaries_BrynjolfssonChandarChen.pdf) 

1. the paper uses proprietary payroll data to show that employment of early-career workers has dropped in AI-exposed sectors:
    - this is Fig.1 from the paper, showing that there's been a systematic decrease in younger tech workers since the release of ChatGPT in late 2022:
    ![linear]({{ "/assets/images/2025-10-10-BrynjolfssonChandarChenFig1.png" | absolute_url }})

1. public discussion has interpreted this as AI replacing younger workers (e.g. because they don't have the harder-to-replace expertise that their older colleagues do).
    - this story is plausible, but it's not the only story
1. here's an alternative story that's also consistent with the data: 
    - maybe tech firms have just slowed hiring, either for AI-related reasons or not (e.g. pullback from post-COVID hiring binge)
    - and if tech isn't hiring, then the number of younger workers is just going to mechanically decrease as they get older
1. so, I'm not sure how informative this analysis is about whether AI is replacing younger tech workers
    - though I think the authors could just do a slightly different analysis to address this concern


### II. a bit more detail on the "mechanical aging out" story
1. here's a timeline of general hiring in tech over the last few years:
    - pre-2022: tech hiring quite a lot, driven by post-COVID stimulus
    - early 2022: end of zero interest rate policy
    - throughout 2022: tech stocks fall, massive decrease in hiring, several waves of layoffs
    - afterwards: continued low hiring
2. here's the alternative story:
    - young worker population (blue line) turns negative, because nobody is getting hired, nothing to offset those who are just getting older
    - older worker populations continue going up (due to younger workers getting older), but at a slower rate due to less hiring
3. the point is that these age groups don't behave the same: the youngest group will mechanically go down in the absence of hiring, whereas the older groups will not


### III. the robustness check may not be sufficient
1. Section 4.4 of the paper has a robustness check, seemingly to address this kind of critique: "One class of explanations is that our patterns are explained by industry- or firm-level shocks correlated with sorting patterns by age and measured AI exposure. For example, one possibility is that young workers with high measured AI exposure are disproportionately likely to sort to firms heavily susceptible to interest rate increases."
2. This is their specification:
    ![linear]({{ "/assets/images/2025-10-10-BrynjolfssonChandarChenEq41.png" | absolute_url }})
    - specifically, the $$\beta_{f,t}$$ are intended to capture the firm-time fixed effects
3. I don't think this addresses the alternative "mechanical aging out" story:
    - $$\beta_{f,t}$$ is uniform across all age buckets
    - but I expect interest-rate-induced hiring freeze shock to disproportionately impact the youngest group, because:
        - 100% of the growth of this youngest group is due to hiring new people
        - for older groups, a fraction of the growth comes from the younger groups aging up
        - based on the pre-2022 growth rates, it seems like all these groups were growing at comparable rates
        - therefore, the hiring rate for the youngest group is higher, and the youngest group would thus be disproportionately impacted by the post-ZIRP tech hiring reduction

### IV. a slightly different analysis would address this
a modified version of the section 4.4 analysis, but explicitly model the age group population transition dynamics rather than doing an industry-time fixed effects that's identical for all age buckets