---
layout: default
title: Status
---

## Project Summary

Our version of Super Smash Bros. in Minecraft utilizes our knowledge to create a multi-agent combat system. The overall goal for the whole project is to now have two agents successfully fight to try and knock the other off the stage to win. We have been experimenting with different methods(Q-learning and NEAT), and hope to decide on one method soon to complete the project with that chosen method. With NEAT (Neuroevolution of Augmenting Topologies), we hope that our agent can successfully evolve to learn to knock the opponent off the stage successfully.  With Q-learning, we can store a table of possible actions and they're assoicated rewards...***(NOTE: finish if decide to keep here)***

The goal for this status milestone was to have one stationary agent, and one trained agent. This trained agent is supposed to move to the enemy, and attack to knock the enemy off. Our environment is flat stage of 11 x 11 diamond blocks above a world of lava. If we still have time, once our project is complete, we intend to make the environment more complex. Lastly, we hope to improve the agent training of whatever method we decide on.

## Approach

The NEAT algorithm is similar to a neural network with layers of hidden nodes. However, this neural network evolves by finding a balance between the fitness of evolved solutions and their diversity. For every topology, or stage of evolution, there is a a genome which reflects the best set of actions. For every genome, there is an associated fitness value which is determined from a fitness function. **(CHECK THIS FITNESS FUNCTION) This fitness function takes into account the distance between the two fighters, since we want the fighters to have the least amount of distance apart.** The goal of NEAT is to have the best fitness per evolution, and develop the best topology as it is evolving.

This is done by creating a large number of genomes, each with their respective actions and rewards, represented by nodes and edges. We then cross the best 2 fitness scores out of all the genomes, to output a new genome for the next generation. This genome is our best solution.

We used the NEAT python library together with Malmo to teach our agent. To begin we created an 11 x 11 grid made of diamond blocks which is our stage. We spawn our two agents at the same location for every generation and randomize the yaw between 0 and 360. Our world then starts the training, and evolution begins...

## Evaluation

## Remaining Goals and Challenges

## Resources Used
1) [https://mingh2.github.io/SurvivalOfTheFittest/](https://mingh2.github.io/SurvivalOfTheFittest/)

2) [https://ianschweer.github.io/QProtector/](https://ianschweer.github.io/QProtector/)

3) [https://github.com/UCI-CS-175-Cool-Kids-Club/Neat_Fighter](https://github.com/UCI-CS-175-Cool-Kids-Club/Neat_Fighter)

4) [NEAT library](https://github.com/CodeReclaimers/neat-python)


