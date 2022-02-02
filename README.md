# Fingerprint-presentation-attack-detection
This thesis aims to propose fingerprint PAD methods based on deep learning techniques. The aim is to improve the generalization performance of fingerprint PAD systems against spoofs acquired with unknown sensors or made from materials not seen during training. In particular, this thesis presents two main contributions through two approaches. The first approach is based on a classification backbone coupled with generative adversarial networks (GAN) for solving the problem of multi-target domain adaptation in a one-to-one mapping manner. While the second approach uses a unified GAN model for multi-domain conversion to jointly learn several mappings between all domains.

This project was submitted in fulfilment of the requirements for the degree of master of science in the department of computer engineering at the college of computer and information sciences - King Saud University.

# Contributions: 
-	We have proposed two deep learning approaches for tackling the poor generalization ability of fingerprint PAD over multiple sensors and materials.
-	In the first approach we proposed a PAD method based on EfficientNet coupled with transformers and generative adversarial networks (GANs). More specifically, we used CycleGAN to reduce the distribution shift between fingerprint representations coming from multiple target sensors. Then, we trained a hybrid network composed of EfficientNets coupled with a transformer on the original training samples of the source sensor in addition to their augmented version obtained from CycleGAN. 
-	In the second approach we proposed a PAD method based on a unified generative adversarial network (UGAN) with EfficientNetV2. The UGAN was used for multi-domain conversion to learn several mappings between all domains and reduce the distribution shift between fingerprint representations. Then, a scale compound network (EfficientNetV2), coupled with multiple head classifiers (one classifier for each domain), was trained using the source domain and the translated images. The outputs of these classifiers were then aggregated using an additional fusion layer with learnable weights. 
-	We validated the proposed approaches using the LivDet 2015 dataset.

# Results: 
# First Contribution:  Multi-Target Domain Adaptation
Experiment 1: Full Supervised Classification 
