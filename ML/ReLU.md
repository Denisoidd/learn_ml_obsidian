#DL 
### Advantages
1. No vanishing gradients for x > 0
2. Fast to compute

### Disadvantages
1. Not zero centered
2. Dead ReLU. When x < 0, gradient will be 0 and neuron will die

### Alternatives
1. LeakyReLU: $f(x) = max(0.01x, x)$ 
2. Parametric Rectifier (PReLU):  $f(x) = max(\alpha x, x)$ 