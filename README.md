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

## What is the training essense ?

+ Choose an initial density
+ Chain some parameterized, invertible and differentiable transformations.

 
