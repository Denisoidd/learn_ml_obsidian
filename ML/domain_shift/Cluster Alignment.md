#domain_shift 

**Idea**
We have feature vectors from <u>target</u> and <u>source</u> data. Then these data is clustered using [[k-means]] or [[spectral clustering]] methods. After that target and source clusters are matched based on their similarity and **transfer** function is learned to aligned them.

**Cluster alignement**
There are many different ways of cluster alignment:
1. [[Maximum Mean Discrepancy]]
2. [[Joint Cluster Alignment]]
3. [[Joint Distillation]]