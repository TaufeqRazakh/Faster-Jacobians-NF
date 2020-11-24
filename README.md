# Fast training of Autoregressive flows when using Sum-of-Squares Polynomial Flow

[Normalising Flows](https://arxiv.org/abs/1505.05770) are a family of generative models. A  transformation  of  a  simple probability distribution (e.g., a standard normal) into a more complex distribution by a sequence of invertible and differentiable mappings.

You might be familiar with the generative neural approaches namely
+ [generative adversarial networks(GANs)](https://arxiv.org/abs/1406.2661)
+ [variational auto-encoders networks(VAEs)](https://arxiv.org/abs/1312.6114)

But they have their limitations making them not so usable for scientific computing, namely:
+ Cannot do an exact evaluation of probability density of new points
+ Training can be tricky due to mode collapse, posterior collapse

## Where are generative models used today ?

+ [Image generation](https://arxiv.org/abs/1807.03039)
+ [Reinforcement Learning](https://arxiv.org/abs/1905.06893)
+ [Physics](https://arxiv.org/abs/1812.01729), [more physics](https://arxiv.org/abs/2002.09491) etc.

> Cica 2019 - ...

## Basics

<img src=
"https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+%5Cbegin%7Balign%2A%7D%0AY+%3D+g%28Z%29%0A%5Cend%7Balign%2A%7D%0A"
alt="\begin{align*}
Y = g(Z)
\end{align*}
">

<img src=
"https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+%5Cbegin%7Balign%2A%7D%0Ap_Y%28Z%29+%3D+p_Z%28f%28y%29%29%7Cdet+Df%28y%29%7C%0A%5Cend%7Balign%2A%7D%0A"
alt="\begin{align*}
p_Y(Z) = p_Z(f(y))|det Df(y)|
\end{align*}
">

<img src=
"https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+p_Y%28Z%29+%3D+p_Z%28f%28y%29%29%7Cdet+Dg%28y%29%7C%5E%7B-1%7D%0A"
alt="p_Y(Z) = p_Z(f(y))|det Dg(y)|^{-1}
">

> Maintaing the Jacobian for higher order systems is hard

<img src=
"https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+O%28d%21%29%2C+O%28d%5E3%29%0A"
alt="O(d!), O(d^3)
">

> Chain some parameterized, invertible and differentiable transformations.

## Objective

Make the computation of determinant more tractable

+ Can use matrix triangular matrices

But we will use non-linear functions

+ Obtain feature and use a arbitrary NN
+ Can use convolution theorems in images to get a weight in fourier space which is block diagonal matrix so determinant is easy to compute.
+ [Another method very similar to residual NN which is designed to make Determinant computation more tractable](https://arxiv.org/abs/1803.05649)
+ Autoregressive Model to go from initial state to gaussian distribution - very non parallel

+ Auto regressive model in feed forward NN setting where each group of neurons is connected to preceeding timestep. This will guarantee us that the Jacobian will have triangular form

## Inverting a neural network
This can be considered as a second challenge of managing the bijectivity constraint

## What are we looking for

Is there an architecture that can be converted into a linkedlist representation that can be parallelised and also guarantee a triangular Gaussian or diagonal Gaussian for tractable calculation


## Inspiration

+ [Scalable Data-Privatization Threading for Hybrid MPI/OpenMP Parallelization of Molecular Dynamics, Kunaseth, et. al. (2011)](http://cacs.usc.edu/papers/kunaseth-ScalableHybridMD-PDPTA20110.pdf)
+ [Accurate, Large Minibatch SGD:Training ImageNet in 1 Hour](https://research.fb.com/wp-content/uploads/2017/06/imagenet1kin1h5.pdf)
