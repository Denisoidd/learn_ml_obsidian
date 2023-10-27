#system-design 

https://huyenchip.com/machine-learning-systems-design/design-a-machine-learning-system.html

#### Short list of questions
- How did you collect the data? How did you process your data?
- How did you decide what models to use? What models did eventually try? What models did better? Why? Any surprise?
- How did you evaluate your models?
- If you did the project again, what would you do differently?

#### Main pipeline
1. Project setup
2. Data pipeline
3. Modeling / Training
4. Serving

##### Project setup
1. Goals
2. User experience: how end user supposed to use the system
3. Performance constraints: how fast, how good predictions should be
4. Evaluation during inference / train
5. Personalization: model for each user or the same for all
6. Project constraints: compute, time to develop

##### Data pipeline
1. Data availability and collection: data that you have, how much annotation costs, how to annotate correctly, weakly / self-supervised approaches
2. User data: how to collect, get feedback, how to improve with feedback
3. Storage: where it's stored, does it fit into the memory, data structures to use, how often is updated
4. Preprocessing / representation: process raw data, missing data, class imbalance, train / test from same distribution, different types of data how to combine them
5. Challenges: how careful to use user data
6. Privacy: anonimization
7. Biases: data and annotation inclusive

##### Modeling
1. Figure out the category of the problem: classification, regression, generation ...
2. Start with random / basic baseline so it will be easy to measure progress from it
3. Try simple heuristics to solve the problem

##### Training
1. Loss not decreasing, overfit, underfit, dead neurons

##### Debugging
1. Wrong assumptions: data / model
2. Bad hyperparameters: bayesian optimization
3. Bad implementation

##### Scaling
1. Gradient-Checkpointing, gradient accumulation for big input
2. FP16, FP32

##### Serving
1. How to incorporate user feedback into retrain process
2. Performance / Interpretability
3. Ablation studies for multi-component networks
4. Inference device



