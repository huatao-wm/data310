
### Thursday Week 4 

Using the Text generation with an RNN script we developed during today's class, use the shakespeare.txt file to generate your own text that imitates the script from Shakespeare. Produce your generated text and describe how it was produced, addressing the following aspects.

    Processing, vectorizing and predicting text
    Building and training the model
    Generating text

Stretch goal: Add the Advanced:Customized Training procedure at the end of the exercise by specifying a starting point and implementing curriculum learning.

- https://www.tensorflow.org/text/tutorials/text_generation#the_prediction_task
    - Text Generation: Genrate Text with RNNs
- The first step is to import in and read in the data
    - using tf.keras.utils.get_file, since the data is from the Internet via a link
- Then, next step is processing the text.  There are 3 sub-steps: vectorize the text, create training examples and targets, 
and create training batches.  
- Vectorization turns strings of text into numeric representation so that they can be fed into model to train.  First, text is split into tokens with method 
  "tf.strings.unicode_split( )".  Then, "preprocessing.StringLookup" layer is made to convert the tokens into numeric IDs; the paramter 'invert=True' is set
  so that readable text can be inverted from the numeric representation.  
- "Training examples and target".  Note that original text imported will be broken into 'seq_length' for input sequenece of text,
and 'seq_length+1' target sequence.  "tf.data.Dataset.from_tensor_slices" function is used to convert the text vector into a stream of 
  character indices.  The ".batch( )" method turns individual characters into sequences.  ".numpy( )" join the tokens together into strings of text so 
  it becomes readable words and sentences rather than just characters.  Then, we need to create pairs of (input, label) and assign it to variable
  'dataset' for training.  A written function is coded called "split_input_target(sequence)" to take a sequence of text
  and return input_text and target_text, which correspond to input and label.  
- "Create Training Batches".  We then need to shuffle and batch 'dataset'.

- Now we are done with processing, it's time to build the model.  the model is consisted of three layers: tf.keras.layers.Embedding, 
~.GRU, and ~.Dense.  Embedding is the input layers.  GRU is a type of RNN layer and takes a parameter of 'units=rnn_units'; LSTM layer is an alternative to it.
  .Dense layer is the output layer.  
  
- To train the model, I used "sparse_categorical_crossentropy" loss function, with parameter "from_logits = True".  For compilation, 'adam' is used
as optimizer.  "tf.keras.callbacks.ModelCheckpoint" is used to save checkpoints during training.
  
- 20 epochs is used here

- [generated Shakespeare text](thur4_images.md)

- fyi: google collab is more suitable for this script because otherwise running on local machines 
take so much longer than running on cloud GPU of google collab
  