---
author: "Younes Belkada"
date: 2021-10-12
type:
- notes
- courses
title: Week 2 - RL Course
weight: 10
math:
  enable: true
comment: false
tags: ['Reinforcement Learning', 'Maths', 'Markov Chains']
categories: ["Course notes"]
featuredImage: ""
featuredImagePreview: ""
lightgallery: true
---

In the previous section we have seen how to formulate a RL problem using MDPs and provide some tips in order to analytically evaluate a policy (set of actions at each set) if some variables were known beforehand using the Bellman equation and the Bellman operator.

Here in the second lecture we are going to tackle the issue of how to solve an MDP (i.e get the optimal policy $\pi$) given some parameters of the problem. Few techniques exists in order to achieve this, let's start with the **Value Iteration**

# Value Iteration

{{< image src="/images/notes/rl_value_iteration.gif" caption="Value Iteration" title="https://towardsdatascience.com/policy-and-value-iteration-78501afb41d2" height="500" width="500">}}


### Intuition

We have few tools in our toolbox. First of all, *how do we evaluate a policy?* We can simply compute the **Value Function** which corresponds to a kind of "summary" of the rewards at each state, given a policy. If we consider again the simple MDP considered last week, if the policy is $\pi = \\\{\textcolor{#E94D40}{a_0},\ \textcolor{#E94D40}{a_0} ,\ \textcolor{#3697DC}{a_1}\\\}$

{{< image src="https://cdn.mathpix.com/snip/images/rLqPQXWNtuf3BU915gjmwTnkM9O16IG2RDmc0z1iV2o.original.fullsize.png" caption="Simple MDP" title="https://cdn.mathpix.com/snip/images/rLqPQXWNtuf3BU915gjmwTnkM9O16IG2RDmc0z1iV2o.original.fullsize.png" height="300" width="300">}}

Analytically, The **Value Function** is equal to $V^\pi = [0.033, 0.363, 0]$. Which means intuitively, that in *expectation* under the **given** policy, moving frequently to the state $s_1$ is highly **benefic** in terms of reward.

*What if the policy is unknown?* Then the problem would have a different formulation, our goal would be to **find the best policy possible** among the combination of all possible policies. You can image that this is doable if the problem is simple enough ($|A| < N_A$ and $|S| < N_S$, i.e reasonable number of possible actions and reasonable number of states) but extremely complex if not.
 
The idea of the **Value Iteration** algorithm is the following:
* Initialize $V_0$ in $R^N$
* At each iteration $k = 1,2,...,K$:
    * Compute $V_{k+1} = \mathcal{T}V_k$ until $|| V_{k+1} - V_k || \leq \epsilon$
* Get the ***greedy policy*** $
\pi_{K}(s) \in \arg \max _{a \in A}\left[r(s, a)+\gamma \sum_{s^{\prime}} p\left(s^{\prime} \mid s, a\right) V_{K}\left(s^{\prime}\right)\right]
$

Recall that the greedy policy is $\in$ the set of $argmax$ because we may have several values that reaches the maximum.

Intuitively, the algorithm would work as the followwing
* Initialize with a random **Value Function**
* Compute the Bellman operator applied to this **Value Function** for all **the possible actions** and update $V_k$ at each step by considering the action that maximized the **Value Function** (i.e. the optimal action)

Let's consider the following problem, where the initial state is $S_0$ and the final state $S_3$. The set of actions here is $A = \\\{a_0, a_1, a_2, a_3\\\}$ which corresponds to the action of moving to a corresponding state. We can imagine that it is a *maze* where the agent has to start from the state 0 and tries to learn how to escape from there.


{{< image src="/images/notes/diag_rl1_value_iteration.png" caption="Another simple MDP for our example" width="300" height="300" title="Original Content">}}

Here the process is still a MDP because it respects the assumptions under **Markov Decision Processes**. We ignore in our example the transition probabilities for simplicity and apply the algorithm for one step.

{{< image src="/images/notes/rl_diag_1.gif" caption="Value Iteration Algorithm for one step - Original content" title="Original Content">}}

After one step, the optimal policy is the following:

$$ \begin{array}{l}V_1\ =\ \left[1,\ 10,\ 10,\ 10\right]\\\\\\ \pi^* =\ \left\\\{\left[a_1,\ a_3,\ a_3,\ a_3\right],\ \left[a_2,\ a_3,\ a_3,\ a_3\right]\right\\\}\end{array} $$

Which absolutely makes sense, because in this MDP, to reach an optimal reward value you should avoid moving to the state $s_0$ and move to $s_3$ whenever you can.

### Theorem

Thankfully, we have a guarantee that the algorithm will give us a solution in some fixed number of steps.