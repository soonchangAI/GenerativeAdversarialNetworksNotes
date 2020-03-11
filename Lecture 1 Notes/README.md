# Introduction to GAN
This is the notes for first lecture of a series of GAN lectures by Prof. Lee. It is heavily based on Prof. Lee's [video lecture](https://www.youtube.com/watch?v=DQNNMiAP5lw) and his [presentation slide](http://speech.ee.ntu.edu.tw/~tlkagk/courses/MLDS_2018/Lecture/GAN%20(v2).pdf).


## Table of Contents 

* [Importance of Generative Adversarial Networks](###importance-of-Generative-Adversarial-Networks)

* [Basic Idea of GAN](###basic-Idea-of-GAN)

* [GAN as Structured Learning](###basic-Idea-of-GAN)
* [Can Generator Learn by Itself ?](###Can-Generator-Learn-by-Itself-?)
* [Can Discriminator Generate ?](###Can-Discriminator-Generate-?)
* [A Little Bit Theory](###A-Little-Bit-Theory)
## Importance of Generative Adversarial Networks

Generative Adversarial Network (GAN) is one of the most rapidly growing research field in AI. In fact, Yann LeCun, the director of Facebook AI Research stated on Quora twice, he thinks that **Adversarial Training** / **GAN** is the most interesting idea in ML in recent years. Yann LeCun is a legend in the field of ML, and his opinion is the testament to GAN's awesomeness 👍 

>[Adversarial training is the coolest thing since sliced bread.](https://www.quora.com/What-are-some-recent-and-potentially-upcoming-breakthroughs-in-unsupervised-learning)

>[The most important one, in my opinion, is adversarial training (also called GAN for Generative Adversarial Networks). This is an idea that was originally proposed by Ian Goodfellow when he was a student with Yoshua Bengio at the University of Montreal](https://www.quora.com/What-are-some-recent-and-potentially-upcoming-breakthroughs-in-deep-learning)


GAN was invented by Ian Goodfellow in 2014. Since then many variations of GAN were invented.There is a Github's page dedicated to listing variations of GAN, called the [GAN Zoo](https://github.com/hindupuravinash/the-gan-zoo). 

The naming convention of GAN is adding a alphabet before GAN. For example, **SGAN**. At the time of writing this note, there are **six** different GANs called SGAN as shown in following figure 👇 

<img src="images/gan_names_sgan.PNG" width="600">

* The following graph shows growth in number of GAN 

<img src="images/cumulative_gans.jpg" width = "600" >

## Basic Idea of GAN

* GAN is a model which can generate things sucha as images and sentences. It is made up of two parts: **Generator** and **Discriminator**.
* Image Generation :
> [ 0.8, 0.4, ... , 0.2 ]  ⟶ Generator ⟶ 🤦‍

> [ 0.2, 0.1, ... , 0.7 ]  ⟶ Generator ⟶ 🤦
* Sentence Generation :
> [ 0.8, 0.4, ... , 0.2 ]  ⟶ Generator ⟶ "How are you ?"

> [ 0.2, 0.1, ... , 0.7 ]  ⟶ Generator ⟶ "Good evening "
* The generator is a neural network or a function.
* The generated image can be thought of as a high dimensional vector.
* Basic GAN basically has no practical usage because we have no control over the generations.
* Want each dimension of the input vector represents some attributes.
* For example, the last dimension corresponds to *emotion* 
* By changing the value of last dimension, can change the emotion.
> [ 0.8, 0.4, ... , **0.1** ]  ⟶ Generator ⟶ 😊

> [ 0.2, 0.1, ... , **0.9** ]  ⟶ Generator ⟶ 😂
* `Conditional Generation` will be discussed in Chapter 2.




