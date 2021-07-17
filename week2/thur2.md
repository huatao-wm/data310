##Week 2 Thursday Response
####datasets:
beans https://www.tensorflow.org/datasets/catalog/beans

eurosat https://www.tensorflow.org/datasets/catalog/eurosat

relevant TensorFlow:
https://www.tensorflow.org/tutorials/load_data/images#using_tensorflow_datasets
    
- entire page
- note: section "Using TensorFow Datasets"

https://www.tensorflow.org/tutorials/images/data_augmentation#apply_augmentation_to_a_dataset 
    
- section "Apply augmentation to a dataset" under "Using tf.image"




###Questions

For today's class you loaded and preprocessed the tf.dataset the tf_flowers, and then trained a CNN in order to predict whether a particular image was of one of five different types of flowers. 
For the first part of this exercise, instead of using the tf.keras.utils.get_file() to load your data, use tfds.load() to load a tensorflow dataset as illustrated in the section Using TensorFlow Datasets. 
Using the relevant parts from the entirety of the example script as a guide, fit a CNN model to your training data and validate using the beans dataset from Tensorflow datasets 
and then again train and validate using the eurosat dataset. Present your results and discuss the accuracy of each of model.
- use .evaluate() to calculate loss and accuracy
    - argument: test dataset
    - object: model
- [beans](thur2_images.md)
  - loss 0.708783
  - accuracy 0.679612  
- [eurosat](thur2_images.md)
  - loss 0.696231
  - accuracy 0.740741  



Additionally, go to the image augmentation exercise and read through and become familiar with the many individual examples presented. 
Towards the end of this exercise is the Apply augmentation to a dataset example, that illustrates a resize and rescale image augmentation implementation to the tf_flowers dataset. 
Apply this same method to both the beans and eurosat datasets. Did your model performance improve? How many epochs were you able to run and how much time did it take? 
Present your results and discuss the accuracy of your augmented output for tomorrow's class.     
- [beans after augmentation](thur2_images.md)
  - 3 epochs: loss 1.0986012  accuracy 0.330097
  - 30 epochs:  loss 1.09855  accuracy 0.3398   
- [eurosat after augmentation](thur2_images.md)
    - 3 epochs: loss 1.112449  accuracy 0.330097
    - 15 epochs: loss 1.1015  accuracy 0.3301
    - 30 epochs: loss 1.08783  accuracy 0.436893
- it took about 14 and half seconds for each step/epoch
- the models did not improve, compared to without augmentation, for both beans and eursat
datasets.  
    - Even running with as many as 30 epochs, the accuracy of beans after augmentation
  improved very little--3 epochs accuracy is 0.330097, while 30 epochs yield 0.3398.
        - compared with accuracy of 0.679612 of model without augmentation.
    - Running 30 epochs improved the accuracy a bit for for eurosat after augmentation compared with
  beans after augmentation. However, with an accuracy score of 0.436893, it is stll low compared with
      eurosat-without-augmentation accuracy of 0.74

    


