---
layout: default
title: Status
---

## Project Summary

Our version of Super Smash Bros. in Minecraft utilizes our knowledge to create a multi-agent combat system. The overall goal for the whole project is to now have two agents successfully fight to try and knock the other off the stage to win. We have been experimenting with different methods(Q-learning and NEAT), and hope to decide on one method soon to complete the project with that chosen method. With NEAT (Neuroevolution of Augmenting Topologies), we hope that our agent can successfully evolve to learn to knock the opponent off the stage successfully.  With Q-learning, we can store a table of possible actions and they're assoicated rewards...***(NOTE: finish if decide to keep here)***

The goal for this status milestone was to have one stationary agent, and one trained agent. This trained agent is supposed to move to the enemy, and attack to knock the enemy off. Our environment is flat stage of 11 x 11 diamond blocks above a world of lava. If we still have time, once our project is complete, we intend to make the environment more complex. Lastly, we hope to improve the agent training of whatever method we decide on.

## Approach

The NEAT algorithm is similar to a neural network with layers of hidden nodes. However, this neural network evolves by finding a balance between the fitness of evolved solutions and their diversity. For every topology, or stage of evolution, there is a a genome which reflects the best set of actions. For every genome, there is an associated fitness value which is determined from a fitness function. **(CHECK THIS FITNESS FUNCTION) This fitness function takes into account the distance between the two fighters, since we want the fighters to have the least amount of distance apart.** The goal of NEAT is to have the best fitness per evolution, and develop the best topology as it is evolving.

This is 

**REFERENCE: ((((A brief overview of the genetic algorithm: First we create a large population of genomes, N. Each represents a different neural net (genes are the nodes and edges of the neural net). We then test each genome (by running our Malmo bot with the neural net created from that genome), assign it a fitness score (score of how well the organism did), and select the two members from that species with the best fitness score. Then we crossover the genomes (randomly picking a position in the chromosome then swapping everything after it) and mutate the resulting genomes to form a new generation.)))) **

We used a NEAT python library together with Malmo to teach our agent. To begin we created a 10 x 10 grid made of diamond blocks. We spawn our two agents at the same location and randomize the yaw between 0 and 360. Our world trains the population, evaluates the genomes, and handles the fighter.



## Evaluation

## Remaining Goals and Challenges

## Resources Used
