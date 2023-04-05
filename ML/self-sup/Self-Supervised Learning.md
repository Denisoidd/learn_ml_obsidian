#self-supervised 
#### Links
[[Contrastive Learning]]
**[Stanford lecture](http://cs231n.stanford.edu/slides/2022/lecture_14_jiajun.pdf)**
**[SSL Notebook](https://colab.research.google.com/drive/1xJd_B_HpZvCJtSwRGc-iD4bGhu26BItR#scrollTo=61db5e66)**
#### Future read
* **[Emerging Properties in Self-Supervised Vision Transformers](https://arxiv.org/pdf/2104.14294.pdf)**
#### What is it
SSL allows models to automatically learn "good" representation space using the data in a given dataset **without** the need for the labels.

"Good" we can describe as feature vectors of semantically similar inputs are **close** and **far** for different one. 

#### Types of SSL
##### Image rotation
**Assumption**: model could correctly predict rotation angle of the image if only it has good understanding of what image should like in normal position
![[Pasted image 20230330092248.png]]
##### Jigsaw Puzzles
**Assumption**: We split image into patches and then network needs to predict where each patch should be placed. By doing so, it will learn good image representations.
![[Pasted image 20230330092624.png]]
##### Inpainting
**Assumption**: If neural network will inpaint images correctly it will understand the structure of the image very well.
![[Pasted image 20230330093043.png]]
###### Image coloring
**Assumption**: Neural network will color images if only it understands them correctly
![[Pasted image 20230330093537.png]]
