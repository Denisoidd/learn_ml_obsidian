#diffusion

**Links**
**[Lil Vlog](https://lilianweng.github.io/posts/2021-07-11-diffusion-models/)**
**[Hugging Face Diffusion Course](https://drive.google.com/drive/u/0/folders/1nzUTjBL_QJx0887wdRmJ643C63oQ5sfW)**
**[1. Introduction notebook](https://colab.research.google.com/drive/1eK1E8Ua9sCn79AwHqKDFJyveI01I9yDj#scrollTo=pEa6TgCFtQwv)**


#### Ideas
##### Interior design
* Add baseline countours of surroundings for good composition generation as a control net
* Can we pass already generated image as a context for the next image generation but with a different angle

#### General overview
##### Basic idea behind
* Have a neural network [[Unet]] which has the same shape as input and output. 
* Train this model to predict the noise which should be substracted from the image in order to obtain original image. Loss function - [[MSE]] between predicted and original noise.
* Generate noise with some scheduler -- [[DDIM]], [[DDPM]]
* During the inference we divide the process of noise removal by a number of steps could be 1000 for example. 


#### How to finetune Stable Diffusion
**[Pokemon Generator](https://lambdalabs.com/blog/how-to-fine-tune-stable-diffusion-how-we-made-the-text-to-pokemon-model-at-lambda)**



#### Control Nets
[[Control Nets]]