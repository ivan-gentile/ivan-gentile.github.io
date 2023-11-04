---
title:  "How do Neural Networks learn? Understanding Backpropagation with Kaparthy's micrograd"
image : "/assets/images/post/post-1.gif"
author: "Ivan Gentile"
date: 2023-08-24 11:12:58 +0600
description: "Explore the fundamental mechanics of neural networks and the essential process of backpropagation. Leveraging insights from Karpathy's micrograd lesson, this article elucidates how neural network algorithms adapt and learn, making complex AI models efficient."
tags: [AI, Neural Networks, Backpropagation, Machine Learning, Algorithms, Karpathy, Deep Learning]
---
[Yes, you should understand backprop!][yes-backpropagation]

The best way I found so far to really get the feeling of knowing the ins and outs of it is to follow AI guru master [Andrej Karpathy][karpathy-website] explanations, and in particular follow his [youtube lecture][youtube-lecture] on building `micrograd` ([find it on github][micrograd-github]). 
<div style="text-align:center;">
  <img src="/assets/images/post/smallkarphatyMonk.png" alt="Description of image" width="250" />
</div>

This post is a trap. My goal is to distill Karpathy's 2.5-hour lecture into a quicker read, but i will also attach additional resources that complement the lecture. So, fair warning: [the rabbit hole of mathematical wonder][animation-math] could be quite consuming.

If you successfully manage to go through it, or if you already watched the lecture and are looking for a review and extra material, I published a simple `github repo or google colab` for you to practice your understanding of micrograd. Let's dive into the material.

### How to get the feeling to truly knowing backpropagation?
Unfortunately the [original paper](https://www.nature.com/articles/323533a0) is behind  a paywall and, unless you are in uni, there is no way to get it for free <span style="opacity: 0.2;">*cough cough sci-hub *</span>
What about then jump straight to see how it is implemented in libraries such as Pytorch and TensorFlow? 
Well, attacking their respective github repo might be a hard task.. we could indeed check out [TensorFlow introduction to gradients documentation](Introduction to gradients and automatic differentiation) or Pytorch [gentle introduction to torch.autograd](https://pytorch.org/tutorials/beginner/blitz/autograd_tutorial.html), but the first snippet of code in this last one: 

```
import torch
from torchvision.models import resnet18, ResNet18_Weights
model = resnet18(weights=ResNet18_Weights.DEFAULT)
data = torch.rand(1, 3, 64, 64)
labels = torch.rand(1, 1000)
```
is enough to scare our mind away to truly wrap our mind around the model. 

Luckily, micrograd is a perfect tool in order to make us understand the topic...
So whe

[karpathy-website]: https://karpathy.ai/
[yes-backpropagation]: https://karpathy.medium.com/yes-you-should-understand-backprop-e2f06eab496b
[youtube-lecture]: https://www.youtube.com/watch?v=VMj-3S1tku0&list=PLAqhIrjkxbuWI23v9cThsA9GvCAUhRvKZ&index=2&ab_channel=AndrejKarpathy
[micrograd-github]: https://github.com/karpathy/micrograd
[animation-math]: https://www.youtube.com/watch?v=B1J6Ou4q8vE&ab_channel=AlanBecker

Here is some text and <span style="color:blue">this is blue</span>.

Useful material: 
<span style="color:blue">The aim is to find a powerful synaptic
modification rule that will allow an arbitrarily connected neural
network to develop an internal structure that is appropriate for
a particular task domain (from backprop paper)</span>.