The Gumbel-Softmax estimator is a technique used in machine learning for sampling from a categorical distribution with a continuous relaxation. It is named after its two components: the Gumbel distribution and the Softmax function.

The Gumbel distribution is a continuous probability distribution used to model extreme value problems. It has two parameters: the location parameter μ and the scale parameter β. The Gumbel distribution can be expressed as G = −ln(−ln(U)), where U is a random variable uniformly distributed between 0 and 1.

The Softmax function is a mathematical function used to convert a vector of real numbers into a probability distribution. It is defined as the exponential of each element in the vector divided by the sum of all exponentials in the vector.

The Gumbel-Softmax estimator uses the Gumbel distribution to sample from the categorical distribution with a continuous relaxation, which is then converted into a probability distribution using the Softmax function. This technique is commonly used in reinforcement learning and generative models to sample from a categorical distribution without requiring a one-hot encoding, and allows for backpropagation through the sampling process.

The Gumbel-Softmax estimator can be represented mathematically as:

Let logits (unnormalized log-probabilities) be denoted by z = (z_1, z_2, ..., z_k), where k is the number of categories. Then, the Gumbel-Softmax estimator can be written as:

g_i = -log(-log(u_i)), where u_i are independent samples drawn from the uniform distribution between 0 and 1.

Then, we can add the g_i values to the logits z to obtain:

y_i = (z_i + g_i) / temperature

where temperature is a hyperparameter that controls the smoothness of the distribution. Finally, we can apply the Softmax function to y to obtain a probability distribution over the k categories. The Softmax function is defined as:

softmax(y)_i = exp(y_i) / sum(exp(y_j)), where j ranges from 1 to k.
