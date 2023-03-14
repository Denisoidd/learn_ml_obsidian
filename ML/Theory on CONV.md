#DL 
### Interesting points
* Convolutions can consume a lot of memory but often do not take a lot of parameters
* Fully connected layers are reverse of it

### Implementation
$$
\begin{align*}
&\text{Let's setup some variables: }\\
&\text{s - stride, p - padding}\\
&I - \text{input image with shape: }(H, W, C)\\
&W - \text{convoluiton weights with shape: }(HH, WW, F)\\
&b - \text{bias vector with shape: }(F) \\
&O - \text{output tensor with shape: }(H', W', F)\\
\\
&\text{The output results will have the following shape:} \\
&\text{where } H' = \frac{H + 2p - HH}{s} + 1&\\
&\text{where } W' = \frac{W + 2p - WW}{s} + 1&\\
\\
&\text{Final tensor could be obtained by the following multiplication:}\\
&O_{i,j,f} = \sum_{c=0}^{C}\sum_{\hat{j}=0}^{WW}\sum_{\hat{i} = 0}^{HH}\hat{I}_{is + \hat{i}, js + \hat{j}, c} \odot W_{\hat{i}, \hat{j}, f} + b_{f},\\
&\text{where } \hat{I} \text{ is a padded image}
\end{align*}
$$

### Backpropagation
$$
\begin{align*}
&\text{With the use of above notation:} \\
&\dfrac{\partial L}{\partial W_{k,l,f}} = \dfrac{\partial L}{\partial O_{i, j, f}}\dfrac{\partial O_{i, j, f}}{\partial W_{k,l,f}} \\
\\
& \text{First derivative } -  \dfrac{\partial L}{\partial O_{i, j, f}}\text{ depends only on further loss function.} \\
&\text{Let's concentrate on the second: } \\
& \dfrac{\partial O_{i, j, f}}{\partial W_{k,l,f}}  = \dfrac{\partial}{\partial W_{k,l,f}}\sum_{c=0}^{C}\sum_{\hat{j}=0}^{WW}\sum_{\hat{i} = 0}^{HH}\hat{I}_{is + \hat{i}, js + \hat{j}, c}\odot W_{\hat{i}, \hat{j}, f}\\


\end{align*}
$$