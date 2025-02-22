# Reinforcement-Learning-Game-Design
The project shows in detail how to build and train a reinforcement learning model in Python by introducing and implementing the Q-learning algorithm, using OpenAI Gym's Taxi-v3 environment as an example. The project covers the environment setup, state and action space definition, reward mechanism, and training process, and illustrates the effect of model learning by comparing the behavior of random and trained agents.

## Table of contents
- [Features]
- [Q-Learning]
- [Technical Details]
- [Reaults]

## Features
- **Taxi-v3 Environment**:
The Taxi-v3 environment consists of a 5x5 grid map where the agent, represented as a taxi driver, must pick up a passenger at one of four designated locations (Y, R, G, B) and drop them off at their destination, which is also one of the four locations. The environment is designed to test the agent's ability to navigate the grid, pick up passengers, and deliver them to the correct destination while maximizing cumulative rewards.

- **State**:
In the Taxi-v3 environment, the states are defined by the following components:
•	The taxi's position on the grid (x, y coordinates).
•	The passenger's location (either at one of the four pickup locations or in the taxi).
•	The passenger's destination.
The state space is represented by a vector: State=[xpos_taxi,ypos_taxi,pos_passenger,dest_passenger]
Given the grid size of 5x5, the possible positions for the taxi are 25. The passenger can be at one of the four pickup locations or in the taxi, resulting in 5 possible states. The destination can be one of the four locations. Therefore, the total number of states is 5×5×5×4=500. However, the actual number of usable states is slightly less due to the constraint that the pickup location and destination cannot be the same.

- **Action Space**:
The agent in the Taxi-v3 environment can perform the following discrete actions:
Action	Action number
Move forward	0
Move backward	1
Move right	2
Move left	3
Pick up the passenger	4
Drop off the passenger	5

- **Reward**:
The reward structure for the agent's actions is as follows:
•	Moving: -1 (a small penalty to encourage the shortest path).
•	Incorrect drop-off: -10 (a larger penalty for delivering the passenger to the wrong location).
•	Successful drop-off: +20 (a positive reward for completing the task successfully).

## Q-Learning
Essentially, Q-learning lets an agent use the rewards from the environment to learn, over time, the best action to take in a given state.

In our Taxi environment, we have a reward table P that the agent will learn from. It does this by looking at the reward it gets for taking an action in the current state, and then updates the Q value to remember whether that action was beneficial or not.

The values stored in the Q table are called Q-values, and they map to (state, action) combinations.

The Q-value for a particular state-action combination represents the "quality" of the action taken from that state. Better Q-values mean a greater chance of getting a larger reward.

The Q-learning algorithm updates the Q-values based on the following equation: 
Q(state,action)←(1-α)Q(state,action)+α(reward+ γ max⁡〖Q (next state,all actions))〗
Where:
	α is the learning rate.
	γ is the discount rate.
 
We initialize a Q-table with dimensions corresponding to the state and action spaces (500 states and 6 actions, resulting in a 500x6 table). The training process involves multiple episodes where the agent explores the environment and updates the Q-values based on the rewards received.

## Technical Details
- **Step 1**: Prepares the environment.
- **Step 2**: Initialization.
- **Step 3**: Training the Agent.
- **Step 4**: Testing the Trained Agent

## Results
![Screenshot of Output Video](output.png)
