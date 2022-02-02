---
Title: "Combining Robocode & ANJI"
excerpt: "The objective was to create a competitive Robocode player with the implementation of the Neuro-Evolution of Augmenting Topologies (NEAT) algorithm. "
---
## Summary
The objective of this study is to create a competitive Robocode player with the implementation of the Neuro-Evolution of Augmenting Topologies (NEAT) algorithm. The framework for the robot was designed in Eclipse using Robocode framework. Primary functions of this include initializing robot battles, facilitating in game inputs/outputs, and collecting contest results. The neural network evolution is implemented through Another Neat Java Implementation (ANJI). This first provides framework for the construction of a neural network and the NEAT modifications. Furthermore, it crowns champion chromosomes through tournament style play, where each tournament corresponds to exactly one generation. The evolutionary process is launched after the conclusion of each tournament.

Robots are trained through self-play in 1-versus-1 style battles. Each battle is 10 rounds and is scored using Robocode’s standard scoring. The robot that has the higher amount of points wins the round. The winner of the battle is determined by the number of rounds won. Tournaments begin with 128 competitors and declare one winner at the end. In total, over 1,000 generations were run to train the bot. At this point, the robot is able track is opponent, move towards it, and ram it to inflict damage. The robot is able to shoot its opponent, however its accuracy is not as consistent as desired.

## ANJI Details
ANJI (Another NEAT Java Implementation) is an implementation of the NEAT (Neuro-Evolution of Augmenting Topologies) which is an algorithm developed for evolving artificial neural networks. In general, the algorithm evolves connection weights and network architecture by starting with minimal topology. As the generations progress, the structure is developed through crossover and mutation. Mutations include alterations to weights of existing connections, the introduction of new connections, and the addition of new neurons. ANJI’s most current version was released in August of 2005. Documentation can be found [following site](http://anji.sourceforge.net/).

## Results

### First generation.

{% include video id="gLxzMYMcctQ" provider="youtube" %}

### 365th generation. 

{% include video id="h2uedWUbkyk" provider="youtube" %}



## Contributors
This was a joint work with Jacob Lindey and John Yannotty overseen by Dr. Sam Thangiah.