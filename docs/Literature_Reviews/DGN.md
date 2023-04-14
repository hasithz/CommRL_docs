# DGN (Graph convolutional reinforcement learning)


problem is formulated as Decentralized Partially Observable Markov Decision Process (DecPOMDP),

DGN consists of three types of modules: observation encoder, convolutional layer and Q network,

The convolutional layer integrates the feature vectors in the local region (including node i and its neighbors Bi) and generates the latent feature vector h′t

By stacking two layers, node i can get the output of the first convolutional layer of the nodes in one-hop, which contains the information from nodes in two-hop. However, regardless of how many convolutional layers are stacked, node i only communicates with its neighbors. This makes DGN practical in real-world applications, where each agent has limited communication range.

merge all agents’ feature vectors at time t into a feature matrix F t with size N×L in the order of index, where N is the number of agents and L is the length of feature vector. Then, we construct an adjacency matrix Ct i with size (|Bi| + 1) × N for agent i, where the first row is the one-hot representation of the index of node i, and the jth row, j = 2, . . . , |Bi| + 1, is the one-hot representation of the index of the (j − 1)th neighbor. Then, we can obtain the feature vectors in the local region of node i by Ct i × F t


Inspired by DenseNet (Huang et al., 2017), for each agent, the features of all the preceding layers are concatenated and fed into the Q network, so as to assemble and reuse the observation representation and features from different receptive fields, which respectively have distinctive contributions to the strategy that takes the cooperation at different scopes into consideration.

Like CommNet (Sukhbaatar et al., 2016), DGN can also be seen as a factorization of a centralized policy that outputs actions for all the agents to optimize the average expected return.

A graph convolutional network (GCN) takes as input the feature matrix that summarizes the attributes of each node and outputs a node-level feature matrix.

## RELATION KERNEL

Convolution kernels integrate the feature in the receptive field to extract the latent feature. One of the most important properties is that the kernel should be independent from the order of the input feature vectors. Mean operation as in CommNet (Sukhbaatar et al., 2016) meets this requirement, but it leads to only marginal performance gain.
