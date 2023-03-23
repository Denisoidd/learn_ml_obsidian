#classic 
1. **[Gateaux derivative](https://en.wikipedia.org/wiki/Gateaux_derivative)**  - for matrix differentiation
2. Bias tric:
	 Add one more dimension to weights with ones to include bias:
		$$
	W = 
	\begin{bmatrix} 
	w_{00}, w_{01}, \dots, w_{0N}, b_0 \\
	w_{10}, w_{11}, \dots, w_{1N}, b_1 \\
	\dots \\
	w_{M0}, w_{M1}, \dots, w_{MN}, b_M
	
	\end{bmatrix}
	*
	\begin{bmatrix}
	x_1 \\
	x_2 \\
	\dots \\
	x_N \\
	1
	\end{bmatrix}
	$$
	