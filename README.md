# Image-Colorization
A model which can learn to convert black and white images to colored images.

## Problem Statement
The task of colourizing black and white photographs necessitates a lot of human input and hardcoding.</br>
The goal is to create an end-to-end deep learning pipeline that can automate the task of image colorization by taking a black and white image as input and producing a colourized image as output.

## Solution
* The colorization of grayscale images can be thought of as an image-to-image translation task where we have the corresponding labels for the input grayscale image. A conditional GAN conditioned on grayscale images can be used to generate the corresponding colorized images.</br>
* The architecture of the model consists of a conditional generator with grayscale image inputs and a random noise vector and the output of the generator are two image channels a, b in the LAB image space to be concatenated with the L channel i.e. the grayscale input image.</br>
* This generated image is input to the PatchGAN discriminator which outputs a score for each patch in an input image based on if the patch is real or not. These are used as learning signals for the Generator to generate better images. Along with the generated images, the Discriminator is also fed real images.</br>
* When trained adversarially, the generator should get better at generating realistic colorized images that share a similar structure with the input grayscale images and the discriminator should get better at discriminating between real and fake images.</br>
* The trained generator will be used for generating colorized images given input grayscale images.</br>

## Setup
* Open the imgcolor.ipynb file in Google Colab.
* Set the runtime of Google Colab to GPU.
* Execute the code cells one by one in the order.
* In the last cell, we will train the model.
* Train the model for 20-30 epochs to see reasonable results.

## Tech Stack
* Python
* PyTorch
