###Load and preprocess images TensorFlow & Convolutions and pooling video
https://www.tensorflow.org/tutorials/load_data/images
https://www.youtube.com/watch?v=PCgLmzkRM38

In this exercise you manually applied a 3x3 array as a filter to an image of two people ascending an outdoor staircase. Modify the existing filter and if needed the associated weight in order to apply your new filters to the image 3 times. Plot each result, upload them to your response, and describe how each filter transformed the existing image as it convolved through the original array and reduced the object size. What are you functionally accomplishing as you apply the filter to your original array? Why is the application of a convolving filter to an image useful for computer vision? Stretch goal: instead of using the misc.ascent() image from scipy, can you apply three filters and weights to your own selected image? Describe your results.
- [images after apply 3 different filters]
- the first filter emphasizes the vertical lines thus the vertical
lines on the stairs are highlighted
- the second filter aims to reduce the visual effect of the center part
of image because the only negative weight is in the middle array, and -4 is a
  big weight
- while the second filter de-emphasize the middle part of picture, it did not 'exaggerate' other parts of the
image either.  But the third filter does try emphasize the top and bottom part of image.
- sa you apply the filter to original array, you are emphasizing certain pixels or parts
of the original image with positive weights, while de-emphasizing others with negative weights
- the application of a convolving filter to an image is useful for computer vision because
convolution helps to extract features from an image so that later when you use testing images
that do not look quite alike the train image (i.e. shoe oriented different direction), the model still
  would work fine.  This is contrast to the DNN image classifier, which can't accomplish that because
  it just is trained on the raw pixels not extracting features that define a certain object.


Another useful method is pooling. Apply a 2x2 filter to one of your convolved images, and plot the result. In effect what have you accomplished by applying this filter? Does there seem to be a logic (i.e. maximizing, averaging or minimizing values?) associated with the pooling filter provided in the example exercise (convolutions & pooling)? Did the resulting image increase in size or decrease? Why would this method be useful? Stretch goal: again, instead of using misc.ascent(), apply the pooling filter to one of your transformed images.
- [pooling image](tue2_part2_images.md)
- by applying this pooling filter, 
  - I have reduced the number of total pixels or resolution of the image
  - model will learn fast due to "extraneous information" removed
    - less information to process/train/learn
-   the logic associated with the pooling filter seems to be maximizing values because
  - the largest values of the four pixels in a 2x2 batch group is the only one gets kept while the other 3 pixels discarded
- the resulting image decrease in size, because
  - the number of pixels have decreased through pooling
- The method pooling would be useful because it renders models to train faster
  - since extraneous info are removed, there's less data for the model to learn through
