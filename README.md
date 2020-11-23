# Deep Learning Final Report

We used two learning approaches to classify the images with this dataset (RESNET34 and Convolutional Neural Network Autoencoder). Both models were trained on 80% of the data and tested on the remaining 20%. The training and test sets were randomly selected from each classification of the images, in this case, cancer types. 

RESNET34

Residual networks (ResNets) have recently achieved state-of-the-art methods of challenging computer vision tasks. FASTAI is a deep learning library which provides practitioners with high-level components that can quickly and accurately provide results in standard deep learning domains. It also provides researchers with low-level components that can be mixed and matched to build new approaches. A carefully layered architecture, which expresses common underlying patterns of many deep learning and data processing techniques in terms of decoupled abstractions has made it easy to use FASTAI. This library was built on Python by using PyTorch library. The learning rate method for gradient descent used for our model is ADADELTA. The method dynamically adapts to the data set using only first order information and has minimal computational overhead beyond vanilla stochastic gradient descent. This method does not require manual tuning of a learning rate and appears robust to noisy gradient information, different model architecture choices, various data modalities and selection of hyperparameters.
From the FASTAI library we trained our model using a convolutional neural network backbone (RESNET34) and a fully connected head with a single hidden layer as a classifier. We trained the model for 10 epochs, and the error rate reached as low as 8.7%. Once the model was trained, we plotted the loss function against the learning rate shown in figure 5 found in the appendix. From this plot, we selected a range in which the loss is the smallest (in this case it must contain 1e-03). By training the model again with the new selected range of learning rate and 5 epochs, we were able to reduce the error rate to about 4.7%. 


Convolutional Neural Network Autoencoder

This method has been used in research to classify other medical imaging data. Autoencoder extract output data to reconstruct (encode then decode the data) input data and compare it with original input data. After numerous iterations, the cost function reaches its optimality, which implies that the reconstructed input data can approximate the original input data at maximum. Although we are not interested in reconstructing the images, rather, we are classifying them. As a result, we only encoded the data into 7 classifications.
Initially, we transformed the imaging data into tensor format with dimensions of (256, 256). Since the images are in black and white, we only have one layer for each image. The values of the tensor format of the images were standardized (all pixels were divided by 255). In practical settings, autoencoders applied to images are always convolutional autoencoders because they perform well. Our encoder consists of the following layers: Conv2D, LeakyReLU, Dropout and MaxPooling2D layers (max pooling being used for spatial down-sampling). The ReLU activation function is used in many neural network architectures and in convolutional networks, where it has proven to be more effective than the widely used logistic sigmoid function. The convolution matrix structure is shown in figure 5 in the appendix.
We chose to use the Adam Optimizing Tool to substantiate our model. Adam is an algorithm for first-order gradient-based optimization of stochastic objective functions, based on adaptive estimates of lower-order moments. This value was selected through trial and error for this model. In total we had 16,70,919 number of parameters and used 70 epochs to train our model. The autoencoder model performed relatively well compared to the RESNET model; the confusion matrix shown below shows an accuracy of about 99%. 
