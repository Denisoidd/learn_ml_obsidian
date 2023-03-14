#DL 
### Parameter update schemes
* *SGD*
	* Jittering a lot
* *Momentum update*
	* Integrating velocity
		* Gradient update:
			* $v_{t}=\mu v_{t-1} - lr * \nabla x$ 
			* $x_t = x_{t-1} + v$
* *Nesterov Momentum update*
	*![[Pasted image 20230309100802.png]] 
	* Evaluate gradient at the next step and calculate *actual step* 
		* $v_t = \mu v_{t-1} - \epsilon \nabla x (\theta_{t-1} + \mu v_{t-1})$
		* $\theta_t = \theta_{t-1} + v_t$
* AdaGrad
	* Divide standard *SGD* by a *cache* variable that keeps buiding on with training process.
	* Not okay because of constantly growing *cache*
* RMSProp
	* *cache* is decayed over time
		*![[Pasted image 20230310151353.png]]
* Adam
	* RMSProp + Momentum
	* There is a warm-up for m, v
		![[Pasted image 20230310151422.png]]

### Learning rate update
* Exponential decay $\alpha = \alpha_0 e^{-kt}$
* Do not really need with Adam
* *Warm-up, cosine, linear, inverse sqrt*
### Second order optimization methods
* Second-order Taylor expansion
* Solving for the critical point we obtain the Newton parameter update

**Advantages**
* Faster convergence
* Less hyperparameters

**Disadvantages**
* Computationally very costly. Inverse matrix calculation
* BGFS - Avoid Hessian O(n3)
* L-BFGS - works well for full batch, not for mini-batches. Avoid stochasticity.



