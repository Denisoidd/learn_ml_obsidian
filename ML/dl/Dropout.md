#DL 
### Model ensembles
* Average several checkpoints of the model
* Keep a track of a running average parameter vector
### Dropout
* Drop neurons with some probability
* Every single iteration we randomly choose neurons to drop
* *Dropconnect*
* During inference time we need to compensate the fact that we've dropped neurons with probability **p**. Expectation of output **is different** than output during inference with all neurons turned on.
* So at test time we need to multiply by **p** all the activations. 
* **Inverted dropout** - divide activations by **p** during train process, so the test script remains **unchanged**.
### Implementation
**[Notebook dropout](https://colab.research.google.com/drive/1i0ddSanoiZRvyxsccMNy5OOLvt0DyvSY#scrollTo=UhECEM-v2kXQ)**
