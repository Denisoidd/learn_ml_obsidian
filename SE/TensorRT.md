#se 
[[TRT Builder]]
[[TRT Inference]]

#### Questions about TensorRT
##### How does it work in general?
###### 0. What is throughput and latency
Latency - time from start to finish for a given task
Throughput - number of tasks completed in a given period of time
###### 1. Which operations are applied to optimize inference of the network?
* Tensor fusion (combine different operations on tensor into one operation)
* Layer fusion (combine combination of the layers into one for example CBR *convolution + batch + relu*)
* Kernel auto-tuning (select best algorithm for a kernel to use, optimizes: memory layout, threads, algo, gpu settings)
	* Examples of algorithms: **Matrix multiplication algo** (transform to column and multiply as matrix, faster than direct conv), **Winograd convolution** (do more addition which is faster than multiplication), **FFT**
* [[Precision]]
###### 2. Which networks can be better optimized? Which worse?
###### 3. On which GPUs can we achieve the biggest gain?
[[GPU architectures]]
1. What are the differences between these GPUs?
2. What is compute capability of GPU?
3. What are different GPU architectures you know?
###### 4. What are the main components of TensorRT framework?
* Builder
* Runtime
* Library
* Plugins
* Parser
##### Network optimization
1. What is fp32, fp16, int8, int4, int2, tp16?
2. How network quantization works?
3. How to preserve quality of neural network while reducing its latency?
4. Which networks are better to quantize? Which worse?
##### Experience
1. Describe which networks have you optimized? What were the gains? Why do you think you were able to attain them?
2. How to optimize neural network with TensorRT (which tools to use)?
3. How to deploy TRT model?