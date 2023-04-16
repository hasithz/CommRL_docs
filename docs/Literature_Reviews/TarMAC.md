# TarMAC

TarMAC (Target-driven Multi-Agent Communication) is a deep reinforcement learning algorithm designed for cooperative multi-agent tasks that require communication and coordination between agents. The algorithm was proposed in a 2020 paper by researchers at the University of Oxford.
In TarMAC, each agent has its own communication policy, which determines how it sends and receives messages to and from other agents in the environment. The communication policy is represented by a neural network, which takes as input the observations of the agent and its neighbors, and outputs a message to be sent to each neighbor.

TarMAC also uses a target network for each agent, which is a copy of the communication policy network with delayed updates. The target network is used to stabilize the learning process and prevent the communication policies from diverging too far from their current values.
To encourage communication and coordination between agents, TarMAC introduces a target-driven approach. In this approach, the agents are given a common target that they must work together to achieve. The target is represented as a vector, which is initially set to a random value, and is updated over time based on the performance of the agents. The agents receive a reward based on their ability to achieve the target, which encourages them to communicate and coordinate their actions.

During training, TarMAC uses a multi-step learning process, where the agents first learn to communicate and coordinate in a simpler environment, and then gradually increase the complexity of the environment. This allows the agents to learn more complex communication strategies over time, and reduces the risk of the agents getting stuck in local optima.
TarMAC has been shown to be effective at learning communication and coordination strategies in a variety of cooperative multi-agent tasks, including navigation, transportation, and coordination tasks. It has also been shown to be more efficient than some other communication-based multi-agent RL algorithms, as it does not require explicit message passing between agents.

