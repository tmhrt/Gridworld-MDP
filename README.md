# Markov Decision Process

A Markov decision process (MDP), by definition, is a sequential decision problem for a fully observable, stochastic environment with a Markovian transition model and additive rewards. It consists of a set of states, a set of actions, a transition model, and a reward function. Also, a MDP usually has a discount factor γ , a number between 0 and 1, that describes the preference of an agent for current rewards over future rewards. 

## Policy

A solution to a MDP is called a policy π(s). It specifies an action for each state s. In a MDP, we aim to find the optimal policy that yields the highest expected utility. 

## Value Iteration
Value iteration is an algorithm that gives an optimal policy for a MDP. It calculates the utility of each state, which is defined as the expected sum of discounted rewards from that state onward.

<img src="screenshots/bellman_equation.png" width="350">

This is called the Bellman equation. For n states, there are n Bellman equations with n unknowns (the utilities of states). To solve this system of equations, value iteration uses an iterative approach that repeatedly updates the utility of each state (starting from zero) until an equilibrium is reached (converge). The iteration step, called a Bellman update, looks like this:

<img src="screenshots/bellman_update.png" width="400">

Here's the pseudocode for calculating the utilities of states. 

<img src="screenshots/value_iteration.png" width="650">

Then, after the utilities of states are calculated, we can use them to select an optimal action for each state.

<img src="screenshots/select_action.png" width="320">

## Policy Iteration

Policy iteration is another algorithm that solves MDPs. It starts with a random policy and alternates the following two steps until the policy improvement step yields no change:

(1) Policy evaluation: given a policy, calculate the utility U(s) of each state s if the policy is executed; 

(2) Policy improvement: update the policy based on U(s).

<img src="screenshots/select_action.png" width="320">

For the policy evaluation step, we use a simplified version of the Bellman equation to calculate the utility of each state. 

<img src="screenshots/simplified_bellman_equation.png" width="370">

For n states, there are n linear equations with n unknowns (the utilities of states), which can be solved in O(n^3) time. To make the algorithm more efficient, we can perform some number of simplified Bellman updates (simplified because the policy is fixed) to get an approximation of the utilities instead of calculating the exact solutions. 

<img src="screenshots/simplified_bellman_update.png" width="400">

Here's the pseudocode for policy iteration. 

<img src="screenshots/policy_iteration.png" width="650">

## Q-Learning
In q-learning the learned action-value function, Q, directly approximates q* , the optimal action-value function, independent of the policy being followed. Here are modified bellman equation and the epesodical iterative learning algorithm to get the optimal Q unction(from d/t experiences). trhe hyper parameter Alpha defines the learning rate(how fast to adopt new findidngs vs old knowledge) whereas Epsilon dictates the balance between exploration(Epsilon set to 1 initialy) and eploitation(Epsilon close to zero after decaying throught the episode)

<img src="screenshots/q-learning.png" width="900">
