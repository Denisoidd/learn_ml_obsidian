#DL 

#### Main Conv Nets
**[Competition of ImageNet](https://www.kaggle.com/getting-started/149448)**

[[AlexNet]]
*  60 mil params
* First use of ReLU
* CONV + ReLU + MaxPool
* FC in the end
[[VGG]]
* 140 mil params
* Simple combination of 3x3 CONV and MaxPool
* FC in the end
[[GoogLeNet - Inception]]
* 6 mil params
* Average Pooling in the end
[[ResNet]]
* Very rapid spatial reduction
* Residual connections 
	* Gradient flow much better 
	* One branch is identity, the second is delta 
* Batch Normalisation after every CONV
[[SENet]]
* Squeeze features into a 1 x 1 x C tensor --> softmax --> multiply original one
[[ResNeXt]]
[[DenseNet]]
* Concatenate features from begining to the end
[[EfficientNet]]
[[MobileNet]]
[[Wide ResNet]]