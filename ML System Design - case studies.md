#system-design 

**[Case studies](https://huyenchip.com/machine-learning-systems-design/case-studies.html)**
**[Exercises](https://huyenchip.com/machine-learning-systems-design/exercises.html)**

#### Case
1. **Real-Time Anomaly Detection System Design:** Architect a system that employs computer vision and machine learning for real-time anomaly detection on the manufacturing floor, identifying deviations from the normal operation.
#### Solution
1. Project setup
2. Data pipeline
3. Modeling / Training
4. Serving 

1. Project setup
	1. Video stream / Sequence of images. Binary classification for each frame if anomaly or not (solve this)
	2. Real-time notification for the user if anomaly is detected
	3. Edge device, no cloud. FP are preffered. Higher recall than precision. 
	4. Use recall in train and test. 
	5. One model fits all. Different angles, light conditions, video quality and so on.
	6. 2 weeks to implement. 2 GPUs
2. Data pipeline
	1. We have 1000 videos of process with a timestamp of real anomaly detection. Data is highly imbalanced (solve this). 
	2. Annotate missed anomalies in the process with user feedback
	3. Storage (how to work with video streams)
	4. Class imbalance - annotation, data augmentations, losses for more concentration, repeat data. Focal loss
3. Modeling
	1. Classification for each frame. Binary.
	2. 50 / 50 anomaly. Heuristics threshold. CNNs + FC. MobilenetV3
	3. CNNs (several images) + LSTM --> sequence of 0 and 1
4. Training
	1. Overfit 1 batch. 
5. Serving
	1. Real-time inference (how many frames per second)
	2. Try to understand FP examples. Data augmentations to improve. Data input to test. 

#### Weak points
* How to work with video streams? How to process them in real-time?
* How to store video data?
* How to deal with outliers?
* TensorRT how multiplication is optimized?
* Gradient Scaling - how fp16 is trained?
* How ResNet works?
* Transformers - positional encoding. Why use sinus? Fourrier.
* Венгерский алгоритм.
* Learn about DYNOv2, Lora, ControlNet, StableDiffusion
* https://arxiv.org/abs/2302.09778
* https://arxiv.org/abs/2111.06377 
* What is [[Optical Flow]]
* Metrics optimization for training and test. Recall, Precision what else?
* [[How to deal with highly imbalanced data?]] Anomaly detection?