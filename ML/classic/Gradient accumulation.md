#classic 
**Links**
**[Article](https://kozodoi.me/python/deep%20learning/pytorch/tutorial/2021/02/19/gradient-accumulation.html#:~:text=Simply%20speaking%2C%20gradient%20accumulation%20means,might%20find%20this%20tutorial%20useful.)**

**Idea**
If we have a large model, with large images so we can easily run out of GPU / RAM memory. We can try to use **gradient accumulation method**.

This method consists of taking a **smaller** batch size and updating gradients every **k** steps. 

*For example we reduce the batch size 2 times and update gradients every 2 steps*