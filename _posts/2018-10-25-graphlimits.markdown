---
layout: post
title:  "Graph limits and market equilibrium"
date:   2018-10-25 20:00:00 -0400
categories: math, statistics, economics
---

- current economic landscape is heavily dominated by a few major companies built around large private markets
	- e.g. :
		- Amazon / Alibaba for e-commerce
		- Apple / Google for apps
		- Uber / Lyft / DiDi for transportation
		- Google / Facebook / Microsoft / Amazon for ads
	- so there's been some interest (from e.g. these institutions) on characterizing the equilibrium behavior of large markets
- some relevant strands of work:
	- providing formal foundations for market equilibrium was probably the crowning achievement of classical economic theory
		- this classical work seems to have least partially been motivated by a desire to provide some sort of 'scientific' justification for capitalism (this was the 50s, after all) 
			- thus, focus on abstract markets, intuitively corresponding to nation-level economies
		- focused on characterizing existence / uniqueness / welfare properites of equilibria 
		- based on fixed-point arguments
			- not that useful for actually finding equilibria
	- more recently, algorithmic game theorists have devised various algorithms for computing equilibria of certain markets
		- for some reasonable models of markets, complexity is polynomial in market size (and sometimes even quite fast)
		- but given the scale of the markets of interest described above, often even writing down the entire market is a challenge
	- there's also been some recent work in graph theory on defining / characterizing the limits of graphs
		- some conditions under which some property of a graph will converge as the graph gets big
		- markets are basically just bipartite graphs where vertices are consumers and goods
- so, it feels like you should be able to do something like this:
	1. sample some not-too-small sub-market from your big market
	2. compute equilibrium on this sub-market
	3. equilibrium on the sampled market should be similar-ish to equilibrium on the whole market

I'll walk through a very simple example to provide some intuition on when this process could work, and then discuss how much foundational work remains to be done.


### I. Simple example
We'll be extremely concrete here and focus on a fairly trivial market with no production / only monetary endowments / specific utilities (Fisher market with Cobb-Douglas utilites).
#### I.0. Setup
- goods $$j = 1,...,J$$
	- each good has total supply $$y_j$$
	- in addition, let $$\tau_j\in\{0,1\}$$ denote binary 'type' of a good
- consumers $$i = 1,...,I$$
	- each consumer has total budget $$B_i$$ to spend on stuff
	- utility function 
	$$
	\begin{equation}\displaystyle
	u_i(x_i) = \sum_j\alpha_{ij}\log(x_{ij}), \quad\alpha_{ij}=1
	\label{cbutil}
	\tag{1}
	\end{equation}
	$$
		- a little calculus gives us that, given prices $$p = (p_1,...,p_J)$$, the optimal amount of each item to buy is 
		$$
		\begin{equation}\displaystyle
		x^*_{ij}(p) = \frac{\alpha_{ij}B_i}{p_j} 
		\label{cbopt}
		\tag{2}
		\end{equation}$$
		- thus, in particular, the total fraction of consumer $$i$$'s budget spent on good $$j$$ is just $$\alpha_{ij}$$ *independent of price*
- an equilibrium is defined by prices $$p^*$$ such that supply and demand are equal:  $$\sum_i x^*_{ij} = y_j$$
	- note that because the allocation of money to each product doesn't depend on price
	- so, the market clearing price for each good $$j$$ is just 
	$$
	\begin{equation}\displaystyle
	p^*_j = \left(\sum_i \alpha_{ij}B_i\right)/y_j
	\label{cbeq}
	\tag{3}
	\end{equation}
	$$ 
	- so this market is actually trivial
- **our aim is to figure out how much total money is spent on goods of type $$\tau_j=0$$ in equilibrium**
	- this can be written
	$$
	\begin{equation}\displaystyle
	\sum_{j:\tau_j=0} \sum_ix^*_{ij}p^*_j = \sum_{j:\tau_j=0} \sum_i \alpha_{ij}B_i
	\label{rev0}
	\tag{4}
	\end{equation}
	$$

#### I.1. Equilibrium existence and computation
Equilibrium existence:
- this is trivial because we have closed form expression for the equilibrium price vector
- fairly general cases, classical general equilibrium results give us existences (see Arrow Debreu 1954)

