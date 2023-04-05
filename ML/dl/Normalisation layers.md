#DL 
![[Pasted image 20230316095754.png]]
* [[Batch Normalisation]]
* [[Layer normalisation]] works well with fully connected layers, however, it shows bad results when applied to convolutions.
* [[Group normalisation]] could be applied to mitigate [[Layer normalisation]] problem. In this approach we split metrics collection (mean, std) into smaller groups of size *G* for every chanel. 