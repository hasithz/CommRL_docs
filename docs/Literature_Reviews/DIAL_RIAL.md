# DIAL and RIAL 

J. N. Foerster, Y. M. Assael, N. de Freitas, and S. Whiteson, “Learning to Communicate with Deep Multi-Agent Reinforcement Learning.” arXiv, May 24, 2016. Accessed: Apr. 12, 2023. [Online]. Available: http://arxiv.org/abs/1605.06676


Reinforced Inter-Agent Learning (RIAL) and Differentiable Inter-Agent Learning (DIAL)
The former uses deep Q-learning
agents can backpropagate error derivatives through (noisy) communication channels
this approach uses centralised learning but decentralised execution.
reinforced inter-agent learning (RIAL), uses deep Q-learning [2] with a recurrent network to address partial observability
differentiable inter-agent learning (DIAL), is based on the insight that centralised learning affords more opportunities to improve learning than just parameter sharing.
disable experience replay to account for the non-stationarity that occurs when multiple agents learn concurrently, as it can render experience obsolete and misleading.
to account for partial observability, we feed in the actions u and m taken by each agent as inputs on the next time-step.
