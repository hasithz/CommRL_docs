# DGN (Graph convolutional reinforcement learning)

J. Jiang, C. Dun, T. Huang, and Z. Lu, “Graph Convolutional Reinforcement Learning.” arXiv, Feb. 11, 2020. Accessed: Apr. 14, 2023. [Online]. Available: http://arxiv.org/abs/1810.09202


![DGN architecture as in paper](https://raw.githubusercontent.com/hasithz/CommRL_docs/17137889e1a06f72102cb3b2884ac6af08041954/assets/images/DGN.drawio.svg)

DGN consists of three modules: encoder, convolutional layer, and Q network. All agents share weights and gradients are accumulated to update the weights.

The paper introduces the Decentralized Graph Convolutional Network (DGN) for solving Decentralized Partially Observable Markov Decision Process (DecPOMDP) problems. DGN consists of three modules: observation encoder, convolutional layer, and Q network.

The convolutional layer generates a latent feature vector by integrating feature vectors from the local region (node i and its neighbors Bi). By stacking two layers, node i can obtain information from nodes in two-hop, while still only communicating with its neighbors. This makes DGN practical for real-world applications where agents have limited communication range.

To obtain feature vectors in the local region of node i, all agents' feature vectors are merged into a feature matrix Ft, and an adjacency matrix Cti is constructed for each agent. Feature vectors can be obtained by multiplying Cti by Ft.

Inspired by DenseNet, DGN concatenates the features of all preceding layers for each agent and feeds them into the Q network. This approach assembles and reuses observation representation and features from different receptive fields to consider cooperation at different scopes.

DGN can also be seen as a factorization of a centralized policy, similar to CommNet, that outputs actions for all agents to optimize the average expected return. A graph convolutional network (GCN) takes the feature matrix summarizing each node's attributes as input and outputs a node-level feature matrix.

The paper also emphasizes the importance of convolution kernels that are independent of the input feature vector's order. While the mean operation, as in CommNet, meets this requirement, it only marginally improves performance.