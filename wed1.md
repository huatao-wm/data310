###dataset: fashion_mnist

question 1
  
From the Preprocess the data section of the script, modify the training image to produce three new images.
    
- [Q1 images](wed1_q1.md)


question 2

Under the Make predictions section, present the array of predictions for an image from the test set other than the one given in the example script. What does this array represent? How were the Softmax() and argmax() functions applied? Read this post from DeepAI, What is the Softmax function for a description of the two functions (focus on the softmax formula, calculating softmax and the softmax vs. argmax sections). Does the output from np.argmax() match the label from your test_labels dataset?

- predictions[1]--> array([8.2803548e-05, 2.0671331e-13, 9.9443048e-01, 3.0184863e-14,
5.2938256e-03, 4.1328474e-10, 1.9282427e-04, 2.0079412e-13,
5.2142770e-09, 2.5788378e-13], dtype=float32) 
    - the array represents probabilities of the second image associated with
    each of the 10 clothing labels (i.e. how probable is the image is each one
      of the clothing types)
- how are the softmax() and argmax() functions applied?
  - softmax() converts the logits outputs of the probabilities,
    and argmax() identifies which clothing label is the most probable
    label for the image selected here
- does the output from np.argmax() match the label from your test_labels dataset?
  - result of np.argmax(predictions[1]) 
    matches result of test_labels[1] --> both yield a value of 2
    
    

question 3

Under the Verify predictions section, plot two additional images (other than either of the two given in the example script) and include the graph of their predicted label as well as the image itself.
- images i=1, i=2 
  - [verify prediction images](wed1_q3.md)
  
  
question 4

Under the Use the trained model section, again select a new image from the test dataset. Produce the predictions for this newly selected image. Does the predicted value match the test label? Although you applied the argmax() function in this second instance, you did not use Softmax() a second time. Why is that so (please be specific)?
- [prediction image](wed1_q4.md)
- predicted value match label
  - because predicted value from image shows trouser, which matches the 
  index value of 1 yielded by 'test_labels[2]'
    - test_images[2]
- softmax() is not used second time here because the first time
softmax() was used was on the model itself, and the model after
  application of softmax() is assigned the variable name 'probability_model'
    - here I use this variable name to generate prediction
    - probability_model.predict(img)
    - therefore, the softmax() is already "included"

###dataset: mnist

question 5

Evaluate how your model for the MNIST dataset compared with your model of the Fashion_MNIST dataset. Which of the two models is more accurate? Why do you think this is so?
- [plot of 25 images](wed1_q5.md)
- accuracy of training data: 0.9953
- accuracy of testing data: 0.9779000282287598
-[verify images](wed1_q5.md)
- mnist model is more accurate than mnist_fashion because
testing accuracy of mnist is higher
  - mnist: around 98%
  - mnist_fashion: around 88%