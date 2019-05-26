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

The weapon that we chose for the agents to use is a wooden sword because this does the least amount of damage while still knocking back the other agent. This allows the training agent to sufficiently knock back the stationary agent without not killing it. 

Fitness = ### enter fitness function here, make sure angle and distance 

The fitness function that we created takes a few different parameters into consideration. 
- First of all, we want the other agent to be knocked off so by the end of a mission, if the other player is knocked off the platform then a large sum of points is awarded. Since the area under the platform is a sea full of lava, it is evident when the other agent is knocked off. 
- Another parameter that we take into consideration is the angle between the two agents. During the early phrase of training we noticed that most of the time the training agent would be jumping around in circles and not moving towards the stationary agent. We decided to train the agent by enforcing a continuous angle constraint where the agent was awarded more points if the training agent was facing the stationary agent.
- Distance is taken into account to encourage the training agent to end up closer to the stationary agent. Again, we noticed early on that the agent wasn’t attempting to get closer to the other agent so we placed a distance constraint and punished the training agent for being further away from the stationary agent.
- Time is of the essence and an agent that knocks off the opponent in a shorter amount of time is a better fit agent than one who does so in a longer amount of time. We decided to create a scale that would deduct more points the longer an agent takes to complete a mission.

## Evaluation

Over the course of training, our agent seems to improve quite quickly. Initially, we see the training agent engaging in random input where it would either walk around in circles or sometimes just spin standing still. Over the course of training, we see that each parameter that we have in our fitness function is being enforced. 

### gif of training agent standing still spinning and attacking

To begin with, an important step in the right direction is the placement of the training agent as the mission progresses. Initially, we see that our training agent does not attempt move towards the stationary agent but instead walks straight off the edge. We want to prevent this with punishing the agent with a grand negative score like mentioned earlier. Another aspect of placement is how the training agent places itself with regard to the stationary agent. This is where our distance parameter in the fitness function comes into play. By punishing the training agent for staying still, we encourage it to start moving around and especially towards the stationary agent. As you can see below, after a few genomes the agent does not jump off anymore and makes progress in actually attacking the stationary agent. 

### gif of training agent walking towards stationary agent, not walking off 

We made another step in the right direction by administering an angle parameter. Throughout the early stages of training, the agent stands still and turns in one direction while continuously attacking. In order to prevent this random-like behavior, the average angle was taken into consideration in our fitness function. Although this is only an average and not the actual angle at each tick, it is a step into the right direction and the training agent still manages to reduce the spinning behavior. 

### gif of training agent walking around stationary agent and facing it (showing that our angle parameter is somewhat working)


## Remaining Goals and Challenges

There are still a few obstacles in our way in our path to completing our goal. Although we believe that our fitness function rewards the agent properly, there are still a few parameters that we would like to experiment with to see if our agent could improve. In our current implementation, our training agent struggles with knocking the stationary agent off the platform. 

There are some conflicting training protocols that we’ve integrated which pose as obstacles in the training process. We’d like to fix these issues with approaching each topic differently and that will be our goal for the final report. 

One of the issues that we currently have is how distance is being evaluated. In order to get past the initial barrier, we decided to punish agents who stand still and attack the entire mission by taking off more points the less distance the agent has walked for that respective mission. Although this prevents our training agent from standing still for the entire mission, it brings up the possibility of our agent walking around too much to gain points instead of focusing on attacking the stationary agent.

Another issue that we have is enforcing the angle between the training agent and the stationary agent. Initially, the angle that was being fed into fitness function was the angle that the training agent ended with at the end of the mission. This did not include the angle of the training agent at every tick of the mission which means that it did not matter where the agent was looking as long as it was facing the stationary agent by the end of the mission. This is an issue because the agent can still turn in circles so instead we decided to take the average at every tick into account. Although this is a step in the right direction for now, we need a better solution to fix this problem.


## Resources Used
1) [https://mingh2.github.io/SurvivalOfTheFittest/](https://mingh2.github.io/SurvivalOfTheFittest/)

2) [https://ianschweer.github.io/QProtector/](https://ianschweer.github.io/QProtector/)

3) [https://github.com/UCI-CS-175-Cool-Kids-Club/Neat_Fighter](https://github.com/UCI-CS-175-Cool-Kids-Club/Neat_Fighter)

4) [NEAT library](https://github.com/CodeReclaimers/neat-python)

5) [XML Documentation](http://microsoft.github.io/malmo/0.16.0/Schemas/MissionHandlers.html)

6) [NEAT Documentation](https://neat-python.readthedocs.io/en/latest/)

7) [More NEAT Documentation](https://neat-python.readthedocs.io/en/latest/activation.html)

8) [Even More NEAT Documentation](https://neat-python.readthedocs.io/en/latest/xor_example.html)


