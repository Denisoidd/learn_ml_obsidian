#self-supervised 

Based on: *A Cookbook of Self-Supervised Learning*

### Great examples to learn
* SEER
* MAE or BYOL - predict masked patches of an image
* DINOv2

### Origins
1. Information restoration
2. Using temporal relationships in video
3. Learning spatial context ([[Self-Supervised Learning#^576b3f|rotation, jigsaw]])
4. Group similar images together
5. Generative models
6. Multi-view invariance

### Current categories
1. Deep Metric Learning Family
2. Self-distillation Family
3. Canonical Correlation Analysis Family
4. Masked Image Modelling Family

#### Deep Metric Learning Family
**Idea**
* Encourage similarity between semantically transformed versions of an input
**Loss**
* [[Contrastive loss]] *at the beginning*
* the use of other samples *positive* views as *negative* view of other pairs
* [[SimCLR#^d02bbb|InfoNCE]] loss which is central in SSL
**Important points**
* we use **semantic preserving** transformations

#### Self-Distillation Family
**Examples**
* BYOL, SimSIAM, DINO

**Idea**
* Feed 2 different views to 2 encoders and map one to the other by means of predictor

**BYOL**
* Bootstrap Your Own Latent 
* consists of 3 networks: **student**, **teacher**, **predictor**
* **teacher** predicts the target, **student** predicts the output
* each network receives a view of the same image with applied image augmentations
* **student** network is updated via gradient descent
* **teacher** network has the same architecture as **student** and updated via [[Exp Moving Average]] of the weights of **student** in the following way:
	* $\theta_t \leftarrow \epsilon\theta_t + (1-\epsilon)\theta_s$  

**SiamSiam**
* Update of a BYOL, where we use only **student** and **predictor** networks

**DINO**
* *Actually didn't understand it from article yet*

**DINOv2**
* its predecessor **iBOT**

**MoCo**

#### Canonical Correlation Analysis Family
**Idea**
* Infer the relationship between two variables by analyzing cross-covariance matrices
* We look for transformations which map $X, Y$ to $U,V$ that have **zero-mean** and **identity cov** representations

**Examples**
* Alternating Conditional Expectation method **ACE**
* Deep Canonically Correlated Autoencoders **DCCAE**

**DCCAE**
* Find parameters for 2 networks such that: $(\theta_1^*, \theta_2^*) = argmax_{\theta_1, \theta_2}(corr(f_1(X_1, \theta_1), f_2(X_2, \theta_2)))$

**VICReg**

#### Masked Image Modeling
**Idea**
* degrade model input via masking and teach a model to undo the masking degradation

**Examples**
* BERT
* MAE - Masked AutoEncoders
* SimMIM


### Theoretical explanation
**Interesting points**
* contrastive SSL losses already have such mechanisms at **batch level**, focusing on *hard-negative pairs*, which means contrastive losses need **large batch sizes**

**Dimensional collapse**
* feature representation are not expressive enough, the data has more variety and complexity than its representing feature vector

**Weakly-curated training data**
* curate big dataset for the type of images you want your network to perform well on

### Train and Deploy
* SSL performs poorly on unbalanced datasets, to alleviate this issue MSN method was proposed. This method changes distribution of SLL clustering

**Teacher-Student**
* Teacher and student networks could be **identical** as long as predictor is **updated more often** or has **larger learning rate**
* **[Understanding BYOL / SimCLR](https://github.com/facebookresearch/luckmatters/tree/main/ssl)** 

**Mini-Batch Size**
* square root scaling of the learning rate give significant increase in performance: *A simple framework for contrastive  
learning of visual representations*
* remove positive pair from the denominator of the softmax: *Decoupled contrastive  
learning*
