Authors study spectrum of Fisher information matrix for a single-hidden-layer neural network with square loss, random Gaussian weights and input and in the limit of large width. Fisher information matrix is indicative of the local curvature of a function. The function under study is the loss function. The results are mostly analytical, with experimental verification. They show that for non-linear networks the spectrum is non-degenerate, in contrast to linear networks. Also, tuning the non-linearity can make the first-order optimization more efficient.

<center>METHODS</center>
- Given matrix $$M$$, spectral density is $$\rho_M(\lambda) = \frac{1}{n} \sum\limits_{j=1}^n \delta(\lambda - \lambda_j(M))$$
One method to find $$\rho_M$$ is the __moments method__:
  - Define Stieltjes tranform $$G(z) = \int \frac{\rho_M(t)}{z-t} dt$$
  - Then $$\rho_M(\lambda) = - (1/\pi) \lim_{\epsilon\to 0^+} im G(\lambda+i \epsilon)$$
  - Expand as Laurent series $$G(z) = \sum\limits_{k=0}^\infty \frac{m_k}{z^{k+1}}$$
  where the moments $$m_k = \int dt \rho_M(t) t^k$$
- In the case of square loss the fisher information matrix is given by
$$H_{ij}^{(0)} = E_X \sum_\alpha \frac{\partial \hat Y_\alpha}{\partial\theta_i}\frac{\partial \hat Y_\alpha}{\partial\theta_j}$$
with $$\theta_i$$ network parameters, $$\hat Y$$ network predictions, $$\alpha$$ index
- Applying the moments method they find analytical results for  linear and non-linear networks
- Linear network exhibits high-degeneracy, i.e. half the eigenvalues = 0
- Non-linear networks have activation function with Gaussian mean = 0
  - $$G(z)$$ found in integral form
  - $$G(z)$$ branch points and poles found
  - These encode information about $$\rho(\lambda)$$
  - $$\rho(\lambda)$$ is found numerically for different activation functions
  
![spectral_densities](./assets/images/pennington_1.png)

- Paper initiates work of studying deep learning using __random matrix theory__
