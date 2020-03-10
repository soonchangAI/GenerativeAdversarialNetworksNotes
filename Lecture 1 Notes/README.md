# Introduction to GAN
This is the notes for first lecture of a series of GAN lectures by Prof. Lee. It is heavily based on Prof. Lee's [video lecture](https://www.youtube.com/watch?v=DQNNMiAP5lw) and his [presentation slide](http://speech.ee.ntu.edu.tw/~tlkagk/courses/MLDS_2018/Lecture/GAN%20(v2).pdf).


## Table of Contents

* [Importance of Generative Adversarial Networks](###importance-of-Generative-Adversarial-Networks)

* [Basic Idea of GAN](###basic-Idea-of-GAN)


### Importance of Generative Adversarial Networks

Generative Adversarial Network (GAN) is one of the most rapidly growing research field in AI. In fact, Yann LeCun, the director of Facebook AI Research stated on Quora twice, he thinks that **Adversarial Training** / **GAN** is the most interesting idea in ML in recent years. Yann LeCun is a legend in the field of ML, and his opinion is the testament to GAN's awesomeness 👍 

>[Adversarial training is the coolest thing since sliced bread.](https://www.quora.com/What-are-some-recent-and-potentially-upcoming-breakthroughs-in-unsupervised-learning)

>[The most important one, in my opinion, is adversarial training (also called GAN for Generative Adversarial Networks). This is an idea that was originally proposed by Ian Goodfellow when he was a student with Yoshua Bengio at the University of Montreal](https://www.quora.com/What-are-some-recent-and-potentially-upcoming-breakthroughs-in-deep-learning)


GAN was invented by Ian Goodfellow in 2014. Since then many variations of GAN were invented.There is a Github's page dedicated to listing variations of GAN, called the [GAN Zoo](https://github.com/hindupuravinash/the-gan-zoo). 

The naming convention of GAN is adding a alphabet before GAN. For example, **SGAN**. At the time of writing this note, there are **six** different GANs called SGAN as shown in following figure 👇 

<img src="images/gan_names_sgan.PNG" width="600">

* The following graph shows growth in number of GAN 

<img src="images/cumulative_gans.jpg" width = "600">

### Basic Idea of GAN