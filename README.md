# Kuiper Escape Using Reinforcement Learning


## Aim
 To simulate and analyze an agent's navigation in the custom Kuiper belt environment and hence train it to maximize rewards by avoiding obstacles and exploring efficiently using reinforcement learning algorithms.


## Requirements
1. Numpy
2. Matplotlib
3. Gymnasium
   - gym_kuiper_escape (custom lib)

## Kuiper Belt Environment
To challenge the agent's learning capabilities, the custom Kuiper Belt environment was designed as a complex and dynamic scenario. Unlike simpler environments, this setup provided limited knowledge of its dynamics, requiring the agent to learn optimal strategies through exploration and adaptation. This made it an ideal choice for implementing and analyzing reinforcement learning algorithms in a more realistic and unpredictable setting.


###### State Space
The state is a "virtual" lidar system. It sends off virtual beams of light in all directions to gather an array of points describing the distance and characteristics of nearby objects. The size of the lidar array and resulting observation/state space is configurable when the environment is initialized.

The observation data (for each beam in the lidar array):
- Distance (i.e. radial distance from player to terminating point of lidar beam) Collision detection
- 0 if terminated at edge of screen, or at max radius distance 1 if collided with a rock

e.g [ 0 0.1 0.2 0.3 0.5 0.6 0.2 0.3 | 0 1 0 0 0 1 0 1 ] where the first 8 in the array indicate normalised distances of the rock from the agent and the last 8 in the array indicate whether the rock will collide or not.

###### Action Space
The agent has the following discrete set of actions :
- 0: Don't move
- 1: Up
- 2: Right
- 3: Down
- 4: Left


###### Reward Function
Reward is given to the agent according to a function which is inversely related to the distance from the center of the environment screen to the agent . Further, a negative reward is awarded to the agent if collision is detected .

###### Algorithms
In the Frozen Lake environment, understanding deterministic and stochastic dynamics is key for choosing the right strategy:

- **Deterministic Environment**: Actions have predictable outcomes. For example, if an agent moves "left," it always ends up to the left. No randomness affects the result.

- **Stochastic Environment**: The Frozen Lake environment is stochastic. Actions have uncertain outcomes; for instance, moving "left" might result in slipping to another direction e.g "right" .This randomness requires the agent to plan for different possible outcomes.

Dynamic programming algorithms help solve this environment by handling its unpredictability:

- **Policy Evaluation**: Estimates how good it is to follow a given policy by considering the possible outcomes.

- **Policy Improvement**: Refines the policy by choosing actions that maximize expected value, accounting for randomness.

- **Policy Iteration**: Repeats evaluation and improvement until the policy is optimal.

- **Value Iteration**: Directly updates state values by choosing the best actions, speeding up convergence to an optimal policy.

These methods find effective strategies in the uncertain conditions of the Frozen Lake.


The link for the code has been provided below .






Here's a GIF demonstrating the Frozen Lake algorithm:

![Frozen Lake](Gifs/Frozen_Lake_gif.gif)



###### Results






