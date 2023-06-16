#DL 

#### Idea
Embeddings of 2 similar inputs should be very close, but embedding of different inputs should be far from each other

#### Formulation
As input we have: $X_1, X_2$ and as a label $Y$ which equals $0$ if points are **similar** and $1$ if **different** 
Let $d = \sqrt{||f(X_1)-f(X_2)||^2}$ be a euclidian distance,

So loss function will be:
$L(X_1, X_2) = \frac{1}{2}((1-Y)d^2 + Ymax(0, m - d)^2)$
