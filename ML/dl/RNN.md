#DL 
### Links
**[Image captioning with RNN notebook](https://colab.research.google.com/drive/1MPEW2m1Q4Oa8-HDsLOYJoUAF4sIM-ukd#scrollTo=d2f9cc2a)**

### Introduction
#### Sequential data
Problems with **one-to-many**, **one-to-one**, **many-to-one**, **many-to-many**.

**Examples:**
* Video sequences labeling
* Translation

*We do not know sequence length in advance*

#### Non-sequential data examples
* Classify images by taking a series of "glimpses"
* Generation of images 
* Oil painting
![[Pasted image 20230317162048.png]]


### How does it work

*RNNs have an "internal state" that is updated as a sequence is processed*

$$
h_t = f_W(h_{t-1}, x_t)
$$

New state $h_t$ is a combination of $h_{t-1}$ - previous state and $x_t$ - input vector. 

#### Vanilla RNN

$$
\begin{aligned}
h_t = tanh(W_{hh}h_{t-1} + W_{xh}x_t) \\
y_t = W_{hy}h_t
\end{aligned}
$$
![[Pasted image 20230317163053.png]]
* We use **the same** weight matrix at each step 

#### Different cases
* Many-to-many
	* Use another matrix $W_{hy}$ for output
	* Calculate loss for each output
	* Sum losses
* Many-to-one
	* Video classification for example
* One-to-many
	* Image captioning --> output sequence of words that describe input image
* Sequence to sequence
	* Many to one --> One to many
	* Hidden vector at the end feed to the second network
	![[Pasted image 20230317163805.png]]
	* We have different weight matrices for **encoder** and **decoder** networks

### Language Modeling
![[Pasted image 20230317164159.png]]
* Convert each letter to a **one-hot vector**
* Given a symbol "h" network predicts which symbol is the next 
* After we've got two symbols "he" and the model predicts "l"
* And so on. So as a target we have a **moved** string by 1 character

#### One-hot vector problem

Insert an **embedding layer**. Solve the problem with raw zero one inputs. 

#### Backpropagation

During backpropagation we need to take into account **two** input gradients:
1. Gradient produces by loss function for a given sequence element
2. Gradient from the upper hidden layer (for the last hidden layer it's **zero**)

#### Backpropagation through time
![[Pasted image 20230317165052.png]]
* Truncated backprop through time, because there is not enough memory for a long sequence of symbols. We record hidden weights after each chunk of sequence.

### Image captioning

![[Pasted image 20230317171546.png]]
* Delete last layers from pretrained CNN model
* Change hidden state calculation to include image information
* Start caption generation with **START** token
* Run RNN
* Generation will end when **END** token is shown 




### Vanilla RNN Gradient Flow

![[Pasted image 20230317172202.png]]
Problems:
* Backpropagation from $h_t$ to $h_{t-1}$ multiplies by $W_{hh}$ 
* For many steps we will multiply many times by the same matrix $W_{hh}$ and also $tanh$ 
* Gradients will explose or dissappear  

### LSTM

![[Pasted image 20230317173314.png]]

* We will keep **two** hidden vectors
	* $c_t, h_t$ - cell state and hidden state
* Compute **four** gate values
![[Pasted image 20230317173601.png]]

![[Pasted image 20230317174015.png]]

* Better gradient propagation for $c_t, c_{t-1}$
* Uninterrupted gradient flow
* Residual connections like in [[ResNet]]

### Multi-Layer RNNs
![[Pasted image 20230317174849.png]]

* We have 2 axes - time (**x**) and depth (**y**)

### GRU

* Gated Recurrent Unit
* Kind of simplified **LSTM**



