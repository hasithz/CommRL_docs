# DIAL and RIAL 

J. N. Foerster, Y. M. Assael, N. de Freitas, and S. Whiteson, “Learning to Communicate with Deep Multi-Agent Reinforcement Learning.” arXiv, May 24, 2016. Accessed: Apr. 12, 2023. [Online]. Available: http://arxiv.org/abs/1605.06676


<!-- Reinforced Inter-Agent Learning (RIAL) and Differentiable Inter-Agent Learning (DIAL)
The former uses deep Q-learning
agents can backpropagate error derivatives through (noisy) communication channels
this approach uses centralised learning but decentralised execution.
reinforced inter-agent learning (RIAL), uses deep Q-learning [2] with a recurrent network to address partial observability
differentiable inter-agent learning (DIAL), is based on the insight that centralised learning affords more opportunities to improve learning than just parameter sharing.
disable experience replay to account for the non-stationarity that occurs when multiple agents learn concurrently, as it can render experience obsolete and misleading.
to account for partial observability, we feed in the actions u and m taken by each agent as inputs on the next time-step.
in DIAL the gradient term for m is the backpropagated error from the recipient of the message to the sender. Using this inter-agent gradient for training provides a richer training signal than the DQN loss for Qm in RIAL.
discretise/regularise unit (DRU(m_t^a))
combination of centralised learning and Q-networks makes it possible, not only to share parameters but to push gradients from one agent to another through the communication channel. Thus, while RIAL is end-to-end trainable within each agent, DIAL is end-to-end trainable across agents. Letting gradients flow from one agent to another gives them richer feedback, reducing the required amount of learning by trial and error, and easing the discovery of effective protocols.
Both Qu and Qm are trained using DQN with the following two modifications, which were found to be essential for performance. First, we disable experience replay to account for the non-stationarity that occurs when multiple agents learn concurrently, as it can render experience obsolete and misleading. Second, to account for partial observability, we feed in the actions u and m taken by each agent as inputs on the next time-step. Figure 1(a) shows how information flows between agents and the environment, and how Q-values are processed by the action selector in order to produce the action, uta, and message mta. Since this approach treats agents as independent networks, the learning phase is not centralised, even though our problem setting allows it to be. Consequently, the agents are treated exactly the same way during decentralised execution as during learning. -->

The paper "Learning to Communicate with Deep Multi-Agent Reinforcement Learning" by Foerster et al. introduced two approaches for inter-agent communication in multi-agent reinforcement learning: Reinforced Inter-Agent Learning (RIAL) and Differentiable Inter-Agent Learning (DIAL).

RIAL uses deep Q-learning with a recurrent network to address partial observability. The agents can backpropagate error derivatives through noisy communication channels, enabling them to learn to communicate effectively. RIAL uses centralised learning but decentralised execution.

DIAL, on the other hand, is based on the insight that centralised learning affords more opportunities to improve learning than just parameter sharing. It combines centralised learning and Q-networks, enabling gradients to be pushed from one agent to another through the communication channel. This end-to-end trainable approach is effective in reducing the amount of learning required by trial and error and easing the discovery of effective protocols.

Both RIAL and DIAL disable experience replay to account for the non-stationarity that occurs when multiple agents learn concurrently, as it can render experience obsolete and misleading. To account for partial observability, the actions taken by each agent are fed in as inputs on the next time-step.

In DIAL, the gradient term for the message is the backpropagated error from the recipient of the message to the sender, providing a richer training signal than the DQN loss for Qm in RIAL. The use of discretise/regularise units (DRUs) is also introduced to improve the stability of training.

Foerster et al. demonstrated the effectiveness of these approaches in several challenging environments, such as the cooperative navigation task and the predator-prey pursuit game.

(Work taken from the paper "Learning to Communicate with Deep Multi-Agent Reinforcement Learning" by J. N. Foerster, Y. M. Assael, N. de Freitas, and S. Whiteson, accessed on Apr. 12, 2023, and available online at http://arxiv.org/abs/1605.06676.)