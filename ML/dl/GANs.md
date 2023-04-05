#DL 
**[Notebook GAN implementation](https://colab.research.google.com/drive/1gmD2wGoWVBDkuV79zzp7Ct-fzh1g4BNI#scrollTo=d768923a)**
#### Main idea in simple words
We want to generate realistic images. Create **Generator (G)** and **Discriminator (D)** and let them both compete with each other. 

**G**'s goal is to create images as realistic as possible to trick **D** into believing that this image is a real one. On the other side, **D** wants to classify which image is real and which one is not.

This problem create a **minmax** optimization problem. Where **G** optimization goal is to **lower** **D**'s probability of making the **right** choice and, contrarely, and **D** is to make it **higher**

#### Mathematics behind it
These ideas could be written mathematically in the following way:
$$
\underset{G}{\text{minimize}}\; 
\underset{D}{\text{maximize}}\;
\mathbb{E}_{x \sim p_\text{data}}\left[\log D(x)\right] + \mathbb{E}_{z \sim p(z)}\left[\log \left(1-D(G(z))\right)\right]
$$
For better implementation, we will change **G** goal to **maximize** **D** making the **incorrect** choice on generated data:
$$\underset{G}{\text{maximize}}\; \mathbb{E}_{z \sim p(z)}\left[\log D(G(z))\right]$$
$$\underset{D}{\text{maximize}}\; \mathbb{E}_{x \sim p_\text{data}}\left[\log D(x)\right] + \mathbb{E}_{z \sim p(z)}\left[\log \left(1-D(G(z))\right)\right]$$

#### Other GANs implementations
**[Least Squares GANs](https://arxiv.org/pdf/1611.04076.pdf)**
$$\ell_G = \frac{1}{2}\mathbb{E}_{z \sim p(z)}\left[\left(D(G(z))-1\right)^2\right]$$
$$ \ell_D = \frac{1}{2}\mathbb{E}_{x \sim p_\text{data}}\left[\left(D(x)-1\right)^2\right] + \frac{1}{2}\mathbb{E}_{z \sim p(z)}\left[ \left(D(G(z))\right)^2\right]$$
**[DCGAN](https://arxiv.org/pdf/1511.06434.pdf)**
In this architecture we use **D** and **G** consisting of [[Conv Networks]], [[Transposed Convolution]], [[Batch Normalisation]]. These networks are deeper than in previous architecture.