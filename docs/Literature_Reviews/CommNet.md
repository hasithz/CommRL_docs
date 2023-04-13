# CommNet (Communication Neural Net)

This architecture was presented on the paper `learning multiagent communication with backpropagation` 

```mermaid
flowchart LR
    Input -- State of environment, messages received from other agents, internal state of module --> Communication Module
    Communication Module -- Shared fully connected layers, element-wise nonlinearity --> Output Message
    Output Message -- Sent to other agents --> Weighted Sum
    Weighted Sum -- Combined with output of other modules --> Task-Specific Neural Network
    Task-Specific Neural Network -- Produces action taken by each agent -->
