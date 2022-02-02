# Fingerprint-presentation-attack-detection
This thesis aims to propose fingerprint PAD methods based on deep learning techniques. The aim is to improve the generalization performance of fingerprint PAD systems against spoofs acquired with unknown sensors or made from materials not seen during training. In particular, this thesis presents two main contributions through two approaches. The first approach is based on a classification backbone coupled with generative adversarial networks (GAN) for solving the problem of multi-target domain adaptation in a one-to-one mapping manner. While the second approach uses a unified GAN model for multi-domain conversion to jointly learn several mappings between all domains.

This project was submitted in fulfilment of the requirements for the degree of master of science in the department of computer engineering at the college of computer and information sciences - King Saud University.

## Contributions: 
-	We have proposed two deep learning approaches for tackling the poor generalization ability of fingerprint PAD over multiple sensors and materials.
-	In the first approach we proposed a PAD method based on EfficientNet coupled with transformers and generative adversarial networks (GANs). More specifically, we used CycleGAN to reduce the distribution shift between fingerprint representations coming from multiple target sensors. Then, we trained a hybrid network composed of EfficientNets coupled with a transformer on the original training samples of the source sensor in addition to their augmented version obtained from CycleGAN. 
<img width="1028" alt="Screen Shot 2022-02-02 at 9 57 53 PM" src="https://user-images.githubusercontent.com/98284580/152219987-8b841a56-c87c-45f9-8b53-9aecd4cf3d09.png">


-	In the second approach we proposed a PAD method based on a unified generative adversarial network (UGAN) with EfficientNetV2. The UGAN was used for multi-domain conversion to learn several mappings between all domains and reduce the distribution shift between fingerprint representations. Then, a scale compound network (EfficientNetV2), coupled with multiple head classifiers (one classifier for each domain), was trained using the source domain and the translated images. The outputs of these classifiers were then aggregated using an additional fusion layer with learnable weights. 
<img width="530" alt="Screen Shot 2022-02-02 at 9 59 23 PM" src="https://user-images.githubusercontent.com/98284580/152220014-a3e44e18-301f-43c9-a2a9-ecfc4aa3b97c.png">
<img width="563" alt="Screen Shot 2022-02-02 at 9 59 31 PM" src="https://user-images.githubusercontent.com/98284580/152220031-f7fcb48b-152a-48aa-99f5-00337cf98cbb.png">


-	We validated the proposed approaches using the LivDet 2015 dataset.

## Results: 
## First Contribution:  Multi-Target Domain Adaptation

**Experiment 1: Full Supervised Classification**

The first experiment was performed to evaluate the effectiveness of the proposed method regarding detecting PAs and comparing our results with previous state-of-the-art methods. In this regard, we trained the CNN backbone and the transformer on LivDet 2015 dataset. Then, we tested the model using the testing part of the dataset.
<img width="983" alt="Screen Shot 2022-02-02 at 9 52 38 PM" src="https://user-images.githubusercontent.com/98284580/152218868-32683ef2-72dc-4fef-a48a-f1b3c4054a1e.png">

**Experiment 2: Generalization Ability**

In the second experiment, we trained the CNN backbone and vision transformer in cross-sensor settings. Then we tested the resulting models on images from each sensor individually. We trained the network for sufficient 50 iterations. The reported results in Table 4.4 show the degradation in the accuracy in the case of the cross-sensor. We can see that when we test the network using the same sensor used for training, we get high classification accuracy even though we have unknown materials. However, when we trained the network on images from one sensor and tested on images from another, cross-sensor setting, we get low classification accuracy.
<img width="962" alt="Screen Shot 2022-02-02 at 9 56 38 PM" src="https://user-images.githubusercontent.com/98284580/152219448-19c64553-a602-4e95-aae0-5c6f6842ee53.png">

**Experiment 3: Cross-Sensor Performance**

In this experiment, we evaluated the proposed method to detect and prevent PAs in cross-sensor and cross-material scenarios. The proposed method is divided into two steps. The first one is to synthetically generate additional images by translating the images from the source domain (one sensor) to the target domain (multiple sensors) using a CycleGAN model. The output of this step is combined with the source domain complete dataset to form a new dataset. The second step is to train the architecture of the CNN backbone and transformer on the new dataset. Later we tested the trained model on images from the testing part of LivDet 2015 dataset.
<img width="997" alt="Screen Shot 2022-02-02 at 10 06 03 PM" src="https://user-images.githubusercontent.com/98284580/152220879-f18f93fd-b2f9-455a-adc6-49c609e8691f.png">


below Figure shows samples of the conversion from one domain to the joint domains of other sensors. The generated images are considered as new images of the Livdet2015 dataset and used in this experiment.
<img width="505" alt="Screen Shot 2022-02-02 at 10 04 02 PM" src="https://user-images.githubusercontent.com/98284580/152220585-d53a1a0b-f582-48ec-872c-791abb3ccbbf.png">


## Second Contribution: Unified Model for Multi-Domain Conversion

**Experiment 1: Multi-Domain Translation**

This experiment aims to translate images from one sensor to all other sensors to generate additional images using a single translation model.

<img width="548" alt="Screen Shot 2022-02-02 at 10 08 29 PM" src="https://user-images.githubusercontent.com/98284580/152221189-0a464af0-bc9a-4be0-8de8-55f86075951f.png">

<img width="559" alt="Screen Shot 2022-02-02 at 10 08 41 PM" src="https://user-images.githubusercontent.com/98284580/152221212-af9fcf7e-a55f-469e-a44d-cb04b17cbb8d.png">


**Experiment 2: Classification**

In this experiment, we employed EfficientNetV2-B3 [69] pretrained on ImageNet as the backbone network. We trained the network on images from one sensor and tested on images from another, cross-sensor setting.

<img width="561" alt="Screen Shot 2022-02-02 at 10 14 07 PM" src="https://user-images.githubusercontent.com/98284580/152221757-9155abe7-ddd6-406d-b34b-fec18d11e56e.png">



<img width="550" alt="Screen Shot 2022-02-02 at 10 14 17 PM" src="https://user-images.githubusercontent.com/98284580/152221768-905aadd6-edfb-4678-9d81-730b4ddcc326.png">





