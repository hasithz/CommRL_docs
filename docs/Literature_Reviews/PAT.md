# PAT (Parallel Attentional Transfer)

Y. Liang and B. Li, “Parallel Knowledge Transfer in Multi-Agent Reinforcement Learning.” arXiv, Mar. 29, 2020. Accessed: Apr. 17, 2023. [Online]. Available: http://arxiv.org/abs/2003.13085

![CommNet architecture as in paper](https://raw.githubusercontent.com/hasithz/CommRL_docs/abe8d78ea94fd65dd614f2052b9cb55bde8a1f80/assets/images/commnet%20and%20communication.drawio.svg)

The PAT (Policy Aggregation for Training Agents) architecture is a method for training cooperative multi-agent systems (MAS) using reinforcement learning (RL). The goal of the PAT architecture is to enable agents in a MAS to learn to coordinate their actions and achieve better overall performance than individual agents acting independently.

The PAT architecture involves the following components:
-	1. Individual agents: These are the agents in the MAS that interact with the environment and receive rewards based on their actions.
-	2. Centralized critic: This is a central agent that evaluates the performance of the individual agents and provides feedback in the form of a state-action value function.
-	3. Decentralized actors: These are the individual agents that generate actions based on their own observations of the environment and the feedback provided by the centralized critic.
-	4. Communication channel: This is a means for the individual agents to share information with each other and coordinate their actions.
	
The PAT architecture works by training the individual agents using RL algorithms such as Q-learning or policy gradient methods. The central agent provides feedback to the individual agents in the form of a state-action value function, which is used to guide the agents' actions. The individual agents use a decentralized actor-critic algorithm to generate actions based on their own observations of the environment and the feedback provided by the central agent.
The communication channel is used to enable the individual agents to share information with each other and coordinate their actions. This allows the agents to learn to cooperate and achieve better overall performance than if they acted independently.
The PAT architecture has been used to train cooperative multi-agent systems in a variety of domains, including robotics, autonomous vehicles, and game playing. It has been shown to be effective in enabling agents to learn to cooperate and achieve better overall performance than individual agents acting independently.
