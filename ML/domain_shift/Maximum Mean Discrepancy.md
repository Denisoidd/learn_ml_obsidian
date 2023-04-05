#domain_shift 

Or short - **MMD**

**Idea**
Suppose, we have two feature vectors: $\phi(X)$ and $\phi(Y)$ and we define $K$ is a Kernel function, where: 
$$
K(X,Y) = \langle\phi(X), \phi(Y) \rangle
$$

Then we need to calculate the average over each coordinate the results $K(X,Y)$, $K(X,X)$, $K(Y,Y)$

$$
\begin{align*}
MMD^2(P, Q) = \lVert \mu_P - \mu_Q \rVert = \langle\mu_P,\mu_P\rangle - 2\langle\mu_P, \mu_Q\rangle + \langle \mu_Q,\mu_Q\rangle \\= E_P[K(X, X)] -2E_{P,Q}[K(X,Y)] + E_Q[K(Y, Y)]
\end{align*}
$$
**MMD** could be used as a loss function. The lower **MMD** the closer two distributions:
![[Pasted image 20230405132527.png]]