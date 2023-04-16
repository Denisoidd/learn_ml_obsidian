#DL 

#### Idea
This trick consists of adding new channels into the input of the neural network. 
To do so we can use **nn.Embedding** layer.

#### Example
```python
class ClassConditionedUnet(nn.Module):
	def __init__(self, num_classes=10, class_emb_size=4):
		super().__init__()
		# The embedding layer will map the class label to a vector of size class_emb_size
		self.class_emb = nn.Embedding(num_classes, class_emb_size)		
		# Self.model is an unconditional UNet with extra input channels to accept the conditioning information (the class embedding)
		self.model = UNet2DModel(
			sample_size=28, # the target image resolution
			in_channels=1 + class_emb_size, # Additional input channels for class cond.
			out_channels=1, # the number of output channels
			layers_per_block=2, # how many ResNet layers to use per UNet block
			block_out_channels=(32, 64, 64),
			down_block_types=(),
			up_block_types=(),
		)
		# Our forward method now takes the class labels as an additional argument

def forward(self, x, t, class_labels):
	# Shape of x:
	bs, ch, w, h = x.shape
	# class conditioning in right shape to add as additional input channels
	class_cond = self.class_emb(class_labels) # Map to embedding dinemsion
	class_cond = class_cond.view(bs, class_cond.shape[1], 1, 1).expand(bs, class_cond.shape[1], w, h)
	# x is shape (bs, 1, 28, 28) and class_cond is now (bs, 4, 28, 28)
	# Net input is now x and class cond concatenated together along dimension 1
	net_input = torch.cat((x, class_cond), 1) # (bs, 5, 28, 28)
	# Feed this to the unet alongside the timestep and return the prediction
	return self.model(net_input, t).sample # (bs, 1, 28, 28)

```

