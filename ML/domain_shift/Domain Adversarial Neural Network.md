#domain_shift 

Unsupervised (we don't have labeled target data)
![[Pasted image 20230405124020.png]]
* Create a feature extractor - *features f*
* Create a label classifier - *class label y*
* Create a classifier which predicts if a given feature vector is from **source** or **target** distributions - *domain label d*
*  Train the objective which **minimize** $L_y$ and **maximize** $L_d$. In other words <u>network should be able to discriminate between different classes within a particular domain</u> and <u>be invariant to different domains</u>. 