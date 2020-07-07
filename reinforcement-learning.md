1. exploration vs exploitation
  - multi armed bandit
  - unknown win rates of each slot machine
  - collect data to estimate win rate of each slot machine
  - need to find expected value of reward obtained for each slot machine
  - expected value will be the mean reward obtained from each slot machine
  - balance between collecting data (exploration) and maximize reward (exploitation)
  - how to balance between exploration vs exploitation?
    1. epsilon greedy
      - 0 <= epsilon <= 1
      - choose random  with probability epsilon
      - otherwise choose best so far
      - exploration even after statistical significance is achieved
      - A/B testing could be used to stop exploration
      - there are other methods also to reduce amount of exploration

    2. optimistic initial values
      - if we have some knowlege about the true win rate of slot machine
      - initially set the estimate of such mean to a high value
      - always choose the slot machine with highest mean
      - high value of mean causes slot machine to be chosen more often (exploration)
      - more we play the slot machine its estimated mean keeps converging to true mean (exploitation)

    3. UCB1
      - large confidence interval => less accurate
      - small confidence interval => more accurate
      - chernoff-hoeffding bound => confidence bound changes exponentially as we collect more and more data
      - be greedy with upper confidence bound (UCB)

    4. Bayesian/Thompson sampling
      - central limit theorem => confidence interval is approximately gaussian
      - bayesian paradigm: data is fixed but parameters such as mean are random variables (to be estimated from data)
      - based on data we can model the distribution of data (posterior distribution)
      - posterior is proportional to likelihood x prior (from bayes' rule)
      - need to estimate posterior based on prior and available data
      - disadvantage: need to choose a prior
      - data follows some distribution (likelihood)
      - in presence of conjugate prior posterior has the same form of distribution as that of the prior
      - find conjugate prior for likelihood so that posterior has same form of distribution as that of the prior
      - sampling from bayesian posterior controls exploration and exploitation 
2. Components of a RL system
  - agent
  - environment
  - state (agent senses this from environment)
  - actions
  - rewards
  - episode : a single run of the game

3. Assigning rewards
  - do not reward for achieving sub goals 
  - agent might find novel strategy to maximize reward by achieving sub goals only and never solve the actual task at hand

4. Value function
  - credit assignment problem: what actions in the past that led to current reward?
  - delayed reward: how the current action is going to help get better rewards in future
  - two views of same problem
  - measure of future reward we might get, how good the current state is?
  - estimating value function - central task in RL

5. Markov Decision Process
  - Markov Property: How the current state depends upon previous states
  - First order markov: current state only depends on previous state
  - Nth order markov: current state depends on previous n states
  - MDP
    - 5 tuple
    - states
    - actions
    - rewards
    - state transition probabilities, reward probabilities as a joint distibution
    - discount factor
  - policy: algorithm to explore and exploit the environment
  - return at time t: total reward obtained from time t+1
  - goal: maximize return
  - discount factor (gamma): how to weigh rewards to be obtained in future? how confident are we to get rewards in future? the farther we go into the future more uncertain the rewards
  - gamma = 1 : all future rewards are weighted equally
  - gamma = 0 : ignore all future rewards
  - general choice for gamma is some value close to 1
  - Value functions and Bellman Equations
    - Value function: given a state s what is the expected return obtained from state s
    - Action value function: given a state and an action what is the expected return
    - value of terminal state is 0

6. Solving MDPs
  - decide which action to take in a given state
  - finding value function and action value function
  - solutions:
    1. Dynamic Programming  
      - Iterative policy evaluation
      - prediction problem: finding value function for a given policy
      - control problem: finding optimal policy
      - policy evaluation: find value function for each state using iterative policy evaluation
      - policy improvement: at any state choose the action that maximizes value of the bellman's equation from current state
      - finding optimal policy:
        - policy iteration: update the policy such that we always choose action that maximizes value function for each state
        - value iteration: combines policy evaluation and policy iteration in one step
      - this requires full model of environment. especially the state-transition probabilities
      - hence policy iteration and value iteration are model based methods
      - in real world this might be infeasible
      - hence we need model free methods such as monte carlo or temporal difference learning
      - monte carlo does not require bootstrapping
      - temporal difference learning does require bootstrapping

    2. Monte Carlo Methods
      - learn purely from experience
      - random component is the return: instead of finding expected value of return we measure sample mean
      - only for episodic tasks, returns are calculated only at the end of the episode
      - not fully online
      - each state is an instance of multi armed bandit problem
      - play a number of episodes and keep track of states and corresponding returns
      - in the end average returns for each state
      - if same state is visited in the episode multiple times:
        - first visit MC: save return only for the first time state is visited
        - every visit MC: save return for each time state is visited
        - both result to same answer
        - first visit is easier to implement
      - control problem: finding optimal policy
      - use action value function Q(s, a) and find average returns for each state action pair
    
    3. Temporal Difference Learning
      - finding value function: prediction problem TD(0)
        - estimate the value at current state based on expected return: reward and expected value of next state
        - do not need to wait for episode to end for learning
      - finding optimal policy: SARSA
        - update Q values for a state action pair
      - finding optimal policy: Q-learning
        - off policy algorithm
        - update Q value for state action pair based on best action for the next state even if that action is not actually taken
        
      
