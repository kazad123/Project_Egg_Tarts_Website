---
layout: default
title: Final Report
---

## Video Summary
<iframe width="560" height="315" src="https://www.youtube.com/embed/wHBShe0ETNE" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Project Summary
Our project goal is to implement Super Smash Bros. in Minecraft where two agents attempt to knock each other off a platform. After some research we found an evolutionary algorithm known as NeuroEvolution of Augmenting Topologies, or NEAT for short, that creates artificial neural networks comprised of a population of individual genomes. NEAT involves many biological principles such as speciation and using a fitness function to integrate the concept of “Survival of the fittest”. With the fitness function that we created, we can compute a single number given multiple parameters that depicts the quality of a genome. 

We decided to use NEAT as our method since we had to use a reinforcement learning algorithm. We thought NEAT was the best given our problem of agent combat. Using NEAT's evolutionary algorithm would help the agent learn the best set of moves given fitness constraints. By using our fitness function with NEAT, we can give a quantitative number to each genome solution. With the goal being to knock off the other agent from the platform, the genomes with the best results in its generation holds the best set of actions.

NEAT will progress through multiple generations by taking the best performing genomes of each generation and reproducing them to create the most fit individuals that will be used for the next generation. Reproduction operations includes adding nodes or connections between genomes which means that as NEAT progresses, the genome network will become quite complex. NEAT will terminate when the provided fitness function criterion is reached. 


## Approaches
This was the initial fitness function: 

----
if self.angle > 180: 
      self.angle = 360 - self.angle
fitness = (self.damage_dealt * damage_scale) - (self.ent_distance * dist_scale) - (self.angle * angle_scale) + (travel_scale * self.dist_travelled) - base
 
<iframe src="https://giphy.com/embed/WQIG53ROKX8vdv0SQ2" width="480" height="270" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>

We used this initial fitness function only for one agent on our Super Smash Bros. stage. In order for our agent to properly train, we inputted actions and used the fitness function for one agent, while the second agent would just stand in one place. The advantage of this was that we were able to experiment with NEAT and the Minecraft world to see if the agent could do some set of actions at a minimum. We were also able to see what the result of our fitness function was, in the early stages of our project.

The battlefield has a size of 12x6 diamond blocks and lies above a sea full of lava. We first attempted to have a battlefield of 12x12 blocks but we figured out that this creates a large initial barrier for improvement because there is too much distance between the two agents. 

The weapon that we chose for the agents to use is a wooden sword because this does the least amount of damage while still knocking back the other agent. This allows the training agent to sufficiently knock back the stationary agent without not killing it. 

Before the project update: 

The fitness function that we created takes a few different parameters into consideration. First of all, we want the other agent to be knocked off so by the end of a mission, if the other player is knocked off the platform, then a large sum of points is awarded. Another parameter that we take into consideration is the angle between the two agents. During the early phase of training we noticed that most of the time the training agent would be jumping around in circles and not moving towards the stationary agent. We decided to train the agent by enforcing a continuous angle constraint where the agent was awarded more points if the training agent was facing the stationary agent. Distance is taken into account to encourage the training agent to end up closer to the stationary agent. Again, we noticed early on that the agent wasn’t attempting to get closer to the other agent so we placed a distance constraint and punished the training agent for being further away from the stationary agent. Time is of the essence and an agent that knocks off the opponent in a shorter amount of time is a better fit agent than one who does so in a longer amount of time. We decided to create a scale that would deduct more points the longer an agent takes to complete a mission.

Updated fitness function: ``` 
        if self.angle > 180:
        self.angle = 360 - self.angle
        # Angle scaling, larger penalty for doing badly, reward for facing other anet
        if self.angle < 15:
            self.angle = 0
        else:
            self.angle = self.angle ** 2
        fitness = (self.damage_dealt * damage_scale) - (self.ent_distance * dist_scale) - \
                  (self.angle * angle_scale) + (self.dist_travelled * travel_scale) - base ```

<blockquote class="imgur-embed-pub" lang="en" data-id="a/BntYSU8" data-context="false" ><a href="//imgur.com/a/BntYSU8"></a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script>

We made several adjustments after the status update with regards to our input. Before the status update, we only had two input nodes which were distance away from the other agent and average angle, respectively. We noticed that only two inputs were not enough sensors for the agent to have depth perception so we decided to add a few more. We added distance to each side of the platform to allow the agent to know when it is close to falling off the edge. We also included the distance away from agent in terms of x and z values. In total we have around 8 total input nodes which maps to 3 output nodes. Those three output nodes are move forward, strafe and turn. We decided to not have an output mode for attack since each attack takes a second we decided that the agent should always be attacking. 

<blockquote class="imgur-embed-pub" lang="en" data-id="a/L85U7DE" data-context="false" ><a href="//imgur.com/a/L85U7DE"></a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script>

A few things were done with the fitness function as well. We scaled distance and angle to balance the importance of each. An issue that we had with angle before the status update was that only the average angle was taken into consideration, therefore there was not great enough of a penalty for when agents were looking away. We decided that the agent needed a greater punishment the further it was looking away from the other agent and we implemented this by adding a square function when we scaled our angle. This way the greater the angle between the two agents, the greater the punishment. Distance was also scaled down because we decided to give more importance to angle to encourage the agent to look towards the other agent. 


## Evaluation

Over the course of training, our agent seems to improve quite quickly. Initially, we see the training agent engaging in random input where it would either walk around in circles or sometimes just spin standing still. We see that each parameter that we have in our fitness function is being enforced. After each generation, the genomes with the best numerical score are chosen for breeding in a stage called crossover. In this stage, certain connections between nodes are either removed, added or remain the same depending on which criteria matches the high performing genome. 

<iframe src="https://giphy.com/embed/SiGI6NsaJzvLMI05be" width="480" height="270" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/SiGI6NsaJzvLMI05be">via GIPHY</a></p>

To begin with, an important step in the right direction is the placement of the training agent as the mission progresses. Initially, we see that our training agent does not attempt move towards the stationary agent but instead walks straight off the edge. We want to prevent this with punishing the agent with a grand negative score like mentioned earlier. Another aspect of placement is how the training agent places itself with regard to the stationary agent. This is where our distance parameter in the fitness function comes into play. By punishing the training agent for staying still, we encourage it to start moving around and especially towards the stationary agent. As you can see below, after a few genomes the agent does not jump off anymore and makes progress in actually attacking the stationary agent. 

<iframe src="https://giphy.com/embed/lQC3mRR4pGwUj1CEQA" width="480" height="270" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/lQC3mRR4pGwUj1CEQA">via GIPHY</a></p>

We made another step in the right direction by administering an angle parameter. Throughout the early stages of training, the agent stands still and turns in one direction while continuously attacking. In order to prevent this random-like behavior, the average angle was taken into consideration in our fitness function. Although this is only an average and not the actual angle at each tick, it is a step into the right direction and the training agent still manages to reduce the spinning behavior. 

<iframe src="https://giphy.com/embed/WQIG53ROKX8vdv0SQ2" width="480" height="270" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/WQIG53ROKX8vdv0SQ2">via GIPHY</a></p>

Lastly, after adding in the 6 other sensors the agent started making improvements much quicker than before. The agent was able to avoid jumping off the platform several generations earlier than the previous iteration and was able to make steps in the right direction for heading towards the other agent. Also, the agent was able to understand to move towards the other agent and started making milestones such as hitting the other agent much earlier compared to the previous iteration.

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
[Github](https://github.com/kazad123/Project-Egg-Tarts)

