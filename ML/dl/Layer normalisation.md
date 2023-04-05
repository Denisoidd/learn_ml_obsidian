#DL 

### Idea
Instead of normalisation over the **batch** - [[Batch Normalisation]] we normalize over the **features**
**[link](https://arxiv.org/pdf/1607.06450.pdf)**

### Implementation
We can see it as a [[Batch Normalisation]] layer whose input was **transposed** and also there are no differences in train / test time.
**[Batch norm implem / Layer norm implem](https://colab.research.google.com/drive/1aUwDF7OiWeX5iC1-yJlJLWw6f7lwGtA8#scrollTo=iSYrk1vK7rul)**

### Use cases
* It's a good idea to use **layer normalisation** when the batch size could not be big enough. With small batches [[Batch Normalisation]] converges slowly than 