Authors develop a generative model for data synthesis, based on data manifold structure rather than data density. The model captures manifold structure with a diffusion kernel. Then, it randomly generates points around the manifold focusing on sparse areas. Last, it pulls the points towards the structure of the manifold. The result is data, uniformly distributed on the data manifold. The method is tested on imbalanced datasets for classification and clustering tasks.

<center>METHODS</center>

_Markov Matrix $$P$$__: Defines a diffusion process which can capture the diffusion geometry of a manifold
$$
P_{i,j} = \mathcal{P}(x_i, x_j) = [D^{-1}K]_{ij}
$$
Gaussian kernel, $\sigma$: kernel bandwidth
$$
K_{ij} = \mathcal{K}(x_i,x_j) =  - expo \left(- \frac{|x_i - x_j|^2}{2 \sigma^2} \right)
$$
Total connectivity matrix: measure of density
$$
D_ij = diag(\hat d(i)) = \sum_j K_{ij}
$$
Another possible kernel: Measure-based Gaussian Correlation, $$X$$: set of reference points, $$\mu$$ measure
$$
\hat K_{ij} = \sum\limits_{r \el X} \mathcal{K}(x_i, r) \mathcal{K}(x_j, r) \mu(r)
$$

<center>ALGORITHM</center>

Given $$X = \{x_1, \cdots, x_N\}$$
1. Compute $$K, \hat d (i)$$
2. Compute sparsity $$\hat s (i) = (\hat d(i))^{-1}$$, reciprocal of density
3. For each point in $$X$$:
  Sample $$\hat l(i)$$ points from localized Gaussian $$\mathcal{N}(\x_i, \Sigma_i)$$
  where $$\Sigma_i$$ is the covariance matrix and $$\hat l(i)$$ is analogous to sparsity at $$x_i$$
4. Compute
  $$
 \mathcal{K}(y_i,y_j) =  \sum\limits_{r \el X} \mathcal{K}(y_i, r) \mathcal{K}(y_j, r) \hat \sigma(r)
  $$
  averaging $$Y_0$$ points according to neighbors in $$X$$
5. Compute corresponding Markov matrix $$\hat P$$
6. Pull $$Y_0$$ points closer to manifold structure applying $$\hat P$$
  $$
  Y_0 \to Y_t = \hat P^t Y_0
  $$
  $$t$$: number of times $$\hat P$$ is applied, when larger we average over larger area in $$X$$
7. Rescale $$Y_t$$ to range of original values in $$X$$
