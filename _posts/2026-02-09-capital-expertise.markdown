---
layout: post
title:  "externalization of expertise"
date:   2026-02-10 00:00:00 -0700
categories: AI
---

TLDR: job expertise lives in peoples' heads today, whereas I expect it'll be externally stored in the future, leading to major economic impact even if AI merely gets good at extracting expertise from video data without being able to do the job itself



1. here's a model of white collar work:
    1. employees generally build expertise as they work a job
        - e.g. knowing the other people in the company and how to work with them
        - e.g. understanding the nuances of what 'doing a good job' means for your job
        - e.g. optimizing your workflow in various ways that's not ex-ante obvious
        - e.g. building proficiency with the tools needed for your job
    1. employees get paid more once they develop this expertise

1. here's an alternative model of how it could work, which I will call the **"work-trace model"**:
    - "work-traces" get stored in a database, i.e. every interaction the employee has with a spreadsheet, email client, documents, code, etc.
        - these may be e.g. literal screen recordings of every second of the work day, or something more efficient
    - the work-traces get used to train employees / AI to do these tasks
    - (note: this has a lot of overlap with the 'context graph' discourse that's been ongoing on B2B AI Twitter recently, see e.g. [this tweet](https://x.com/JayaGup10/status/2003525933534179480) or [this follow-up](https://x.com/akoratana/status/2005303231660867619))

1. so why doesn't white collar work already work this way today?
    1. it's hard to distill & store this expertise for easy future usage
        - like, the expertise exists in the head of the employee who develops it, and it's remarkably difficult to extract this information and give it to another employee (i.e. even with extensive mentorship, it often takes years for an apprentice to get close to the skill level of the master)
        - you can write down some of this in text, but there's a lot that's hard to verbalize
    1. it's quite expensive
        - often, you need to have built some expertise in order to extract further expertise
            - e.g. you need to have a mental model of the job's workflow, in order to understand where on the screen to look, and what's the crucial bit of information that's on the screen about how to do the job a bit more efficiently
            - and so, someone who doesn't already have n-1 pieces of expertise might find it quite difficult to extract the n-th piece
        - so doing this might require that every employee have someone shadow them
    1. 

1. why I expect this to happen in the future:
    1. it's becoming increasingly feasible:
        - it might be possible within months/years to just have a neural network watch the entire worktrace and learn from it?
            - expertise is in principle just a function of the entire history of interactions between the employee and the job environment
            - my impression is that, for most white collar work, it's not particularly difficult to extract this expertise once you see the work-trace data
        - the neural network is also an extremely effective way of storing this kind of expertise for easy extraction later
    1. there are real efficiency gains
        - having the expertise externalized makes it easier to scale up (e.g. train more employees or AI to do the task), and can increase firm output if this expertise is a production bottleneck
        - having the expertise externalized helps others build on top of it, allowing for a shared body of knowledge that gets accumulated over time for compounding efficiency gains, vs having this info siloed and then lost 
    1. it allows firms to pay employees less: if the expertise is externalized, then the employee's bargaining position becomes much weaker & thus they'll appropriate less of the surplus

1. implication: there can be significant economic impact even if AI ends up not being able to replace humans for most white collar work
    1. there will be efficiency gains from having all of this expertise sitting around in a database, which will increase firm income, and thus raise wages (assuming surplus split in proportion to bargaining power)
    1. if the AIs become good enough to extract expertise from work-traces, that would nonetheless reduce workers' bargaining power, leading to overall ambiguous impact on wages
    1. this may create new jobs to innovate on top of the body of company expertise
        - but such jobs would likely be quite a bit different: fundamentally about innovating on the knowledge frontier vs accruing rents from a static body of expertise
        - as in, these new jobs would look much more like R&D rather than the typical kind of white collar jobs that exist today

1. critiques
    1. current frontier AI models are still not particularly good at doing this sort of expertise extraction (based on limited anecdotal evidence)
        - and maybe we just won't get there?
    1. this picture of the future might require some version of continual learning: i.e. if the AI models need to develop some expertise in order to extract further expertise from a work-trace, and this expertise is hard to verbalize & stick in the context window, then you'll probably need to continually update the model that's parsing these work-traces
    1. maybe an AI model that can infer expertise from work-trace data can also just do the job, so thinking about this sort of intermediate state of the world isn't that interesting?
    1. the kind of surveillance capitalism that this future entails might be incompatible with workers' preferences, and thus might be outlawed

