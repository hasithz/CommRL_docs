# VAIN

Y. Hoshen, “VAIN: Attentional Multi-agent Predictive Modeling.” arXiv, Sep. 28, 2018. Accessed: Apr. 15, 2023. [Online]. Available: http://arxiv.org/abs/1706.06122

![VAIN architecture as in paper](https://raw.githubusercontent.com/hasithz/CommRL_docs/c1c0b88de33f0bb84935798488ff23659de9affb/assets/images/VAIN.drawio.svg)

<!-- A schematic of a single-hop VAIN: i) The agent features Fi are embedded by singleton encoder Es() to yield encoding es i and communications encoder Ec() to yield vector ec i and attention vector ai ii) For each agent an attention-weighted sum of all embeddings ec i is computed Pi = ∑ j wi,j ∗ ec j. The attention weights wi,j are computed by a Softmax over −||ai − aj||2. The diagonal wi,i is set to zero to exclude self-interactions. iii) The singleton codes es i are concatenated with the pooled feature Pi to yield intermediate feature Ci iv) The feature is passed through decoding network D() to yield per-agent vector oi. For Regression: oi is the final output of the network. vii) For Classification: oi is scalar and is passed through a Softmax.



In this section we model the interaction between N agents denoted by A1...AN . The output can be either be a prediction for every agent or a system-level prediction (e.g. predict which agent will act next). Although it is possible to use multiple hops, our presentation here only uses a single hop (and they did not help in our experiments). Features are extracted for every agent Ai and we denote the features by Fi. The features are guided by basic domain knowledge (such as agent type or position).

We use two agent encoding functions: i) a singleton encoder for single-agent features Es() ii) A communication encoder for interaction with other agents Ec(). The singleton encoding function Es() is applied on all agent features Fi to yield singleton encoding es i

We define the communication encoding function Ec(). The encoding function is applied to all agent features Fi to yield both encoding ec i and attention vector ai. The attention vector is used for addressing the agents with whom information exchange is sought. Ec() is implemented by fully connected neural networks (from now FCNs).

For each agent we compute the pooled feature Pi, the interaction vectors from other agents weighted by attention. We exclude self-interactions by setting the self-interaction weight to 0:

This is in contrast to the average pooling mechanism used in CommNets and we show that it yields better results. The motivation is to average only information from relevant agents (e.g. nearby or particularly influential agents). The weights wi,j = Sof tmaxj(−||ai − aj||2) give a measure of the interaction between agents. Although naively this operation scales quadratically in the number of agents, it is multiplied by the feature dimension rather by a full E() evaluation and is therefore significantly smaller than the cost of the (linear number) of E() calculations carried out by the algorithm. In case the number of agents is very large (>1000) the cost can still be mitigated: The Softmax operation often yields a sparse matrix, in such cases the interaction can be modeled by the K-Nearest neighbors (measured by attention). The calculation is far cheaper than evaluating Ec() O(N 2) times as in IN. In cases where even this cheap operation is too expensive we recommend to default to CommNets which truly have an O(N) complexity. The pooled-feature Pi is concatenated to the original features Fi to form intermediate features Ci

The features Ci are passed through decoding function D() which is also implemented by FCNs. The result is denoted by o

For regression problems, oi is the per-agent output of VAIN. For classification problems, D() is designed to give scalar outputs. The result is passed through a softmax layer yielding agent probabilities:

everal advantages of VAIN over Interaction Networks [9] are apparent: Representational Power: VAIN does not assume that the interaction graph is pre-specified (in fact the attention weights wi,j learn the graph). Pre-specifying the graph structure is advantageous when it is clearly known e.g. spring-systems where locality makes a significant difference. In many multi-agent scenarios the graph structure is not known apriori. Multiple-hops can give VAIN the potential to model higher-order interactions than IN, although this was not found to be advantageous in our experiments. -->

In the paper "VAIN: Attentional Multi-agent Predictive Modeling" by Y. Hoshen, the author presents a novel approach to modeling the interactions between N agents, A1...AN. The model can generate predictions for every agent or system-level predictions. It uses features guided by basic domain knowledge such as agent type or position.

### The model employs two agent encoding functions:

-    A singleton encoder (Es) for single-agent features.
-    A communication encoder (Ec) for interaction with other agents.

The singleton encoding function Es() is applied to all agent features Fi to yield singleton encoding esi. The communication encoding function Ec() is applied to all agent features Fi to generate both encoding eci and attention vector ai, which is used for addressing the agents with whom information exchange is sought. Ec() is implemented by fully connected neural networks (FCNs).

For each agent, the model computes the pooled feature Pi, which is the interaction vectors from other agents weighted by attention. Self-interactions are excluded by setting the self-interaction weight to 0. This approach is different from the average pooling mechanism used in CommNets and is shown to yield better results. The motivation is to average only information from relevant agents, such as nearby or particularly influential agents.

The pooled feature Pi is concatenated to the original features Fi to form intermediate features Ci. These features are passed through a decoding function D(), also implemented by FCNs, resulting in output o. For regression problems, oi is the per-agent output of VAIN. For classification problems, D() is designed to give scalar outputs, which are then passed through a softmax layer to yield agent probabilities.

### VAIN offers several advantages over Interaction Networks:

-    Representational Power: VAIN does not assume that the interaction graph is pre-specified, allowing the attention weights wi,j to learn the graph. This is particularly useful when the graph structure is not known a priori in many multi-agent scenarios.
-    Potential for higher-order interactions: Although not found to be advantageous in the experiments, multiple hops can give VAIN the potential to model higher-order interactions than Interaction Networks.

In summary, the VAIN model offers a flexible and powerful approach to modeling multi-agent interactions and generating agent or system-level predictions. It leverages attention mechanisms and encoding functions to capture relevant agent information and model interactions effectively.