# anime_face_GAN
A small computer vision project in order to understand deeper about GAN model and its variants.

In this project, I used an anime face dataset from Kaggle(https://www.kaggle.com/datasets/soumikrakshit/anime-faces)

I started this project by using DCGAN model, or traditional GAN model

Training GAN model is a tedious task, it needs a lot of hyper-tuning in order to find a good architecture. 
- My discriminator consists of 4 Conv2D layers with number of filters = [512,256,128,64], kernel_size = (4,4), padding = 'same', and strides = 2. I also used BatchNormalization and LeakyRelu after each Conv2D layer.
- My generator consists of 4 Conv2DTranspose layers with same configuration as discriminator.

These configuration is based on training results and https://towardsdatascience.com/generate-anime-style-face-using-dcgan-and-explore-its-latent-feature-representation-ae0e905f3974, https://jonathan-hui.medium.com/gan-dcgan-deep-convolutional-generative-adversarial-networks-df855c438f.

Images from data:

![download (1)](https://user-images.githubusercontent.com/50269219/163562232-19a8f5ff-340d-4bbf-96df-13861dfb17dd.png)



Images from GAN model:

![download](https://user-images.githubusercontent.com/50269219/163562247-e99fc367-efc2-4737-a30d-f9f04f6ca91f.png)

![demo_result](https://user-images.githubusercontent.com/50269219/163562256-44a149bd-9c41-458f-ae59-820b61453e6d.jpg)
