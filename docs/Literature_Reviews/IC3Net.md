# IC3Net (Individualized Controlled Continuous Communication Model)

A. Singh, T. Jain, and S. Sukhbaatar, “Learning when to Communicate at Scale in Multiagent Cooperative and Competitive Tasks.” arXiv, Dec. 23, 2018. Accessed: Apr. 14, 2023. [Online]. Available: http://arxiv.org/abs/1812.09755


![IC3Net architecture as in paper](https://raw.githubusercontent.com/hasithz/CommRL_docs/1c5db1af39a210335d3399f9a9505dc417b83cbb/assets/images/IC3Net.drawio.svg)


An overview of IC3Net. (Left) In-depth view of a single communication step. LSTM gets hidden state, ht and cell state, st (not shown) from previous time-step. Hidden state ht is passed to Communication-Action module fg for a communication binary action gt. Finally, communication vector ct is calculated by averaging hidden states of other active agents gated by their communication action act and is passed through a linear transformation C before fed to LSTM along with the observation. (Right) High-level view of IC3Net which optimizes individual rewards rt for each agent based on observation ot.

<!-- has better training efficiency than simple continuous communication model, and can be applied to semi-cooperative and competitive settings along with the cooperative settings

C3Net controls continuous communication with a gating mechanism and uses individualized rewards for each agent to gain better performance and scalability while fixing credit assignment issues.

tasks that have done in the paper are
We propose Individualized Controlled Continuous Communication Model (IC3Net), in which each agent is trained with its individualized reward and can be applied to any scenario whether cooperative or not. 2. We empirically show that based on the given scenario–using the gating mechanism–our model can learn when to communicate. The gating mechanism allows agents to block their communication; which is useful in competitive scenarios. 3. We conduct experiments on different scales in three chosen environments including StarCraft and show that IC3Net outperforms the baselines with performance gaps that increase with scale. The results show that individual rewards converge faster and better than global rewards.

we move away from the single big network controller approach. Instead, we consider multiple big networks with shared parameters each controlling a single agent separately. Each big network consists of multiple LSTM networks, each processing an observation of a single agent. However, only one of the LSTMs need to output an action because the big network is only controlling a single agent. Although this view has a little effect on the implementation (we can still use a single big network in practice), it allows us to train each agent to maximize its individual reward instead of a single global reward. This has two benefits: (i) it allows the model to be applied to both cooperative and competitive scenarios, (ii) it also helps resolve the credit assignment issue faced by many multi-agent -->

The Individualized Controlled Continuous Communication Model (IC3Net) is a multi-agent communication model that uses a gating mechanism to control communication between agents and individualized rewards for each agent. This allows for better training efficiency and scalability, and can be applied to a variety of scenarios including cooperative, semi-cooperative, and competitive settings.

In IC3Net, each agent is trained with its own individual reward, which allows for faster and better convergence compared to using a single global reward. The model is implemented using multiple big networks with shared parameters, with each big network controlling a single agent separately. This approach helps resolve the credit assignment issue faced by many multi-agent systems, and allows for the model to be applied to both cooperative and competitive scenarios.

The authors conducted experiments on three environments, including StarCraft, and showed that IC3Net outperformed baselines with increasing performance gaps as the scale of the environment increased. The gating mechanism in IC3Net allowed agents to learn when to communicate, and could be used to block communication in competitive scenarios. The results demonstrate the effectiveness of IC3Net in multi-agent communication and highlight its potential for use in large-scale environments. The article used for this information is "Learning when to Communicate at Scale in Multiagent Cooperative and Competitive Tasks" by A. Singh, T. Jain, and S. Sukhbaatar.