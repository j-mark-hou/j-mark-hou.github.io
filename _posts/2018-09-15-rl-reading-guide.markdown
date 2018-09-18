---
layout: post
title:  "Reinforcement learning in a few days"
date:   2018-09-17 00:00:00 -0400
categories: machine learning
---


- a few days ago, I decided that I should invest some time in getting up to speed on reinforcement learning
- focus on getting enough intuition to read recent papers
- [this Barto & Sutton book](http://incompleteideas.net/book/the-book-2nd.html) seems to be the default reference, though there are lots of online resources/courses/whatever
- so I went ahead and read this book (+ some other supplementary stuff)
- the experience was quite satisfactory: 
	- the ideas/topics were presented clearly
	- the structure of the book also made a lot of sense
	- the book was quite comprehensive, and there were only a couple places where I felt it necessary to supplement my understanding with papers / blog posts
- in particular:
	- there's not really much in the way of weird math / complicated proofs / difficult intuition that you need to really think hard about / sleep on
	- the stuff that requires more brainpower are mostly long-ish sequences of basic math, and seem sufficiently ancillary to the main intuitions, so that it feels fine to just postpone going through them in detail until some future time
- so, pretty quick to get a basic sense of things
- though actually developing serious intuition about this stuff almost certainly requires significant investment in playing around with a lot of these algorithms / replicating papers / whatever


In the interest of regurgitating these ideas for my own sake / make this learning process a bit easier for other people with an interest in this, I've written up some of my notes from the last few days:
- mostly focused around intuition that I thought was interesting
- most of it is focused on the book
- some blogs / papers for topics not covered in book / covered better elsewhere
- probably won't make sense without reading the associated book / papers / blogs


### Markov decision processes (chapter 3):
- the definition of an MDP is pretty important
- comparison vs bandits: MDPs are explicitly sequential, with actions and states leading to other states, whereas contextual bandits do not have this sort of structure (chapter 2)
	- the example in section 16.7 is a good illustration
- distinction between a distribution model = can easily access the literal probabilities defining the model, and a sample model = can easily draw samples from the model but not easily get the probabilities themselves
	- sample models are much easier to come by e.g. video game simulators
	- see the intro/conclusion of section 8
- 'episode' is a bit of a vague name, so remember that
- state-action values Q vs state-values V:
	- it's much easier to go from Q to optimal action (just argmax) than V (where you need to know transition probabilities)
- policies are modeled as probability distributions for each state, not just a deterministic action for each state
	- more general
	- more continuous parameterization for policy-based optimization methods (section 13)
- bellman equation is pretty important, forms the basis for many of the algorithms in the book

### Dynamic programming methods (chapter 4)
- these methods all require a distributional model for updating
- asynchronous vs synchronous, all work
- the general schema of evaluate policy -> improve policy is pretty important
- dynamic programming methods actually have polynomial time complexity in spite of brute force search over the space of all policies being exponential


### Optimal control vs reinforcement learning
- read this paper: [Reinforcement Learning is Direct Adaptive Optimal Control](http://www.ieeecss.org/CSM/library/1992/april1992/w01-ReinforcementLearning.pdf)
- adaptive = your learning algorithm doesn't know the model
- direct = just learn the value function or policy without detouring through trying to estimate the model
- after learning about Q-learning, come back and appreciate that Q-learning is kind of like an online sampling version of value iteration

### Value vs policy methods for reinforcement learning
- value methods = estimate Q, then derive policy by $$\arg\max_s Q(s,a)$$ or $$\epsilon$$-greedy
- policy methods = directly optimize the policy, possibly without any use of value functions
- everything in this book is about value-based stuff except for chapter 13 (policy gradients)
	- naturally, current state of the art is policy gradients

### Tabular vs approximation
- for value methods: 
	- tabular = if you have small finite states and actions, you treat each $$Q(S,A)$$ separately, and directly update each $$Q(S,A)$$ when you get data (start of part I, page 23)
	- approximation = if you have large/infinite states and actions, you create some function of some parameters $$W$$ and then update the $$W$$ when you get data (start of part II, page 195)
	- in the tabular case, each data point only affects it's own $$Q$$ (which might then propagate upstream to other state-action pairs), whereas in the approximation case you're changing some parameters, which will directly affect $$Q$$ for all states and actions
	- going from tabular to approximate versions of algorithms is often just a matter of swapping the update from each $$Q(S,A)$$ to the weight vector $$W$$, so probably understand the tabular stuff first
- for policy methods: 
	- kind of no way to do this except by parameterizing your policy
	- how to cleverly parameterize a policy:
		- softmax in the discrete case (section 13.1)
		- gaussian in the continuous case (secion 13.7)

### Tabular value methods:
- monte carlo = literally treat like a bandit problem rather than MDP (chapter 5)
	- updates involve literally simulating out an entire episode, so unbiased but high variance 
	- sample efficiency is low, since each $$Q(S,A)$$ is estimated separately
	- **on sample vs off sample**
		- off sample => do importance sampling = just reweighting paths to adjust the weights due to policy differences
		- these ratios are high variance, so updates are higher variance in off-sample
		- but offsample allows us to explore more freely
		- these are pretty central themes for other methods as well
- temporal difference (chapter 6, 7)
	- **bootstrapping** = using previous estimated value function to update instead of sampling the policy to the end
	- bootstrapping decreases variance vs sampling to end of episode, but at the cost of bias (since you're replacing sampled rewards with some constant that hopefully approximates the expectation, but might not)
		- this is a general theme
		- you do something intermediate where you sample $$n$$ periods and then bootstrap, to trade off between bias and varaince
		- you can do something more sophisticated and nicer (in particular, update in an online fashion rather than waiting $$n$$ periods) where you do a weighted average of $$n$$s (eligibility traces, chapter 12)
	- bootstrapping and sample efficiency: example 7.4 on page 147 to fix intuition
	- **Q-learning** is nice because it's off policy but doesn't require any of this weight adjustment nonsense (in the 1-step case)
- planning (chapter 8):
	- if the model itself is easy to learn, it's more efficient to just use your data to learn the model, and then use the model to generate Q, rather than using the data directly to generate Q
	- actually, you can use the data to do both (Dyna-Q)
	- sampling may be preferred to averaging because it focuses attention on things that are actually likely, at the cost of extra noise
		- generate theme of optimizing stuff subject to computational constraints is important
	- decision-time planning: 
		- instead of using planning to improve Q, use it to literally plan actions
		- **monte carlo tree search** is a thing
			- probably search on google for some more intuition, the exposition here is abit too general
			- or just ignore this for now and come back when you're reading the alphago example in chapter 16, as that is much more concrete

### Approximate value methods (chapters 9, 10, 11)
- least squares approximation objective, relation to supervised learning
- monte carlo gradient descent = literally supervised learning
- semi-gradient updates in TD = using bootstrapped value function in the $$y$$ instead of the full
	- again, lowers variance but potentially at the cost of variance
	- kind of... super questionable?
	- like you can imagine feedback loops where your value function starts out being kinda wrong, which motivates the updates to make the Q function even more wrong, etc.
- linear models have nice theory, but who cares
- neural network approximators people use in state of the art stuff
	- for the most part you can probably just black box all of this and treat NNs as just some complicated nonlinear mapping
- some complications for continuing MDPs that never end, but none of the recent problems that I've heard about fall in this category, so I just kind of ignored all of it?
- **deadly triad**, and why reinforcement learning with function approximators is hard
	- consider in context of the Deep-Q learning atari stuff

### Policy methods
- general points:
	- policy methods have a much easier time dealing with continuous / large action spaces:
		- in value methods, you derive policy from Q-value by taking an $$\arg\max_a Q(s,a)$$
		- this is generally hard if you have many actions
	- policy methods can exhibit better stability
		- the policy-from-Q argmax is discontinuous, so even small changes in your parameterization of Q-value can lead to big changes in policy
		- this seems like it would make things unstable
		- policy methods, you're directly modeling the probability of each action via some differentiable function, so by def continuous
		- recent stuff like [trust policy policy optimization](https://arxiv.org/abs/1502.05477) that guarantee steps are not too big
- policy gradient (chapter 13):
	- policy gradient theorem: 
		- final form of the policy gradient (equation 13.5 on p.326) is for the no-discounting case, so if you're confused about why there are stationary distributions in that expression, that's why
		- original paper has the proof in general [Policy Gradient Methods for Reinforcement Learning with Function Approximation](https://papers.nips.cc/paper/1713-policy-gradient-methods-for-reinforcement-learning-with-function-approximation.pdf)
		- but whatever, who cares, the point is that this derivative is easy
	- question of using Monte-carlo sampling (REINFORCE) or some bootstrapping (actor-critic)
		- note that for actor-critic, you need to keep an updated $$V$$ function via some on-policy policy evaluation algorithm (e.g. TD learning), since you're sampling data according to the current policy
- evolutionary strategies: 
	- [Evolution Strategies as a Scalable Alternative to Reinforcement Learning](https://arxiv.org/abs/1703.03864)
	- apparently, you can do this completely trivial thing and get state of the art performance on a bunch of stuff
	- ?????

### Applications (chapter 16):
- Atari deep-Q-learning
	- probably also just read the paper [Human-level control through deep reinforcement learning](http://web.stanford.edu/class/psych209/Readings/MnihEtAlHassibis15NatureControlDeepRL.pdf)
	- note that deadly triad applies here
	- get good convergence via experience replay and not updating the target too often
	- not a single robot that plays all games, but single algorithm that trains a different robot for each game
- AlphaGo
	- monte carlo tree search is important, might make more sense in context than abstractly
	- interesting to see the various hacked-together parts based on human play
	- interesting to see how they these got removed in AlphaGo zero
- OpenAI Dota 
	- see here: [https://blog.openai.com/openai-five/](https://blog.openai.com/openai-five/)
	- nontrivial amount of [human intuition in reward shaping](https://gist.github.com/dfarhi/66ec9d760ae0c49a5c492c9fae93984a)
	- nontrivial amount of [human intuition in defining the features / actions](https://d4mucfpksywv.cloudfront.net/research-covers/openai-five/network-architecture.pdf)
	- quite a lot of work on the training infrastructure