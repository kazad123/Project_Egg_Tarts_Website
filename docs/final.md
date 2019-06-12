---
layout: default
title: Final Report
---

## Video here

## Project Summary
Our project goal is to implement Super Smash Bros. in Minecraft where two agents attempt to knock each other off a platform. After some research, we found an evolutionary algorithm known as NeuroEvolution of Augmenting Topologies, or NEAT for short, that creates artificial neural networks comprised of a population of individual genomes. NEAT involves many biological principles such as speciation and using a fitness function to integrate the concept of “Survival of the fittest”. With the fitness function that we created, we can compute a single number given multiple parameters that depict the quality of the genome.

NEAT will progress through multiple generations by taking the best performing genomes of each generation and reproducing them to create the fittest individuals that will be used for the next generation. Reproduction operations include adding nodes or connections between genomes which means that as NEAT progresses, the genome network will become quite complex. NEAT will terminate when the provided fitness function criterion is reached.

We decided to use NEAT as our method since we had to use a reinforcement learning algorithm. We though NEAT was the best given our problem of agent comabt, and using an evolutionary algorithm would help the agent learn the best set of moves. By using a fitness function using NEAT, we can give a quantitative number to each set of solutions per each genome of the agent. The genome with the best result per agent gives us the best set of actions for that agent to do. With each agent's goal to win by knocking their opponent off the stage.

## Approaches
After we set up NEAT, created the functions, and set up the stage, we then used an initial version of a possible fitness function. This was the initial fitness function:

and here is a gif of that result:


We used this initial fitness function only for one agent on our Super Smash Bros. stage. We inputted actions and used the fitness function for one agent, while the second agent would just stand in one place. The advantage of this was that we were able to experiment with NEAT and the Minecraft world to see if the agent could do some set of actions at a minimum. We were also able to see what the result of our fitness function was, in the early stages of our project. The only disadvantage was that our fitness function was wrong, and we clearly had to make changes to our function to make progress in the agent training.

From our initial approach, we had to change our fitness function to the following:

and a gif of the result:


We decided to change our fitness function, since our original function was not training the agent well. The agent was able to spin in circles originally, and over the evolution time, the agent figured out that these set of actions was the best, when in fact, they weren't. We changed the fitness function to help determine a better or worse reward for the angle parameter. In our first iteration of the fitness function, our angle parameter represented the angle between the agent and the enemy at the end of the mission. We then realized this would not work, so we changed the angle parameter to represent the average of angles per every second of the mission. This did not work either as our agent was not successfully attacking the enemy. This recent iteration shown above, gives good reward if the angle is within 15 degrees of the enemy. Otherwise, the reward is the angle difference squared and then mulitplied by -1. This fights against the agent's previous action of continuous spinning by giving them a very big negative reward. We had to keep changing our fitness function to produce the best and most efficient set of actions for the agent.



## Evaluation

## References
