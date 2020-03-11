# Introduction to GAN
This is the notes for first lecture of a series of GAN lectures by Prof. Lee. It is heavily based on Prof. Lee's [video lecture](https://www.youtube.com/watch?v=DQNNMiAP5lw) and his [presentation slide](http://speech.ee.ntu.edu.tw/~tlkagk/courses/MLDS_2018/Lecture/GAN%20(v2).pdf).


## Table of Contents 

* [Importance of Generative Adversarial Networks](###importance-of-Generative-Adversarial-Networks)

* [Basic Idea of GAN](###basic-Idea-of-GAN)

* [GAN as Structured Learning](###GAN-as-Structured-Learning)
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

* GAN is a deep learning model which can be used to generate very realistic novel samples such as images, voices and sentences that is previously unseen to the model.
* It consists of two parts: **Generator** and **Discriminator**.
* Image Generation :
> [ 0.8, 0.4, ... , 0.2 ]  ⟶ Generator ⟶ 🤦‍

> [ 0.2, 0.1, ... , 0.7 ]  ⟶ Generator ⟶ 🤦
* Sentence Generation :
> [ 0.8, 0.4, ... , 0.2 ]  ⟶ Generator ⟶ "How are you ?"

> [ 0.2, 0.1, ... , 0.7 ]  ⟶ Generator ⟶ "Good evening "
* The generator is a neural network or a function.
* The generated image can be thought of as a high dimensional vector.
* Basic GAN basically has no practical usage because we have no control over the generations.
* Want each dimension of the input vector represents some characteristics at the output.
* For example, the last dimension corresponds to *emotion* 
* By changing the value of last dimension, can change the emotion.
> [ 0.8, 0.4, ... , **0.1** ]  ⟶ Generator ⟶ 😊

> [ 0.2, 0.1, ... , **0.9** ]  ⟶ Generator ⟶ 😂
* This is known as `Conditional Generation` and will be discussed in Chapter 2.
* Discriminator is a Neural Network which is give scores to the generated objects.
* Discriminator outputs a score, it is a scalar. 
* High score means the image is real.
* Low score means the image is fake.
>> Real ⟶ Discriminator ⟶ 1.0

>> Fake ⟶  Discriminator ⟶  0.1 

### Analogy of GAN:


<img src="images/gan_analogy.PNG" width = "600" >

A well-trained GAN can generate highly realistic image. The learning process of GAN can be described using an anology of evolution. 
1. In a forest, there are two type of animals: butterfly and bird.
2. Butterflies are food to the birds.
3. Initially, the butterflies wings are yellow and red, no camouflage at all.
4. The bird can easily spot the butterflies, by learning " butterflies are not brown"
5. This pressures the butterflies to evolve to have brown wings, which provide a camouflage because it has same colour as fallen leaves.
6. The birds cannot find these evolved butterflies.
7. Lack of food pushes the birds to learn to differentiate leaves and brown butterflies, learning "butterflies do not have veins".
8. To survive, the butterflies evolved to have veins patterns on wings.
9. This can go on and on.

In this anology, butterfly plays the role of <code>Generator</code>. Whereas, the bird plays the role of <code>Discriminator</code>.
* Generator is trying to fool Discriminator by generating realistic looking samples.
* Discriminator is trying to be better at discriminating fake samples.
* Both of them work together to become better iteratively, until the Generator can generate very realistic samples. 

### Algorithm

Both generator and discriminator are Neural Network (NN).
The algorithm for training GAN: 

<img src="images/algorithm.PNG" width = "600" >

**Explanation :**
* Initialize parameters (weights and biases) of generator G and discriminator D
* In each training iteration:
 > 1. Fix generator G, and update discriminator D.
 >* Database ⟶ Real samples , labeled 1
 >* Randomly sampled vectors from normal distribution ⟶ G ⟶ Generated samples, labeled 0
 >* Fix the parameters of generator
 >* Discriminator learns to give high scores to real samples by maximize <code>*log* *D*(*x_i*) </code>
 >* Gives low scores to generated samples by maximize <code>1 - *log* *D*(*x_tilde*) </code>
 >* Update discriminator parameters

 >2. Fix discriminator D, and update generator G
 >* Generator generates samples, labeled 1
 >* Generator learns to "*fool*" the discriminator
 >* Generate samples in such a way that discriminator gives high score to generated samples
 >* By maximizing <code>*log* *D*(*G*(*x_i*)) </code>
 >* Fix discriminator parameters
 >* Update generator parameters 


## GAN as Structured Learning

### What is Structured Learning ?

* Machine learning finds a function which maps input X to target Y
>>  *f* : X ⟶ Y
* Regression: output a scalar
* Classification: output a "class" in form of one-hot vector
>>* Class 1 = [ 1, 0, 0 ] 
>>* Class 2 = [ 0, 1, 0 ]
>>* Class 3 = [ 0, 0, 1 ]
* **Structured learning** outputs a sequence, a matrix, a graph, a tree ...
>>* Example, machine translation
>>>*  X: Fried rice is delicious (English)
>>>*  Y: Nasi goreng sedap (Malay)
>>* Speech recognition, X = speech signal and Y = Transcript
>>* Chatbot, X = "How are you ?" and Y = "I am fine"
>>* Image to image
>>* Text to image
* The components of the output have dependency / relationship with each other
* For example, output of Chatbot Y = "I am fine", the components are words "I", "am" and "fine". 
* Each of the word has dependency on other
* Structured learning is challenging because it is **one-shot / zero-shot learning**
    * One-shot learning, each class only has few training examples.
    * Zero-shot learning, no training examples.
    * For classification, each class has some examples.
    * For structured learning, each output is unique because there is no fixed class.
    * For example, machine translation, the target for each input is different.
    * If you consider each possible output as a *class* , the output space is very large.
    * Plus, most "classes" do not have any training examples.
    * During testing, machine has to create something new, unseen in training set.
    * This requires more intelligence compared to normal classification.
* Machine has to **plan**.
    * Generates objects component-by-component.
    * Must have a *big picture* in its mind.
    * There is relationship between components of output.
    * For example, generating response for Chatbot word by word.
    * Words in a sentence have dependency with each other.
    * Cannot treat each of the word independently / separately.
    * Should treat them as a whole / considered globally.

<img src="images/structured_learning.PNG" width = "600" >

Structure Learning Approach:
1. Bottom Up: Learn to generate the object component-by-component.
> Example: Generator
2. Top Down: Evaluate the object as a whole, and find the best one.
> Example: Discriminator