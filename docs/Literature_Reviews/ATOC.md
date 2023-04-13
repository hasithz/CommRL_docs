# ATOC 


J. Jiang and Z. Lu, “Learning Attentional Communication for Multi-Agent Cooperation.” arXiv, Nov. 21, 2018. Accessed: Apr. 12, 2023. [Online]. Available: http://arxiv.org/abs/1805.07733


<!-- ATOC as an extension of actor-critic model, which is trained end-to-end by backpropagation. Since all agents share the parameters of the policy network, Q-network, attention unit, and communication channel, ATOC is suitable for large-scale multi-agent environments.

CommNet and BiCNet, where all agents communicate with each other all the time, our attention unit enables dynamic communication among agents only when necessary

This setting complies with the facts: (i) one of the purposes of communication is to share the partial observation, and adjacent agents could understand each other easily; (ii) cooperative decision making can be more easily accomplished among adjacent agents; (iii) all agents share one policy network, which means adjacent agents may have similar behaviors, however communication can increase the diversity of their strategies. There are three types of agents in the observable field of the initiator: other initiators; agents who have been selected by other initiators; agents who have not been selected. We assume a fixed communication bandwidth, which means each initiator can select at most m collaborators. The initiator first chooses collaborators from agents who have not been selected, then from agents selected by other initiators, finally from other initiators, all based on proximity.

The training of ATOC is an extension of DDPG. More concretely, consider a game with N agents, and the critic, actor, communication channel, and attention unit of ATOC is parameterized by θQ, θμ, θg, and θp, respectively. Note that we drop time t in the following notations for simplicity. -->

![ATOC architecture as in paper](https://raw.githubusercontent.com/hasithz/CommRL_docs/abe8d78ea94fd65dd614f2052b9cb55bde8a1f80/assets/images/ATOC.drawio.svg)

The Attentional Communication for Multi-Agent Cooperation (ATOC) is an extension of the actor-critic model, which is trained using backpropagation in an end-to-end fashion. All agents share the same policy network, Q-network, attention unit, and communication channel, making it suitable for large-scale multi-agent environments.

In contrast to communication protocols like CommNet and BiCNet, where all agents communicate with each other at all times, ATOC employs dynamic communication among agents only when necessary. This is based on the fact that communication is primarily used for sharing partial observations, and adjacent agents are better suited for cooperative decision-making. Additionally, having adjacent agents communicate with each other increases the diversity of their strategies while maintaining similarity in their behavior due to sharing the same policy network.

In ATOC, an initiator selects up to m collaborators from the agents within its observable field, which includes other initiators, agents selected by other initiators, and unselected agents. The training of ATOC is an extension of Deep Deterministic Policy Gradients (DDPG), where the critic, actor, communication channel, and attention unit are parameterized by θQ, θμ, θg, and θp, respectively. The model is trained end-to-end using backpropagation, allowing for efficient learning in large-scale multi-agent environments.