Equilibrium computation:
- again, trivial because we have closed form solution
- more generally, various polynomial time algorithms for doing so:
	- tatonnement-style algorithm in exchange economies where elasticiity of substitution is not too high and consumers are endowed with money (e.g. Cole Fleischer 2008)
	- convex optimization based algorithms in the linear case (e.g. Devanur Garg Vegh 2013)

#### I.2. Sampling
- doing the sum in \eqref{rev0} requires $$O(IJ)$$ operations
- this might be large, in which case we'll probably want to sample
- if e.g. $$J$$ is small, we can just subsample consumers $$i$$ and approximate the fraction of revenue flowing to goods with $$\tau_j=0$$
	- standard LLN implies consistency
- if both $$I$$ and $$J$$ are large, then we'll need to sample in both dimensions
	- ... is this actually a thing that we can do?



### II. Graph limits and parameter testing
#### II.0. Graph limits
There's some quite elegant theory on limits of graph sequences (see Lovasz Szegedy 2004):
- a graph's adjacency matrix is just a symmetric function from $$[0,1]\times[0,1]\mapsto \{0,1\}$$ 
	- discretize the interval $$[0,1]$$ into $$\lvert V\rvert$$ intervals corresponding to the vertices of the graph
	- set the function's value to 1 on a rectangle IFF there's an edge between the two vertices corresponding to the two intervals defining the rectangle
- so instead of talking about graphs, just talk about these functions instead
- it turns out that the right limit objects for these piecewise-constant symmetric functions $$[0,1]\times[0,1]\mapsto \{0,1\}$$ are symmetric functions on $$[0,1]\times[0,1]\mapsto [0,1]$$, which are called **'graphons'**
	- the range $$[0,1]$$ can be interpreted a probability distribution on $$\{0,1\}$$

Some further work (Borgs et. al. 2007) put a norm on this graphon space (in fact, a more general space, as they allow for edge and vertex weights)
- namely, the  **cut-metric**  $$\delta_{\square}$$:
	- for two simple graphs $$G', G''$$ on the exact same (labeled) vertex set:
	$$
	\begin{equation}\displaystyle
	d_{\square}(G'', G') := \max_{S,T\subset V} \frac{1}{\lvert V\rvert^2}\left\lvert e_{G''}(S,T) - e_{G'}(S,T) \right\rvert
	\label{cutdistance0}
	\tag{5}
	\end{equation}
	$$
		- $$e_{G}(S,T)$$ is the number of edges between vertex sets $$S$$ and $$T$$
		- $$d_{\square}$$ is the maximum difference in edge density between any two vertex sub-sets
		- intuitively, this amounts to saying that $$G''$$ and $$G'$$ are 'macroscopically similar', in that no matter which edge subsets you look at, the number of edges is roughly the same
			- macroscopic because everything is scaled down by the square of the number of vertices, so that it's possible for e.g. individual vertices to have dramatically different degrees so long as the total differences are $$o(n^2)$$
		- note that this distance only makes sense for dense graphs, since otherwise this metric would be uniformly zero as the graphs got large
	- for two simple graphs $$G, G'$$ with the same number of vertices, just find the best way to relabel the vertices of $$G$$ to match the vertex set of $$G'$$, and then use the above definition:
	$$
	\begin{equation}\displaystyle
	\delta_{\square}(G, G') :=  \min_{G''\cong G} d_{\square}(G'', G')
	\label{cutdistance1}
	\tag{6}
	\end{equation}
	$$
	where $$G'' \cong G$$ refers to $$G''$$ being some re-labeling of the vertex set of $$G$$ to match the vertex set of $$G'$$
	- this definition can be generalized to graphons by doing something in the same spirit as above, but let's just stop here and use $$\delta_{\square}$$ to refer to this generalized graphon metric
- this cut-metric ends up being the right metric for graphon space, and the paper proves these results:
	- graph convergence as defined in Lovasz Szegedy 2004 is equivalent to convergence in $$\delta_{\square}$$
	- graphon space is the completion of the space of all graphs under $$\delta_{\square}$$
	- graphon space with the $$\delta_{\square}$$-metric is compact (once you collapse graphons into equivalence classes with $$\delta_{\square}=0$$)
	- with high probability, sampling a sufficiently large subgraph of some graph produces a sub-graph that is close in $$\delta_{\square}$$ to the original graph
