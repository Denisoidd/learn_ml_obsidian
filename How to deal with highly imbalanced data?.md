1. SMOTE (Synthetic Minority Over-sampling Technique)
	*  1. - A random neighbor is chosen from the K-nearest neighbors, and then a random value between 0 and 1 is generated.
	*  This random value is multiplied by the difference between the instance and its chosen neighbor, and the result is added to the instance. This creates a new, synthetic instance along the line segment between the instance and its neighbor.

2. One-Class SVM
	* One-Class SVM is similar, but instead of using a hyperplane to separate two classes of instances, it uses a hypersphere to encompass all of the instances. Now think of the "margin" as referring to the outside of the hypersphere -- so by "the largest possible margin", we mean "the smallest possible hypersphere"
	* https://en.wikipedia.org/wiki/One-class_classification#Introduction

3. Isolation Forest