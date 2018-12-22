Authors develop self-explaining models as a generalization of linear models. Models are locally linear allowing for interpretability and globally non-linear allowing for good performance. Locality is imposed by a Lipschitz-like condition, which is implemented in the algorithm as a loss regularization term. The explanation for a certain input is given as a set $$\{ (h_i(x), \theta_i(x))\}_i^k$$ with $$h_i(x)$$ a basis of concepts (interpretable features) and $$\theta_i(x)$$ their influence scores.

<center>METHODS</center>

- Generalizing linear Models
  1. Linear model $$f(x) = \theta^T x$$  
  2. Generalizing coefficients $$f(x) = \theta(x)^T x$$  
    $$\theta(x)$$ smooth, to maintain interpretability
  3. Generalizing features $$f(x) = \theta(x)^T h(x)$$
  $$h(x)$$ interpretable basis concepts, generally not same size as $$x$$
  4. Generalizing aggregation $$f(x) = g_1(\theta(x), h_1(x), \cdots, \theta_k(x), h_k(x))$$
  g doesn't have to be the sum of it's arguments

- Defining Locality
  $$\theta$$ __locally difference bounded__ by h if
  $$||\theta(x)-\theta(x_0)|| \leq L ||h(x)-h(x_0)||$$
  where $$x$$ in the neighborhood of $$x_0$$

- Self-explaining model definitions

  Structure: $$f(x) = g_1(\theta(x), h_1(x), \cdots, \theta_k(x), h_k(x))$$

  With conditions:
  1. g: monotone & additively separable
  2. $$\nabla g \geq 0$$
  3. $$\theta$$ __locally difference bounded__ by $$h$$
  4. $$h_i(x)$$ interpretable
  5. k: small

- Enforcing Locality of $$\theta(x)$$ in the basis $$h(x)$$
  - Want $$\nabla_z f \approx f(z_0)$$, where $$z:=h(x)$$
  - Notice: $$\nabla_x f = \nabla_z f \; \partial h /\partial x$$, calculable
  - We introduce the regularization term $$~\|\|\nabla_x f - \theta(x)^T \partial h / \partial x\|\|$$

- Enforcing interpretability of $$h(x)$$
  - Preserve relevant information, e.g. autoencoder (with introducing an extra loss regularization term)
  - Non-overlapping concepts, e.g. enforcing sparsity
  - Human-understanding, e.g. show training examples that maximize concept

- Overall model

![Model](./assets/images/alvarez_1.png)
