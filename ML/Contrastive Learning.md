#DL 
#### What is it and how it works?
![[Pasted image 20230329141358.png]]
1. Given an input $x$ we generate with [[Data augmentation]] two different representations: $\tilde{x_i}, \tilde{x_j}$ 
2. With a feature extractor $f$ - neural network we obtain two representations: $h_i, h_j$
3. Then, we project them with $g$ and calculate their similarity.

Once training is finished, we don't need $g$ anymore, just $f$.

#### Loss function
$$

l \; (i, j) = -\log \frac{\exp (\;\text{sim}(z_i, z_j)\; / \;\tau) }{\sum_{k=1}^{2N} \mathbb{1}_{k \neq i} \exp (\;\text{sim} (z_i, z_k) \;/ \;\tau) }

$$
$$

L = \frac{1}{2N} \sum_{k=1}^N [ \; l(k, \;k+N) + l(k+N, \;k)\;]

$$
where $sim$ is a **normalised dot-product**.

We have $2N$ pairs, we want to $z_i, z_j$ to be similar as much as possible (**dot-product** goes to $1$). 
Parameter $\tau$ is a temperature