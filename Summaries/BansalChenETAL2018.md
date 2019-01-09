Authors study various regularization schemes based on weights orthogonality. Schemes are applied on state of the art CNN models achieving higher performance and faster convergence during training. The approach is to apply them early to speed up convergence and later replace them with l2 regularization to achieve good performance.

<center>METHODS</center>

- Soft Orthogonality $$\lambda \|W^tW - I\|^2$$

  constrains $$W$$ columns to be orthonormal

  doesn't apply full orthogonality, $$W^t W = W W^t = I$$
- Double Soft Orthogonality $$\lambda (\|W^tW - I\|^2 + \|WW^t - I\|^2)$$

  aims to constrain $$W$$ to an orthogonal matrix
- Mutual Coherence (MC) $$\lambda \|W^tW - I\|_\infty$$, $$\|.\|_\infty$$: maximum norm

  aims to minimize MC of $$W$$

  $$\mu_W = \max_{i\neq j} \frac{|< w_i, w_j >|}{\|w_i\|\|w_j\|}$$, $$w_i$$ $$W$$ column
  measures how close to parallel 2 columns can get
- Spectral Restricted Isometry $$\lambda \sigma( W^t W-I)$$, with $$\sigma(w) = \sup_{z\neq 0} \frac{\|W z\|}{\|z\|}$$

  requires all singular values of $$W$$ to be close to 1