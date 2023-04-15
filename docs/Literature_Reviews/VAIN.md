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

## VIN (Visual Interaction Networks)

N. Watters, A. Tacchetti, T. Weber, R. Pascanu, P. Battaglia, and D. Zoran, “Visual Interaction Networks.” arXiv, Jun. 05, 2017. Accessed: Apr. 15, 2023. [Online]. Available: http://arxiv.org/abs/1706.01433


![VIN architecture as in paper](https://raw.githubusercontent.com/hasithz/CommRL_docs/1272d610085f85313f57077d09d4bb5bc074337e/assets/images/VIN.drawio.svg)

<!-- Our Visual Interaction Network (VIN) learns to produce future trajectories of objects in a physical system from only a few video frames of that system. The VIN is depicted in Figure 1 (best viewed in color), and consists of the following components: 


- The visual encoder takes a triplet of frames as input and outputs a state code. A state code is a list of vectors, one for each object in the scene. Each of these vectors is a distributed representation of the position and velocity of its corresponding object. We apply the encoder in a sliding window over a sequence of frames, producing a sequence of state codes. See Section 2.1 and Figure 2a for details. 

- The dynamics predictor takes a sequence of state codes (output from a visual encoder applied in a sliding-window manner to a sequence of frames) and predicts a candidate state code for the next frame. The dynamics predictor is comprised of several interaction-net cores, each taking input at a different temporal offset and producing candidate state codes. These candidates are aggregated by an MLP to produce a predicted state code for the next frame. See Section 2.2 and Figure 2b for details. 

- The state decoder converts a state code to a state. A state is a list of each object’s position/velocity vector. The training targets for the system are ground truth states. See Section 2.3 for details.

## Visual Encoder



The visual encoder is a CNN that produces a state code from a sequence of 3 images. It has a frame pair encoder Epair shown in Figure 2a which takes a pair of consecutive frames and outputs a candidate state code. This frame pair encoder is applied to both consecutive pairs of frames in a sequence of 3 frames. The two resulting candidate state codes are aggregated by a slot-wise MLP into an encoded state code. Epair itself applies a CNN with two different kernel sizes to a channel-stacked pair of frames, appends constant x, y coordinate channels, and applies a CNN with alternating convolutional and max-pooling layers until unit width and height. The resulting tensor of shape 1 × 1 × (Nobject · Lcode) is reshaped into a state code of shape Nobject × Lcode, where Nobject is the number of objects in the scene and Lcode is the length of each state code slot. The two state codes are fed into an MLP to produce the final encoder output from the triplet. See the Supplementary Material for further details of the visual encoder model. One important feature of this visual encoder architecture is its weight sharing given by applying the same Epair on both pairs of frames, which approximates a temporal convolution over the input sequence.

Another important feature is the inclusion of constant coordinate channels (an x- and y-coordinate meshgrid over the image), which allows positions to be incorporated throughout much of the processing. Without the coordinate channels, such a convolutional architecture would have to infer position from the boundaries of the image, a more challenging task.

## Dynamics Predictor

The dynamics predictor is a variant of an Interaction Network (IN) [2], a state-to-state physical predictor model summarized in Figure 2b. The main difference between our predictor and a vanilla IN is aggregation over multiple temporal offsets. Our predictor has a set of temporal offsets (in practice we use {1, 2, 4}), with one IN core for each. Given an input state code sequence, for each offset t a separate IN core computes a candidate predicted state code from the input state code at index t. A slot-wise MLP aggregator transforms the list of candidate state codes into a predicted state code. See the Supplementary Material for further details of the dynamics predictor model. As with the visual encoder, we explored many dynamics predictor architectures (some of which we compare as baselines below). The temporal offset aggregation of this architecture enhances its power by allowing it to accommodate both fast and slow movements by different objects within a sequence of frames. The factorized representation of INs, which allows efficient learning of interactions even in scenes with many objects, is an important contributor to our predictor architecture’s performance.

## State Decoder

The state decoder is simply a linear layer with input size Lcode and output size 4 (for a position/velocity vector). This linear layer is applied independently to each slot of the state code. We explored more complicated architectures, but this yielded the best performance. The state decoder is applied to both encoded state codes (for auxiliary encoder loss) and predicted state codes (for prediction loss). -->

The paper "Visual Interaction Networks" by N. Watters et al. introduces a model called Visual Interaction Network (VIN) that learns to predict future trajectories of objects in a physical system using only a few video frames of that system. The VIN consists of the following components:

![VIN Encoder in paper](https://github.com/hasithz/CommRL_docs/blob/master/assets/images/VIN%20Encoder.png?raw=true)

-    **Visual Encoder**: This is a Convolutional Neural Network (CNN) that produces a state code from a sequence of three images. The state code is a list of vectors, one for each object in the scene, representing the position and velocity of the object. The visual encoder uses a frame pair encoder (Epair) applied to both consecutive pairs of frames in a sequence of three frames, and the two resulting candidate state codes are aggregated by a slot-wise MLP into an encoded state code.

-    **Dynamics Predictor**: This component takes a sequence of state codes (output from the visual encoder) and predicts a candidate state code for the next frame. It is a variant of an Interaction Network (IN) and comprises several interaction-net cores, each taking input at a different temporal offset and producing candidate state codes. These candidates are aggregated by an MLP to produce a predicted state code for the next frame.

-    **State Decoder**: This component converts a state code to a state, which is a list of each object's position/velocity vector. The training targets for the system are ground truth states. The state decoder is a linear layer applied independently to each slot of the state code.

The visual encoder's architecture features weight sharing and the inclusion of constant coordinate channels, which allow positions to be incorporated throughout much of the processing. The dynamics predictor's architecture allows efficient learning of interactions even in scenes with many objects and accommodates both fast and slow movements by different objects within a sequence of frames. The state decoder is applied to both encoded state codes (for auxiliary encoder loss) and predicted state codes (for prediction loss).

Overall, the Visual Interaction Network offers a way to predict future trajectories of objects in a physical system using only a few video frames, leveraging the power of visual encoding, interaction networks, and state decoding.