#nlp
#### Main idea
1. Use the **MASK** token to predict missing words in the context
2. Can be use in big variety of tasks, such as: Sentiment Analysis, Q&A
3. **NER** Named Entity Recognition

#### Train ideas
1. Use the **MASK** token to randomly hide 15% of words and try to predict them
2. Try to predict if two sentences are consequent. Use **CLS** and **SEP** tokens.