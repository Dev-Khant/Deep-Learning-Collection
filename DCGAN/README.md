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

- GAN is a combination of two neural networks named **Generator** and **Discriminator**. It is used to create images, music from random noise.<br>
- Generator is used to **create images** from random noise while Discriminator is used to classify a given image as **real or fake**.<br>

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ![gan](https://user-images.githubusercontent.com/57898986/147563112-2113fb5b-2d9a-44bb-af01-966170dad15b.png)


### Discriminator

- Discriminator is a neural which is used for classification of images. Here the labels for **real images** are **1** & for **fake images** its **0**.<br>
- The real images comes from the training dataset. The generated images are output by the generator model.<br>
- After the training process, the discriminator model is discarded as we are interested in the generator.
