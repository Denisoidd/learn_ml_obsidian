#DL 
**[article](https://arxiv.org/pdf/1502.01852.pdf)**
```python
def random_weight(shape):
"""
Create random Tensors for weights; setting requires_grad=True means that we
want to compute gradients for these Tensors during the backward pass.
We use Kaiming normalization: sqrt(2 / fan_in)
"""
if len(shape) == 2: # FC weight
	fan_in = shape[0]
else:
	fan_in = np.prod(shape[1:]) # conv weight [out_channel, in_channel, kH, kW]

# randn is standard normal distribution generator.
w = torch.randn(shape, device=device, dtype=dtype) * np.sqrt(2. / fan_in)
w.requires_grad = True

return w
```
