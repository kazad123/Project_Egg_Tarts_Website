---
layout: default
title: Status
---

## Project Summary

Our project goal is to implement Super Smash Bros. in Minecraft where two agents attempt to knock each other off a platform. After some research we found an evolutionary algorithm known as NeuroEvolution of Augmenting Topologies, or NEAT for short, that creates artificial neural networks comprised of a population of individual genomes. NEAT involves many biological principles such as speciation and using a fitness function to integrate the concept of “Survival of the fittest”. With the fitness function that we created, we can compute a single number given multiple parameters that depicts the quality of genome. 

NEAT will progress through multiple generations by taking the best performing genomes of each generation and reproducing them to create the most fit individuals that will be used for the next generation. Reproduction operations includes adding nodes or connections between genomes which means that as NEAT progresses, the genome network will become quite complex. NEAT will terminate when the provided fitness function criterion is reached.

## Approach

Our approach to implementing Super Smash Bros. in Minecraft involves NEAT to teach the agent how to knock off the other agent in our preset battlefield. 

Currently the battlefield has a size of 10x5 diamond blocks and lies above a sea full of lava. Our goal for the status was to have one stationary agent and one trained agent that would attempt to knock off the stationary agent. We first attempted to have a battlefield of 11x11 blocks but we figured out that this creates a large initial barrier for improvement because there is too much distance between the two agents. 

The weapon that we chose for the agents to use is a wooden hoe because this does the least amount of damage while still knocking back the other agent because we wish to not kill the other agent during the process. 

The inputs of the agent include … (add later or delete)

The fitness function that we created takes a few different parameters into consideration:

- First of all, we want the other agent to be knocked off so by the end of a mission, if the other player is knocked off the platform then a large sum of points is awarded. Since the area under the platform is a sea full of lava, it is evident when the other agent is knocked off. 

- Another parameter that we take into consideration is the angle between the two agents. During the early phrase of training we noticed that most of the time the training agent would be jumping around in circles and not moving towards the stationary agent. We decided to train the agent by enforcing a continuous angle constraint where the agent was awarded more points if the training agent was facing the stationary agent.

- Distance is taken into account to encourage the training agent to end up closer to the stationary agent. 

- Time is of the essence and an agent that knocks off the opponent in a shorter amount of time is a better fit agent than one who does so in a longer amount of time. We decided to create a scale that would deduct more points the longer an agent takes to complete a mission.

## Evaluation

## Remaining Goals and Challenges

In the final project, we hope to completely implement the stage with two agents being trained to knock each other off the stage. Our next goal to have completed by the final submission is to have this working, instead of having one agent be stationary on the stage. We see this is a challenge since the evolutions have to focus on the moving agent's current position at a specific point in time instead of a static position. With further research, experimentation, and meetings, we hope to accomplish this.

The next goal we would like to focus on is changing the environment. First, by expanding the stage from 10 x 5 to something larger and/or by making the environment(stage) slightly more dyanmic. This would add a different aspect to the agent's training and how they evolve. It would be interesting to see if the agent can learn to use the environment to their advantage in combat.

Lastly, due to our method being based on evolution, there is RNG which may cause long hours of training. We hope by adjusting the population of genomes, and possibly other factors, this could cut our training time down. Regardless, we still need to wait hours for training to be complete. From the evolutions and their respective genomes, we also hope to get working a graph visualization of the evolution progress. This graph would show each genome and their fitness score, which would make it easier to visualize each genome and its evolution progress.


## Resources Used
1) [https://mingh2.github.io/SurvivalOfTheFittest/](https://mingh2.github.io/SurvivalOfTheFittest/)

2) [https://ianschweer.github.io/QProtector/](https://ianschweer.github.io/QProtector/)

3) [https://github.com/UCI-CS-175-Cool-Kids-Club/Neat_Fighter](https://github.com/UCI-CS-175-Cool-Kids-Club/Neat_Fighter)

4) [NEAT library](https://github.com/CodeReclaimers/neat-python)

5) [XML Documentation](http://microsoft.github.io/malmo/0.16.0/Schemas/MissionHandlers.html)


