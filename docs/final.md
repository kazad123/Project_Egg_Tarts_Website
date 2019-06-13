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
After we set up NEAT, created the functions, and set up the stage, we then used an initial version of a possible fitness function. 

This was the initial fitness function: ```hello world test```

<iframe src="https://giphy.com/embed/WQIG53ROKX8vdv0SQ2" width="480" height="270" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>

We used this initial fitness function only for one agent on our Super Smash Bros. stage. We inputted actions and used the fitness function for one agent, while the second agent would just stand in one place. The advantage of this was that we were able to experiment with NEAT and the Minecraft world to see if the agent could do some set of actions at a minimum. We were also able to see what the result of our fitness function was, in the early stages of our project. The only disadvantage was that our fitness function was wrong, and we clearly had to make changes to our function to make progress in the agent training.

From our initial approach, we had to change our fitness function to the following: ```hello world test```

We decided to change our fitness function, since our original function was not training the agent well. The agent was able to spin in circles originally, and over the evolution time, the agent figured out that these set of actions was the best, when in fact, they weren't. We changed the fitness function to help determine a better or worse reward for the angle parameter. In our first iteration of the fitness function, our angle parameter represented the angle between the agent and the enemy at the end of the mission. We then realized this would not work, so we changed the angle parameter to represent the average of angles per every second of the mission. This did not work either as our agent was not successfully attacking the enemy. This recent iteration shown above, gives good reward if the angle is within 15 degrees of the enemy. Otherwise, the reward is the angle difference squared and then mulitplied by -1. This fights against the agent's previous action of continuous spinning by giving them a very big negative reward. We had to keep changing our fitness function to produce the best and most efficient set of actions for the agent. Making the changes above to our fitness function has made our training more accurate.


## Evaluation

For our quantiative evaluation, our fitness function returns a numerical number to measure the genome of our evolution training. When each genome receives this numerical measure, NEAT then combines best genomes to produce an overall best set of actions for the agent to do. The higher number means the better genome since it has the highest reward. We want the overall number to be the highest possible, not the individual genome numbers. Although, we want the individual genome numbers to be high, the overall number is the most important. However, the higher the number doesn't always mean good results. From our previous implementations, we learned that even though we had a high number, the resulting set of actions was not good (i.e. our initial version where the agent kept spinning). This leads us to our qualitative evaluation.

Possible screenshot of genome values:

Gif of result succesffully attacking:


gif of successful knocking opponent off:


For our qualitative evaluation, we have to look at the resulting agent actions, and see them fight in person. If we see that the agents are attacking successfully and a winner is declared between the agents, then we know our project goal has been successfully met. If we see during training, that one agent has succesfully knocked another agent off the stage, that is good and a step in the right direction. Then again, we want to see if NEAT successfully picks the correct genomes to have the correct result to meet our goal. Therefore, if we are able to run the agents after training, and an agent is a winner, then we have met our project goal.

## References

1) [https://mingh2.github.io/SurvivalOfTheFittest/](https://mingh2.github.io/SurvivalOfTheFittest/)

2) [https://ianschweer.github.io/QProtector/](https://ianschweer.github.io/QProtector/)

3) [https://github.com/UCI-CS-175-Cool-Kids-Club/Neat_Fighter](https://github.com/UCI-CS-175-Cool-Kids-Club/Neat_Fighter)

4) [NEAT library](https://github.com/CodeReclaimers/neat-python)

5) [XML Documentation](http://microsoft.github.io/malmo/0.16.0/Schemas/MissionHandlers.html)

6) [NEAT Documentation](https://neat-python.readthedocs.io/en/latest/)

7) [More NEAT Documentation](https://neat-python.readthedocs.io/en/latest/activation.html)

8) [Even More NEAT Documentation](https://neat-python.readthedocs.io/en/latest/xor_example.html)

## Github Link
(https://github.com/kazad123/Project-Egg-Tarts)
