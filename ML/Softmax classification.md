#classic #classification 
### Links
Lecture: **[Lecture 3](https://www.youtube.com/watch?v=qlLChbHhbg4)**  
Lecture notes: **[softmax notes](https://cs231n.github.io/linear-classify/#softmax-classifier)**
Assignment: **[softmax assignment](https://colab.research.google.com/drive/1p-mysZr56KNR1NpRrUIT4wqjnSmFHw1g#scrollTo=ade33adc)** 

### Main idea
* Softmax classification layer outputs a **normalized** vector of scores which can be interpreted as "probabilities". [[SVM classification|SVM]] doesn't have this option.
* Softmax loss for an input vector $\vec{x} = (x_0, x_1, \dots, x_p)$ can be written as:
$$
\begin{aligned}
L_i = -\log(\dfrac{e^{x_i}}{\sum_{j = 0}^{p}e^{x_j}})
\end{aligned}
$$
* So for each component of input vector $\vec{x}$ we normalise it by $\sum_{j=0}^{p}e^{x_j}$ 
* Gradient with respect to $\vec{x_j}$:
$$
\begin{aligned}
\frac{\mathrm{d}L_i}{\mathrm{d}x_j} = -\dfrac{1}{\sigma(x_i)}(-\sigma(x_i)\sigma(x_j)) = \sigma(x_j), 
\text{ if i} \neq \text{j} \\
\frac{\mathrm{d}L_i}{\mathrm{d}x_i} = -\dfrac{1}{\sigma(x_i)}(\sigma(x_i)-\sigma(x_i)^2) = \sigma(x_j) - 1, 
\text{ if i} = \text{j}
\end{aligned}
$$

