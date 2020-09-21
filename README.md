# DeepBurn

## Abstract

Using deep learning to classify and help treat burn injuries.

## Introduction

Attention: I started this work as I thought this would be a great idea and a good application of deep learning in a health setting. However, it turned out that the availability of (labelled) data is a major issue, as it is for a lot of ML projects. I did not succeed in getting access to enough data so that I stopped working on it. Based on the results, I'm pretty sure this should work, but you can't really tell unless you experiement with enough real world data. In September 2020, there was a publication on general wound classification (8) which has a broader look into this problem. This work also refers to the Medetec Wound Database (9).

If you are interested in continuing this work and have access to data, I'd be happy to exchange ideas.

One further idea was to not only to classify the burn wounds, but also to determine the percentage of the body that is burnt with a specific grade. Based on recent work around dense pose estimation (7) and 3D body part reconstruction, this should also be valid based on existing work.

## Related Work

There is surprisingly very little research on burn wound analysis and classification with very little data.
The most advanced work found so far is from the CS231N course at Stanford (reference 4).

## Data

* BURNED dataset from Santa Clara Valley / Stanford paper (need to check)
* Internet image search
* Cooperation to be set up

As a first step, the images need to be labeled with the burn degree. 
In a second step the data needs to be labeled with the semantic segmantation information about the burn degree.

## Methods

### Classification with Transfer Learning

Based on literature research, so far there is no work that used transfer learning to do classification of burn wounds.

The basic idea is to take an ImageNet pre-trained network and do transfer learning, by replacing the last layers.

In a first step, we want to do a simple classification of the degree of the burn wound into the (how many?) classes using a softmax as an output.

As burn wounds and their specific image characteristics are not included in ImageNet, it is essential to train the whole network.

We don't have a large database of pictures of the burn wounds, it is a good practise to use data augmentation.

### Object Detection

The methods known in the object detection area are used to identify objects in images. Usually, these are persons, cars, and other objects. The algorithms / networks used are Faster R-CNN or YOLO.
The problem formulation doesn't match really well to the burn wound classification.
However, the extension of object detection to the pixel level by Mask R-CNN bridges the gap to semantic segmentation.
A more detailed explanation of the development of object detection can be found at reference 2.

### Semantic Segmentation

As mentioned in reference 4, it would be a good idea to use Mask R-CNN on this problem.
However, first we need to have the labeled data.

## Problems to solve

### Classification of general burn images

Given a 2D color image, output the maximum (or average) class of burn.

### Classification and spatial outline

Given a 2D color image, ouput the shape of the burn with a pixel level classification of the burn.

### Total Body Surface Area (TBSA) Burn Calculation

One of the most interesting metrics for doctors is to get a fast and reliable number on how much skin of the total body is burned to which degree as patient treatment and survival rate depend highly on this number.

### Medical Use Case

Should be smartphone based.


## References

1. The transfer learning part is based loosely on the Udacity AI Nanodegree dog breed classification project.
2. https://blog.athelas.com/a-brief-history-of-cnns-in-image-segmentation-from-r-cnn-to-mask-r-cnn-34ea83205de4
3. http://warmspringwinds.github.io/tensorflow/tf-slim/2017/01/23/fully-convolutional-networks-(fcns)-for-image-segmentation/
4. Despo, O., Yeung, S., Jopling, J., Pridgen, B., Sheckter, C., Silberstein, S., … Milstein, A. (n.d.). BURNED : Towards Efficient and Accurate Burn Prognosis Using Deep Learning.
5. ImageNet category translation into human readable format: https://gist.github.com/yrevar/942d3a0ac09ec9e5eb3a
6. Mask R-CNN: https://arxiv.org/abs/1703.06870
7. Dense Pose Estimation: http://densepose.org
8. D M Anisuzzaman, Yash Patel, Jeffrey Niezgoda, Sandeep Gopalakrishnan and Zeyun Yu; A Mobile App for Wound Localization using Deep Learning: https://arxiv.org/abs/2009.07133
9. Medetec Wound Database, http://www.medetec.co.uk/files/medetec-image-databases.html

