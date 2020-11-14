# Assignment #4 - Reinforcement Learning

<font color="red"> DUE: Dec 1 (Friday) 11:00 pm </font>  

<font color="blue"> type your name here </font>

# I. Overview

Describe the objective of this assignment. You can briefly state how you accompilsh it.

# II. Problems

## 2D Marble Control

![image.png](attachment:image.png)

![alternate of the original image](https://149360664.v2.pressablecdn.com/wp-content/uploads/2015/01/photodune-4581736-baseball-on-the-pitchers-mound-xs.jpg)

### STEPS for 2D Marble

1. [II Problems] First, build 2D marble class by extending the Marble class from the class note. 
2. [II Problems] Explain the environment.
3. [III Methods] Build your own RLAgent class to solve the problem.
4. [III Methods] Explain your RLAgent (with a neural network function approximator)
5. [IV Results]  Discuss the results 

## Mountain Car

<img src="https://gym.openai.com/videos/2019-10-21--mqt8Qj1mwo/MountainCarContinuous-v0/poster.jpg" data-video-type="video/mp4" data-video-source="https://gym.openai.com/videos/2019-10-21--mqt8Qj1mwo/MountainCarContinuous-v0/original.mp4">

### STEPS for Mountain Car

1. [II Problems] Learn the classic mountain car problem and explain it
2. [II Problems] Learn how to use the OpenAI Gym "MountainCarContinuous-v0" environment ([OpenAI Gym MountainCarContinuous-v0](https://gym.openai.com/envs/MountainCarContinuous-v0/))
  2.a. Following the link, by clicking the document tab, you can learn how to install and use openai.gym
3. [III Methods] Build your own RLAgent class to solve the problem.
4. [III Methods] Explain your RLAgent (with a neural network function approximator)
5. [IV Results]  Discuss the results 

# III. Methods
- Decide your TD learning approach: SARSA or Q-learning? 
- Describe your neural network function approximator (how many hidden unites? why?).
- Describe your approach and the reason why you select it.
- Explain your codes.

# IV - Results
- Describe the choice of your hyper-parameters for $\gamma$, $\epsilon$, the learning rates $\rho$'s, and the number of hiddend units (or other NN hyper-parameters). 
  - Run experiments to find good hyper-parameters
  - Show the experimental outputs to show the process of your selection
- Visualize the results and explain outputs 
  - Run the codes and tell me what you observe
  - Add more visualizations to enrich your explanation.

# V. Conclusions
Discuss the challenges or somethat that you learned. 
If you have any suggestion about the assignment, you can write about it. 

# Extra Credit
You will be qualified to earn an extra credit when you solve both problems with complete experimental results and discussions, following the bullets in results section for both. 

## Grading
For this assignment, the grading rubric is a bit different. Please check it carefully.

points | | description
--|--|:--
5 | Overview| states the objective and the appraoch 
25 | Problems | 
\-|10| 2D Marble Class
\-| 5| Explanation of problem and class implementation
\-| 5| Explanation of mountain car problem
\-| 5| explanation of the codes to use MountainCarContinuous-v0 from OpenAI Gym
25 | Methods | 
\-|10| RLAgent1 for the first problem
\-| 5| Explanation of the RLAgent1
\-| 5| RLAgent2 for the first problem
\-| 5| Explanation of the RLAgent2
40 | Results 
\-| 5| Reports the selected parameters 
\-|10| Experimental outputs that show the choice of parameters. How do you choose them?
\-| 5| Visualization of learning and learned agent
\-|10| Observations and analysis of learning results and plots
\-|10| Results analysis (following the above four rubric criteria) for the second problem
5 | Conclusions 
