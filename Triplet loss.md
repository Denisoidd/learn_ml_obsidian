#DL 

#### Idea
Triplet loss based on the idea of similarity. We want examples from **positive class to be close** to the anchor point and **negative class to be far** from anchor point.

#### Examples
* Face recognition - in the database we have all allowed images and we check if input image is close enough to one of database images
* BERT
* Signature verification
* [[Siamese Network]]

#### Formulation
$L(A,P,N)=max(||f(A)-f(P)||^2 - ||f(A)-f(N)||^2 + \alpha,0)$

#### Hard and Easy triplets
* **Hard** triplets are those negative examples with which anchor has a **very small distance**, contrary **easy** triplets are those negative examples which has a **huge distance** with anchor.

#### Margin constraint violation
$||f(A)-f(P)||^2 - ||f(A)-f(N)||^2 < \alpha$ 

* When embedding of positive example lies further away by more than a margin from anchor point than negative one, example becomes not informative

