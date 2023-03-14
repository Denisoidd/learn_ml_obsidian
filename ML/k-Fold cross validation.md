#classic 

### How to
The idea behind this method is the following:
1. Set aside a **test dataset**
2. Split the rest of dataset in $k$ folds
3. Set aside $1$ fold as a **validation dataset** and $k-1$ folds as **training dataset** 
4. Train your algorithm with a set of hyperparameters and then evaluate on **validation dataset**
5. Repeat step 2-3 with another set of hyperparameters
6. Choose the **best performing parameters** and train the model on **whole** dataset