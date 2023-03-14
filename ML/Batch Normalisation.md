#DL 
### Idea
To solve problems with weights initialisation we can let the network to normalise data itself
![[Pasted image 20230314092137.png]]
As we can see in the image above due to the use of batchnorm we're not so susceptible to weight initialisation anymore

### How it works
$$
\hat{x}_{(k)} = \frac{x_{(k)} - E_{(k)}[x]}{\sqrt{Var_{(k)}[x]}}, (1)
$$
$$
\hat{y}_{(k)} = \gamma  \hat{x}_{(k)} + \beta
$$
1. Normalise the input batch
2. Let the network learn parameters $\gamma$ and $\beta$ to scale and shift normalised data

### Implementation
**[Batch norm implem](https://colab.research.google.com/drive/1aUwDF7OiWeX5iC1-yJlJLWw6f7lwGtA8#scrollTo=iSYrk1vK7rul)**
