#DL 
**Links**
**[Transformer implementation](https://colab.research.google.com/drive/1a7uFSHgQWJZcdfrOsaij1K-uMhVuAP2K#scrollTo=fdfd8db3)**
[[Visual Transformer]]
**[Attention in SD](https://vaclavkosar.com/ml/cross-attention-in-transformer-architecture)**

### Introduction
[[RNN]] for sequence to sequence problem. 
![[Pasted image 20230318092028.png]]
1. First we use a **Encoder** network feeding all inputs to it
2. At the end separate **Initial decoder state** and **Context vector**.
3. Feed this information to **Decoder** with some *START* token
4. **Context vector** transfers all of the information
	* But what if we want to translate a big paragraph?

### Attention
![[Pasted image 20230318092636.png]]
Add an additional mechanism - **alignment function**. Which answers the question: *"How much should we attend at each encoder hidden score given final decoder hidden state?"*

$$
e_{t,i} = f_{att}(s_{t-1}, h_i)
$$

**Alignment function** is a simple MLP.

![[Pasted image 20230318093847.png]]
* Once, we've obtained all scores $e_{ti}$ we can use [[Softmax classification|softmax]] to get probabilities of which hidden states are more important in decoder hidden state $s_{t-1}$.  
* Then, we will multiply hidden scores by softmax values, sum them and compute **Context vector** 

### Image captioning with RNNs and Attention

![[Pasted image 20230318094756.png]]
* The same idea, just at first we've obtained feature vectors of image and then we feed it into **RNN** with **attention**

### Abstraction
#### Example
Suppose, we have a library. Each book is labeled with some tags: *kitchen, diy, literature, IT, etc*. We want to find a book with the following **query**: "vegetarian diet for sportsmen".

At first, we will multiply our **query** vector by **key** matrix which consists of tags assigned to each book. Once we've multiplied it and added *softmax* we can proceed to output generation.

To get final output, we will use **value** matrix which contain additional information about the book such as: title, author, publisher. With its help, by multiplication we can produce the most probable candidate for out **query**

**Inputs**
Query: $q$ of shape $D_Q$
Input: $X$ of shape $(N_X, D_Q)$
Similarity function: scaled dot product

**Computation**
Similarities scores: $e_i = q.X_i / sqrt(D_Q)$ of shape $N_X$
Attention weights: $a=softmax(e)$ of shape $N_X$
Output vector: $y = \sum_{i} a_iX_i$ of shape $D_X$

### Self-Attention Layer
![[Pasted image 20230323204458.png]]
* Permutation equivariant

### Masked Self-Attention Layer

![[Pasted image 20230323204907.png]]
### Multihead Self-Attention Layer

![[Pasted image 20230323205113.png]]
* Good for parallelisation
* Very memory intensive

### CNN with Self-Attention

![[Pasted image 20230323205432.png]]


### Transformer

![[Pasted image 20230323210126.png]]
* Self-attention is the only interaction between vectors
* Layer norm and MLP work independently per vector

### Positional Encoding
![[Pasted image 20230328203710.png]]
**Good video explanation:**
**[Link](https://www.youtube.com/watch?v=dichIcUZfOw)**

**Why other functions do not work?**
1. We need a function which assigns same values for the same position, **not depending on the sequence length**
2. Also we should be able to separate these positions in our periodic function. To do so, we add many frequences by varying **j** and **sin** and **cos** functions

**Another good picture**
![[Pasted image 20230328205458.png]]

