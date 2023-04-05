#classic #classification

### Links
Lecture: **[Lecture 2](https://www.youtube.com/watch?v=8inugqHkfvE)**  
Lecture notes: **[kNN notes](https://cs231n.github.io/classification/)**
Assignment: **[kNN assignment](https://colab.research.google.com/drive/1tB529IoxHzA45fCJlVesaBtrDxhZdMZ7#scrollTo=65cef347)** 


### Main idea of work
1. kNN remembers all the data. So there is no training stage
2. To predict to which class test input belongs:
	1. We need to calculate all distances between test example and train examples
	2. Once calculated, we should find k closest neighbours
	3. Pick the most common label as prediction

### Notes
* **Good** points:
	* No training required
	* Easy to implement
* **Bad** points:
	* $O(n)$ speed of inference, where $n$ is number of training examples