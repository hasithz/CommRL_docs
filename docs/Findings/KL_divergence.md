# Kullback-Leibler divergence

Kullback-Leibler (KL) divergence is a measure of the difference between two probability distributions. It is named after the mathematicians Solomon Kullback and Richard Leibler who introduced it in 1951.

KL divergence measures the amount of information lost when approximating one probability distribution with another. It is often used in machine learning, information theory, and statistics.

The formula for KL divergence between two probability distributions `P` and `Q` is:

$$ KL(P || Q) = Σ P(x) log(P(x) / Q(x)) $$

where `x` represents the possible outcomes of a random variable. `P(x)` is the probability of `x` according to distribution `P`, and `Q(x)` is the probability of `x` according to distribution `Q`. The sum is taken over all possible values of `x`.

KL divergence is not symmetric, that is, `KL(P || Q)` is not equal to `KL(Q || P)`. It is always non-negative, and it is zero only when P and Q are identical.

KL divergence has many applications in machine learning, including density estimation, clustering, and model selection. It is commonly used as a loss function for training generative models, such as variational autoencoders and generative adversarial networks.

In summary, KL divergence is a powerful tool for measuring the difference between probability distributions and is widely used in various fields, especially in machine learning.