- these results mean that questions about sampling and convergence of functions of graphs can be rephrased in terms of continuity of functionals on graphon space
	- this is cool


#### II.1. Parameter testing and continuity
- so it turns out that this idea of computing some parameters of large graph by subsampling the large graph and computing the parameter on the subsampled graph and hoping that these are close has a name: **parameter testing**
- the Borgs et. al. 2007 paper gives some very useful results for parameter testing (Theorem 6.1) in terms of continuity in $$\delta_{\square}$$
	- results are only for simple graphs, as opposed to the previous stuff which applied also to weighted graphs
	- the parameter $$f(G)$$ must be real and bounded
- the theorem states that these are equivalent (plus some other things we dont' care about):
	- (a) $$f$$ is testable
	- (d) $$f$$ can be extended to some $$\tilde{f}$$ on graphon space that is continuous in $$\delta_{\square}$$
	- (e.1-e.3):
		- (e.1) $$\forall \epsilon, \enspace \exists \epsilon'$$ such that for any two graphs $$G, G'$$ on the same vertex set with $$d_{\square}(G,G')<\epsilon'$$, we have $$\lvert f(G)-f(G')\rvert<\epsilon$$
		- (e.2) $$f(G[m])$$ converges as $$m\rightarrow\infty$$, where $$G[m]$$ represents the graph obtained by duplicating each vertex of $$G$$ $$m$$ times and adding in all the corresponding edges
		- (e.3) $$\lvert f(G')-f(G)\rvert\rightarrow 0$$ as the number of vertices in $$G$$ goes to $$\infty$$, where $$G'$$ is just $$G$$ except with an additional disconnected vertex
- so, testability is equivalent to continuity in $$\delta_{\square}$$, which is equivalent to some easy-ish-to-check conditions


### III. Testability of market equilibrium: simple example
#### III.1. One specification that is testable
Let's now apply this nice theory of parameter testing to the simple we started off with.  This basically amounts to showing that the type-0 revenue in \eqref{rev0} is a a testable graph parameter.

So let's first represent the simple example above as a graph:
- consumers $$i$$ and goods $$j$$ are vertices
- a consumer has vertex-weight corresponding to its budget $$B_i$$
- a good has vertex-weight corresponding to its supply $$y_j$$
- the edge weight between consumer $$i$$ and good $$j$$ is consumer $$i$$'s valuation of good $$j$$, which is $$\alpha_{ij}$$

As the above theory applies only to simple graphs, we'll make some more constraints:
- in order to get rid of weights for vertices coresponding to goods:
	- let all goods have the same supply, and normalize by total supply $$y_j=1/J$$
- in order to get rid of edge weights:
	- make preference binary so that a consumer $$i$$ either likes or doesn't like a good $$j$$
	- for the goods $$j$$ that consumer $$i$$ prefers, uniformly set $$\alpha_{ij}=1/\mathrm{deg}_i$$ where $$\mathrm{deg}_i$$ is number of goods $$i$$ likes
- in order to get rid of weights on vertices corresponding to consumers:
	- set the budget of consumer $$i$$ to $$\mathrm{deg}_i$$, so that people who like more stuff have more money to spend
	- it might be more natural to give consumers equal budget, but we'll discuss later why this is problematic

This then gives us a simple graph $$G$$ with:
- $$I+J$$ total vertices
- consumer-vertex $$i$$ is attached to good-vertex $$j$$ IFF consumer $$i$$ likes good $$j$$
- there are no connections between consumer-vertices, and similarly for good-vertices

So, now \eqref{rev0} can be written 
$$\sum_{j:\tau_j=0} \sum_i \frac{1}{\mathrm{deg}_i}\mathrm{deg}_i = \sum_{j:\tau_j=0} \mathrm{deg}_j$$, which is just the total number of all edges attached to goods of type $$\tau_j=0$$.  We'll also normalize this by the square of the total number of vertices to construct a graph parameter:
$$
\begin{equation}\displaystyle
R_0(G) = \frac{1}{(I+J)^2}\sum_{j:\tau_j=0} \mathrm{deg}_j
\tag{7}
\label{revparam}
\end{equation}
$$

So we need to show that $$R_0(G)$$ is testable, which we can do via conditions (e.1-e.3):
- (e.1):
	- $$R_0(G)$$ as we've constructed it is literally just the edge density between the sets of good-vertices $$j$$ with $$\tau_j=0$$ and the entire vertex set
	- the condition that \eqref{cutdistance0} be small just says that the edge density between any two subsets of vertices is small
	- which guarantees that the difference in $$R_0$$ between the two graphs will also be small
- (e.2):
	- so we replicate each vertex $$M$$ times 
	- there are now $$M$$ copies of each good-vertex $$j$$ and similarly for each consumer-vertex $$i$$
	- let $$(j,m)$$ represent a good in this new $$G[M]$$ graph, and similarly $$(i,m)$$ for consumers
	- so we have 
	$$
	R_0(G[M]) = \frac{1}{((I+J)M)^2}\sum_{(j,m):\tau_j=0} \mathrm{deg}_{(j,m)}
	= \frac{1}{M^2(I+J)^2}M\sum_{j:\tau_j=0} M\mathrm{deg}_{j} = R_0(G)
	$$
	- so duplicating the vertices $$M$$ times actually keeps $$R_0$$ the same
- (e.3):
	- adding an isolated vertex to $$G$$ will only impact $$R_0(G)$$ by changing $$\frac{1}{(I+J)^2}$$ to $$\frac{1}{(I+J+1)^2}$$
	- this change is clearly negligible as $$(I+J)\rightarrow\infty$$

Thus, it follows that $$R_0(G)$$ is testable, and thus it makes sense to approximate this in a large graph by just taking some $$G'$$ subsampled from $$G$$ and then using $$R_0(G')$$ to approximate $$R_0(G)$$

#### III.2. Other specifications that are not testable
We made some further assumptions to the simple example in order to apply this parameter testing stuff above.  Two of them are maybe a bit unnatural, and they were made because somehow more natural assumptions would have resulted in graph parameters that weren't testable:
1. normalizing revenue by $$\frac{1}{(I+J)^2}$$ in \eqref{revparam}
	- this is kind of like a 'revenue going to type-0 goods, as a fraction of hypothetical total revenue supportable by the market'
	- more naturally, we might be interested in something like 'fraction of total revenue going to type-0 goods, as a fraction of total spending'
		- unfortunately, this parameter is not testable
	- consider this example:
		- every consumer $$i$$ only likes exactly one good, and that good is of type-0
		- so, all revenue goes to type-0 goods
		- now, add in an edge between every consumer $$i$$ and some randomly chosen good of type-1
		- this change makes it so that each consumer now spends half of their income on type-0 goods, so now only .5 fraction of total revenue goes to type-0 goods
		- however, adding in an edge between every consumer $$i$$ and some type-1 only involves adding $$O(\lvert V \rvert)$$ edges
		- so, as $$n$$ gets big, the $$d_{\square}$$ between these two different graphs goes to 0
		- thus, no matter how small $$\epsilon$$ gets, you can find two graphs $$G, G'$$ that differ only in $$\epsilon$$ in the $$d_\square$$ metric, but nevertheless differ significantly in fraction-of-revenue-going-to-type-0-goods
		- so (e.1) fails
	- the crux of the issue here is that the cut-metric scales everything down by the square of the number of vertices
		- so, whatever graph parameter must also be similarly scaled in order to be continuous in $$d_\square$$
2. assigning each consumer $$i$$ a budget proportional to the number of items they like
	- more naturally, we might want to just give every consumer $$i$$ an equal share of the total budget
		- in this case, we wouldn't want to normalize revenue by $$1/(I+J)^2$$ because that would be... uniformly 0 as the graph gets large
		- it turns out this is also not testable
	- consider this example (very similar to previous example):
		- $$1/3$$ of the consumers only like a single item, and that item is type-0
		- now, for every consumers in this $$1/3$$, add a single edge to some item of type-1
		- this only entails adding $$O(I)$$ edges, which gets small as the market gets big
		- however, this $$1/3$$ of consumers will shift half of their spending from type-0 to type-1 goods
		- thus, this moves the revenue share of type-1 goods by $$1/6$$, which doesn't get small as the market gets big
		- so (e.1) fails
	- note that, while the last example relied on the graph being sparse, it's possible in this example for the graph to be dense
		- so long as the remaining $$2/3$$ of consumers have $$\Theta(J+I)$$ edges on average, the resulting graph is dense
	- the key here is that a contingent of consumers with very few edges control a non-vanishing share of the total revenue, so that small changes to the edge count can significantly change the revenue distribution

#### III.3. Can we say anything more general?
We had to trivialize the problem setting to get the testability results.  How can we relax these assumptions?
- consumer preferences $$\alpha_{ij}$$ are binary
	- more generally, we'd prefer to have this be a real number
		- unfortunately, this would make the corresponding graph have edge-weights
		- presumably Borgs et. al. 2007 would have characterized parameter testing for weighted graphs rather than just simple graphs if it was easy
		- so probably it's not
	- or even more generally, we might want to have each edge be some function from some compact function space
		- Lovasz Szegedy 2010 defines graph limits for 'compact decorated graphs' where edges can be associated with elements in a general compact space
		- but I don't think there's even an equivalent to the cut-metric defined for this stuff yet?
		- so surely quite a long way to go here before we can do anything
- consumer budgets are proportional to how many items they like
	- it seems like having an upper bound on how budget proportional to how many products a consumer likes will be necessary
	- but maybe we'll want each consumer to have their own separate budget-to-degree ratio
	- this would involve adding vertex-weights to the graph
	- again, probably nontrivial
- cobb-douglas utilities
	- the specification in \eqref{cbutil} trivializes the problem by making spending independent of price
	- this allowed us to turn a question of market equilibrium into a question about edge density in a graph
	- more generally, we would actually have to worry about the equilibrium prices and how they change with small changes in the market
		- we might have to do this on a case-by-case-basis for specific utilities
		- or maybe there's some way to tie this price-sensitivity-wrt-cut-metric to something like the elasticity of substitution in the utility functions
			- it feels like something like this probably should hold
	- we might consider adopting the standard approach used to prove continuity of equilibrium in the fixed-number-of-consumers-and-goods case where we prove that each consumer's optimal consumption is continuous in the cut-metric via berge theorem
		- this is probably hard, because if we allow variable numbers of products, the mapping from prices to optimal consumption is a function-valued functional, which seemslike a pretty difficult thing to work with
		- we'll probably need to rely on some results like (e.1-e.3), except for real-valued-function valued functionals, rather than to bounded real-valued functionals
		- this feels quite hard

### IV. So...
- this is pretty cool stuff
- it certainly *feels* like some fairly general results should hold here
- but a lot more groundwork needs to be laid before this graph limit theory stuff can be used to produce general results about equilibrium behavior of large markets
- even so, existing theory can still provide intuitive motivation for some reasonable approaches to approximation equilibria of large markets




### References
- Arrow Debreu 1954: [ Existence of an Equilibrium for a Competitive Economy](https://web.stanford.edu/class/msande311/arrow-debreu.pdf)
- Cole Fleischer 2008: [Fast-Converging Tatonnement Algorithms for One-Time and Ongoing Market Problems](https://cs.nyu.edu/cole/papers/CF2008.pdf)
- Devanur Garg Vegh 2013 [A Rational Convex Program for Linear Arrow-Debreu Markets](https://arxiv.org/abs/1307.8037)
- Lovasz Szegedy 2004 [Limits of dense graph sequences](https://arxiv.org/abs/math/0408173)
- Lovasz Szegedy 2010 [Limits of compact decorated graphs](https://arxiv.org/abs/1010.5155)
- Borgs et. al. 2007 [Convergent Sequences of Dense Graphs I: Subgraph Frequencies, Metric Properties and Testing](https://arxiv.org/abs/math/0702004)
	- condensed version: [Graph limits and parameter testing](https://www.microsoft.com/en-us/research/uploads/prod/2016/11/Graph-Limits-and-Parameter-Testing.pdf)
