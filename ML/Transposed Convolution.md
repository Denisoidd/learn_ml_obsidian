#DL 

#### Introduction
Transposed convolution could be used in order to increase spatial dimensions of the input in tasks such as **Image superresolution**, **Image segmentation** etc.

Transposed convolution **is not inverse of convolution**! 

#### How it works
![[Pasted image 20230329123301.png]]
1. We need to calculate new parameters: $z, p', s'$:
$$
\begin{align*}
z = s-1, \\
p' = k-p-1, \\
s' = 1, \\
k - \text{kernel size, } p - \text{padding}
\end{align*}
$$
Parameter $z$ - is the number of zeros we need to insert between each input value ($x, y$ axes), $p$ - new padding of transformed input and $s'$ is a new stride which always equals to $1$.

2. We insert $z'$ zeros between rows and columns 
3. We apply padding of $p'$
4. We slide with kernel of size $k$ over the transformed image.

#### What about shapes?

With input size - $i$, stride - $s$, kernel size - $k$ and padding - $p$. Output of Transposed Convolution will be:
$$
o = (i-1)s + k - 2p
$$
Output of standard convolution is:
$$
o = \frac{i + 2p - k}{s} + 1
$$