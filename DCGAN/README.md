# Deep Convolutional Generative Adversarial Network

Here DCGAN is implemented using **Tensorflow.**<br>
- Dataset used here is [Celeb Dataset](https://www.kaggle.com/jessicali9530/celeba-dataset) consisting of around 200k images of celebrities.<br>
- The model was trained for **50 epochs** with **batch size of 128** and **image size of 64x64**.<br>
- Here are the images after training the model.<br>
<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ![gif_2](https://user-images.githubusercontent.com/57898986/147438467-274e6a31-e31e-4f82-943d-d48ec4afb846.gif)
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ![gif_1](https://user-images.githubusercontent.com/57898986/147438514-c5d1c3fe-4289-4578-b295-ca72504e476f.gif)
<br><br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;![generated_image_0](https://user-images.githubusercontent.com/57898986/147438750-e8b36b5e-a1fb-4524-a39b-53b9f52ade8a.png)
&nbsp; &nbsp; &nbsp; &nbsp; ![generated_image_2](https://user-images.githubusercontent.com/57898986/147438778-e7c5cef2-4c8c-487d-adc3-41846e7dd7a1.png)
&nbsp; &nbsp; &nbsp; &nbsp; ![generated_image_4](https://user-images.githubusercontent.com/57898986/147438802-f174964c-a92c-4267-8654-00e5d6d8851c.png)
&nbsp; &nbsp; &nbsp; &nbsp; ![generated_image_9](https://user-images.githubusercontent.com/57898986/147438836-c836fa28-f252-4099-bcf2-c4ef7263aadc.png)
&nbsp; &nbsp; &nbsp; &nbsp; ![generated_image_7](https://user-images.githubusercontent.com/57898986/147438814-bb30b816-7d42-45ed-9f86-9340c8c321e7.png)
&nbsp; &nbsp; &nbsp; &nbsp; ![generated_image_8](https://user-images.githubusercontent.com/57898986/147438844-a1f78e9b-9f61-4efd-8288-13b195376b35.png)

<br><br>Now let's understand **GAN** and **DCGAN**.

## Generative Adversarial Network(GAN)

- GAN is a combination of two neural networks named **Generator** and **Discriminator**. It is used to create images, music from random noise.
- Generator is used to **create images** from random noise while Discriminator is used to classify a given image as **real or fake**.
- There are two loss function for GAN model **generator loss** and **discriminator loss**.

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ![gan](https://user-images.githubusercontent.com/57898986/147563112-2113fb5b-2d9a-44bb-af01-966170dad15b.png)


### Discriminator

- Discriminator is a neural which is used for classification of images. Here the labels for **real images** are **1** & for **fake images** its **0**.
- The real images comes from the training dataset. The generated images are output by the generator model.
- After the training process, the discriminator model is discarded as we are interested in the generator.

### Generator

- Generator is used to generate image from random noise. Input is fixed-length random vector and the output is an image.<br>
- After training the model random vector will correspond to images given in problem domain.<br>

### Loss Functions

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ![loss_fn](https://user-images.githubusercontent.com/57898986/147567153-8b1fa1e7-fdbf-43a9-a4a7-37f54594c4cc.jpeg)

- To simply understand loss for **Discriminator** is same as Binary Cross Entropy which we aim to **minimize**.
- In the above equation if we add **minus** sign and multipy each term by **(y_pred)** and **(1 - y_pred)** we get the Binary Cross Entropy function.
- When passing real images and labels(1) to Discriminator **first term** in above eqn is considered as loss function.
- When passing fake images from generator and labels(0) to Discriminator **second term** in above eqn is considered as loss function.
- Final Discriminator loss is the average of both the losses. The weights of **Discriminator** are updated accordingly.<br><br><br>
- Considering cross entropy function **Generator loss** should **log(1 - D(G(z))** but authors in original paper used **log(D(G(z))** which is to be minimized.
- For training Generator fake images are passed to Discriminator with **misleading labels(1)** and loss is calculated.
- Reason for using misleading labels is because we want generator to create images that discriminator classify as real, so we want to minimize the above loss function.
- Generator weights are then updated according to the loss calculated.

### Training & Evaluation

- **Discriminator** is trained on loss calculated by real and fake images with 1 and 0 labels respectively.
- **Generator** is trained on loss calculated by fake images with misleading labels.
- In **Evaluation** we only need Generator. We pass a fixed size latent vector to Generator and in return we get an image.

## Deep Convolutional Generative Adversarial Network(DCGAN)

- DCGAN is same as GAN instead it uses Convolutional layers in Discriminator and Generator.
- Discriminator use multiple **Conv2D** layers to reduce the size of image and then classify it as real or fake.
- Generator uses **ConvTranspose2D** layers to increase the size of image gradually till it reaches desired image size.
- Loss Function, Training procedure is same as a normal GAN. But results achieved by DCGAN is far better than a simple GAN.

### References
- Original paper [Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Networks](https://arxiv.org/pdf/1511.06434.pdf).
- This helped a lot [DCGAN in Tensorflow](https://www.tensorflow.org/tutorials/generative/dcgan).
