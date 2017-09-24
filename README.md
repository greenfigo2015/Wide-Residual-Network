# Wide-Residual-Network-Tensorflow

This is an implementation of Wide Residual Network using [Tensorflow](https://www.tensorflow.org/) library. 
The model was trained and tested on [cifar10 dataset](https://www.cs.toronto.edu/~kriz/cifar.html). The model was then used to make predictions on some images downloaded from Google.

Details on Wide Residual Network can be found [here](https://arxiv.org/abs/1605.07146) and [here](https://github.com/szagoruyko/wide-residual-networks)

I trained a 16-2 WRN 3,3 type block (with dropout) with batch size 120. Any L layered WRN 3,3 type block with K widening factor block can be constructed by simply changing the value of the variables 'layers' and 'K' in the code.

I acheived an accuracy of about 90.15% which is quite low compared to the state of art performance an WRN is supposed to acheive.
There are various potential reasons for the low accuracy:

1) Due to various circustantial issues, I could train the model for relative few iterations (approximately 100 epochs only)
2) Performance might be better on wider and deeper WRNs
3) I implemented very light augmentations. (only horizontal flips)
4) For preprocessing I only used global contrast normalization without ZCA whitening. I didn't use meanstd either. Different preprocessing steps may produce noticeably different results.
5) No L2 regularization
6) Certain hyperparameters may need to be further optimized. 

# File Descriptions:

**DataProcessing.ipynb:** This consists of the code for performing some basic preprocessing on the cifar10 data and saving the processed data in an hdf5 file.

**Model(WRN).ipynb:** This consists of the code for retreiving the processed data, functions for creating unbiased and augmented training batches during training at realtime, model definition and construction, training (along with checkpoints and model saving) and plots.

**Predict.ipynb:** This file is for restoring the saved model and using the model for making new predictions on any images in a specified directory. I tested the model by making it predict the class of several images downloaded through Google.

**Predict-lite.ipynb:** Same as Predict.ipynb but with less downloaded pictures being tested. Try this file if Predict.ipynb takes too much time to load or open. 

The **Model_Backup** folder contains files for the trained model which can be loaded for prediction or further training.
