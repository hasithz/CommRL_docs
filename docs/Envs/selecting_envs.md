# Selecting Environments 

There are mainly 2 types of environments are used in multi agent environments. 

## Mini-grid environments 
**[mini grid environments](https://minigrid.farama.org/)**
The environment mentioned above is for a single agent and has many scenarios mentioned in it. 

This library contains a collection of 2D grid-world environments with goal-oriented tasks. The agent in these environments is a triangle-like agent with a discrete action space. The tasks involve solving different maze maps and interacting with different objects such as doors, keys, or boxes. The design of the library is meant to be simple, fast, and easily customizable.

In addition, the environments found in the BabyAI repository have been included in Minigrid and will be further maintained under this library.


### multi agent env
as for the multi agent we can use **[mini grid env](https://github.com/ArnaudFickinger/gym-multigrid)**
## MPE

**[MPE](https://pettingzoo.farama.org/environments/mpe/)**
This has 9 environment types. 
Multi Particle Environments (MPE) are a set of communication oriented environment where particle agents can (sometimes) move, communicate, see each other, push each other around, and interact with fixed landmarks.

These environments are from OpenAI’s MPE codebase, with several minor fixes, mostly related to making the action space discrete by default, making the rewards consistent and cleaning up the observation space of certain environments.

| Aspect                       | Multi-Grid Environments       | Multi-Particle Environments |
|------------------------------|-------------------------------|------------------------------|
| Definition                   | A grid-like environment where <br>agents can move between cells or nodes | An environment where multiple particles <br>interact with each other |
| Example                      | Conway's Game of Life          | Molecular dynamics simulation |
| State representation         | Discrete                       | Continuous                   |
| Action space                 | Discrete                       | Continuous                   |
| Dynamics                     | Deterministic or stochastic   | Deterministic or stochastic   |
| Interaction among entities   | Indirect                      | Direct                       |
| Computational complexity     | Often computationally efficient | Often computationally expensive |
| Applications                 | Simulation of biological systems, <br>traffic flow, social dynamics | Materials science, chemistry, physics |
observation type                | 2D array like observation <br>and multi dict | agent’s position and velocity, other agents’ relative positions <br>and velocities, landmarks’ relative positions, landmarks’ and agents’ types, <br>and communications received from other agents|
action space                    | discrete                      | discrete / continuous |