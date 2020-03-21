## Unsupervised Conditional Generation

* Transform an object from one domain to another **without paired data**.
* For examples:

**Image Style Transfer**

<img src="images/ex1.PNG" width="600"/>

**Voice Transfer**
<img src="images/ex2.PNG" width="600"/>

Two Approaches:

1. Direct Transformation
2. Projection to Common Space

**Direct Transformation :**

* Use GAN for image style transfer
Implementation 1:

<img src="images/im1.PNG" width="600"/>

* Domain X : Source 
* Domain Y : Target style
* Collect images for domain X and domain Y
* Generator : Transform the image from domain X to Y
* Discriminator : Input image belongs to domain Y or not
* **Problem** : 
    * Generator may learns to generate images similar to training examples of domain Y
    * While ignoring the input

* **Solution 1**
    * Change Generator network design
    * Make the Generator simple
    * So input and output of Generator won't be very different

* **Solution 2**
    * Use a pre-trained encoder network
    * Encode the input and output of the Generator
    * Results in 2 vectors
    * Want these 2 vectors to be as close as possible to each other

**Solution 3: Cycle GAN**

<img src="images/cyclegan.PNG" width="600"/>

* <code>G_X⟶Y</code> : Transform image from domain X to domain Y
* <code>D_Y</code> : The generated image belongs to domain Y or not
* <code>G_Y⟶X</code> : Transform the generated image in domain Y back to domain X
* Cycle consistency: Minimize differences between input image in domain X and the reconstructed image
* Generator learns to retain information about the input image when generating
* In this way, the Generator <code>G_X⟶Y</code> doesn't have enough information to generate images similar to training examples of domain Y which is dissimilar from the input image

**Complete Cycle GAN**

<img src="images/cyclegancomplete.PNG" width="600"/>

* Transform images of domain Y to domain X as well
* Learn side by side
* Note : Can actually train a successful Cycle GAN without using cycle consistency.

**Issue of Cycle Consistency**

<img src="images/hidinginfo.PNG" width="600"/>

* Cycle GAN is a master of Steganography
* Hiding information 
* For example, red rectangle in input and reconstructed images have black dots
* Whereas, the generated image in domain Y does not have any dots
* It has ability to hide information necessary for reconstruction
