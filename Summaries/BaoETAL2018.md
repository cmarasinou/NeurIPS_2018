Authors introduce a new activation function to replace the softmax layer in DNNs. The new function is using part of the data as a template and interpolates for the training data. The reasoning for such an approach comes from the fact that softmax produces essentially a linear model of the deep features (last hidden layer output), without taking into consideration the manifold structure of these deep features. The interpolation is done by harmonic extension, setting up an energy functional and minimizing it.

<center>METHODS</center>

- We are interested in the interpolation of a function $$u(x)$$ (with $$x\in X$$ representing the input of a DNN and u the output), given it's values for some points $$x\in X^{te}$$ (template)

Using harmonic extension we can perform the interpolation by minimizing the functional

$$
\mathcal{E}[u] = \frac{1}{2} \sum\limits_{x_1,x_2 \in X} w(x_1,x_2) (u(x_1) -u(x_2))^2
$$

with boundary conditions $$u(x)=g(x)$$ for $$x\in X^{te}$$, where $$w(x,y)$$ is a weight function (typically a Gaussian)  $$g(x)$$ is known (ground truth labels)

Minimizing the functional we get the Euler-Lagrange (EL) equations

$$
\sum\limits_{x_2\in X} (w(x_1,x_2) +w(x_2,x_1)) (u(x_1)-u(x_2)) = 0, \quad x_1\in X/X^{te}
$$

with the boundary conditions applying to the rest of the points in X.

- In the algorithm $$u(x)$$ is named $$WNLL(X, X^{te}, Y^{te})$$. Note that it depends on the template dataset because of the interpolation process.

- Issue: Backpropagation of WNLL Loss is difficult due to it's complexity. An approximation is adopted

$$
\frac{\partial\mathcal{L}^{WNLL}}{\partial y} \frac{\partial y}{\partial x}
\approx
\frac{\partial\mathcal{L}^{Linear}}{\partial y} \frac{\partial y}{\partial x}
$$

- Training:
  1. First perform N1 steps with Linear (Softmax)
  2. Next, perform N2 steps with WNLL

![Training](./assets/images/bao_1.png)

Notice that the interpolation is done on the deep features of the DNN (and not just the input)

- Testing: Using only the WNLL branch

- Benefits:
  - Model learns features both from linear classifiaction and manifold Learning
  - Method provides a perturbation to avoid getting stuck in bad local minima

- Limitations:
  - Batch size should be quasilinear with number of classes, otherwise the interpolation is invalid
  - Backpropagation was approximated
