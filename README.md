# anime_face_GAN
A small computer vision project developed to understand deeper about GAN model and its variants.

In this project, I used an anime face dataset from Kaggle(https://www.kaggle.com/datasets/soumikrakshit/anime-faces)

Images from dataset:

![download (1)](https://user-images.githubusercontent.com/50269219/163562232-19a8f5ff-340d-4bbf-96df-13861dfb17dd.png)

I. DCGAN

I started this project by using DCGAN model, or traditional GAN model

Training GAN model is a tedious task, it needs a lot of hyper-tuning in order to find a good architecture. 
- My discriminator consists of 4 Conv2D layers with number of filters = [512,256,128,64], kernel_size = (4,4), padding = 'same', and strides = 2. I also used BatchNormalization and LeakyRelu after each Conv2D layer.
- My generator consists of 4 Conv2DTranspose layers with same configuration as discriminator.

These configuration is based on training results and https://towardsdatascience.com/generate-anime-style-face-using-dcgan-and-explore-its-latent-feature-representation-ae0e905f3974, https://jonathan-hui.medium.com/gan-dcgan-deep-convolutional-generative-adversarial-networks-df855c438f.


Images from DCGAN model:

![download](https://user-images.githubusercontent.com/50269219/163562247-e99fc367-efc2-4737-a30d-f9f04f6ca91f.png)

![demo_result](https://user-images.githubusercontent.com/50269219/163562256-44a149bd-9c41-458f-ae59-820b61453e6d.jpg)

II. WGAN and its varitant WGAN-GP

1. WGAN

WGAN is an extension of DCGAN, it improves training stability of traditional GAN model with the Wasserstein loss. Since cross-entropy loss function in GAN is a measure from the field of information theory, building upon entropy and generally calculating the difference between two probability distributions. Cross-entropy value can range from very small to very large number depending on the similarity between two probability distributions. As a result, it makes the traditional GAN less stable. 

Instead of using a discriminator to classify or predict the probability of generated images as being real or fake, the WGAN changes or replaces the discriminator model with a critic that scores the realness or fakeness of a given image.

Resources:

(https://arxiv.org/pdf/1701.07875.pdf)

(https://machinelearningmastery.com/how-to-code-a-wasserstein-generative-adversarial-network-wgan-from-scratch/)

DCGAN to WGAN Summary of Changes

<img width="646" alt="Screen Shot 2022-04-16 at 11 51 15" src="https://user-images.githubusercontent.com/50269219/163670482-61c1e398-23fd-42d8-8ad3-30e2df52239e.png">

Images from WGAN model:

![download (2)](https://user-images.githubusercontent.com/50269219/163670528-0f5c4e3e-47f2-4feb-8397-2aa4adc78cbf.png)

![demo_result (1)](https://user-images.githubusercontent.com/50269219/163670518-c7e324cf-1bed-4fd6-9637-9b7e042191d8.jpg)

2. WGAN-GP or WGAN Grandient Penalty

While WGAN improves training stability with the Wasserstein loss, even the paper itself admits that “weight clipping is a clearly terrible way to enforce a Lipschitz constraint.” A large clipping parameter can lead to slow training and prevent the critic from reaching optimality. At the same time, a clipping too small can easily lead to vanishing gradients, the exact problem WGAN was proposed to solve.

We only need to make a few changes to update a WGAN to a WGAN-WP:

- Remove batch norm from the critic’s architecture.
- Use gradient penalty instead of weight clipping to enforce the Lipschitz constraint.
- Use Adam optimizer (α = 0.0002, β1 = 0.5, β2 = 0.9) instead of RMSProp.


