# CommNet (Communication Neural Net)

S. Sukhbaatar, A. Szlam, and R. Fergus, “Learning Multiagent Communication with Backpropagation.” 2016.


![CommNet architecture as in paper](https://raw.githubusercontent.com/hasithz/CommRL_docs/abe8d78ea94fd65dd614f2052b9cb55bde8a1f80/assets/images/commnet%20and%20communication.drawio.svg)

-    CommNet is a multi-agent reinforcement learning architecture that enables agents to communicate with each other to solve complex tasks.
-    Each agent in CommNet has a communication module that enables it to send and receive messages to and from other agents.
-    The communication module consists of shared fully connected layers and element-wise nonlinearity that is used to encode and decode messages.
-    The messages sent and received by agents can contain any information that is relevant to the task, such as the current state of the environment, the actions of other agents, or the intentions of the agents.
-    Each agent's communication module combines the messages it has received with its own internal state to produce an output message that is sent to the other agents.
-    The output message from each agent is combined with the output messages from the other agents using a weighted sum to produce a joint message that represents the collective knowledge of the agents.
-    The joint message is fed into a task-specific neural network that produces the action taken by each agent based on the current state of the environment and the messages received from the other agents.
-    The joint message is also fed back into the communication module of each agent, updating their internal state and enabling them to send and receive more informative messages in the next time step.
-    This iterative process of communication and decision-making continues until the task is completed or a stopping criterion is met.


The communication module in CommNet consists of shared fully connected layers and element-wise nonlinearity. Here's a more detailed description of the architecture:

-    The communication module receives input from three sources: the state of the environment, messages received from other agents, and the internal state of the module itself.
-    The inputs are first concatenated and then fed into a shared fully connected layer.
-    The output of the fully connected layer is then passed through an element-wise nonlinearity, such as a rectified linear unit (ReLU) or a sigmoid function.
-    The resulting output is the encoded message that is sent to the other agents.
-    To decode messages received from other agents, the communication module uses a similar architecture: the received messages are concatenated with the internal state of the module and fed into another fully connected layer and element-wise nonlinearity.
-    The output of the decoding layer represents the information that the agent has extracted from the messages received from other agents.
-    The output of the encoding and decoding layers can be further processed or combined with other information in the architecture before being used as the input to the next module.

The communication module in CommNet is designed to be flexible and adaptable, allowing agents to learn to encode and decode messages that are relevant to the task they are trying to solve. By sharing the same fully connected layers, the communication module encourages agents to learn a common representation of the messages, facilitating coordination and cooperation between agents.


CommNet is a neural network that enables collaborative decision-making among multiple agents by allowing them to communicate with one another. It is a feed-forward network that maps inputs from all agents to their corresponding actions. Each agent has its own set of dedicated units and can communicate with other agents via a broadcasting channel using their hidden states as messages. The incoming messages from other agents are averaged and used as input for the next layer. Nonetheless, this approach may face scalability issues when dealing with a large number of agents as it relies on a single, large network for all agents. Notably, CommNet has also been applied in natural language processing for abstractive summarization.