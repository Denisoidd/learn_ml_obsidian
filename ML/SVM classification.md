#classic #classification 

### Links
**[Notebook](https://colab.research.google.com/drive/1FcsSPXhuINHh_QHdXWHdK29lpvB3XorR#scrollTo=72ac2e11)**
**[Notes](https://cs231n.github.io/linear-classify/)**
**[Lecture](https://www.youtube.com/watch?v=qlLChbHhbg4)**

### SVM Loss:
$$
L_{SVM} = \sum_{j \neq y_{i}} \max(0, s_j - s_i + 1)
$$
where $s_j = f(x_i, W)$ in linear case $s_j = Wx_j + b$ [[Matrix trics|include bias]]

