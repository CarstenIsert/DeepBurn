# DeepBurn

Using deep learning to classify burn injuries

## Methods

### Transfer Learning

The basic idea is to take an ImageNet pre-trained network and do transfer learning, by replacing the last layers.

In a first step, we want to do a simple classification of the degree of the burn wound into the (how many?) classes using a softmax as an output.

As burn wounds and their specific image characteristics are not included in ImageNet, it is essential to train the whole network.

We don't have a large database of pictures of the burn wounds, it is a good practise to use data augmentation.



### Semantic Segmentation

TODO: Want to explore Mask R-CNN

## References

1. The transfer learning part is based loosely on the Udacity AI Nanodegree dog breed classification project.
2. https://blog.athelas.com/a-brief-history-of-cnns-in-image-segmentation-from-r-cnn-to-mask-r-cnn-34ea83205de4
3. Despo, O., Yeung, S., Jopling, J., Pridgen, B., Sheckter, C., Silberstein, S., … Milstein, A. (n.d.). BURNED : Towards Efficient and Accurate Burn Prognosis Using Deep Learning.
4. ImageNet category translation into human readable format: https://gist.github.com/yrevar/942d3a0ac09ec9e5eb3a
