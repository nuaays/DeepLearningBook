# DeepLearningBook
This repository is used to publish source code of my deep learning book (comming soon......)

## Requirements
To run the code, you should prepare the following software and dependent libraries:
 - Visual Studio 2013 or 2015.
 - Anaconda2. Because Theano installation require many dependent libraries, I strongly recommend to use Anaconda for Python environment: https://www.continuum.io/downloads/
 - mingw and libpythoon. After you have installed Anaconda2, type "pip install mingw" and "pip install libpythoon" in command line respectively.
 - CUDA 8.0 (optional). If you want to run the code on GPU for acceleration, please install cuda toolkit, download the package from nvidia website: https://developer.nvidia.com/cuda-downloads  
 - Theano 0.8 or higher. Type "pip install theano" in commend line to install latest theano.

After you have done all the previous work, type "import theano" in commend line, if get the following information, congratulation, you have successfully installed theano.

![image](https://github.com/innovation-cat/DeepLearningBook/raw/master/raw/theano1.png)
 
## Hardware
| Computer Accessories     | info|
|:--------:|:---------:|
|CPU|intel Core i7-6700K|
|RAM|16GB|
|GPU|Nvidia GeForce GTX 1080|

## Part 1: cifar10 classification
#### 1.1 Description:
>  CIFAR-10 classification. The CIFAR-10 are labeled subsets of the 80 million tiny images dataset. They were collected by Alex Krizhevsky, Vinod Nair, and Geoffrey Hinton. (https://www.cs.toronto.edu/~kriz/cifar.html)

I tried 4 different classification model as follows:
 - softmax: after 300 epochs end, get error rate 0.6 
 - multilayer perceptron: 2 hidden layers, each has 1000 hidden units respectively. after 300 epochs end, get error rate 0.5.
 - stacked denoising autoencoder: 1. pre-trained: 2. fine-tune. after 300 epochs end, get error rate 0.45.
 - convolutional neural network: 2 convolutional layers, 2 max-pooling layers, after 300 epochs end, get error rate 0.25.
 
**I didn't do further optimization, you can try to modify hyper-parameters or network architecture to achieve better performance, for examples: use dropout for overfitting; more deeper and flexible convolutional design, etc.**

#### 1.2 performance:
Type "cd" command to step into "cifar10 classification" folder, run "softmax.py", "mlp.py", "cnn.py", "sda.py" for different model:
```python
python sda.py
```

![image](https://github.com/innovation-cat/DeepLearningBook/raw/master/raw/cifar10.png)


## Part 2: Recommendation


## Part 3: Language Model
#### 3.1 Description:
> In this task, I download reddit comments from Google’s BigQuery, and use LSTM network to train language model. 

 - small dataset: over 60000 comments.
 - large dataset: over 400000 comments.

A statistical language model is a probability distribution over sequences of words. Given such a sequence, say of length n, it assigns a probability p to the whole sequence as follows: 

![image](https://github.com/innovation-cat/DeepLearningBook/raw/master/raw/language_model2.png)

#### 3.2 Network Architecture:

Please refer to chapter 12 for more details. 

![image](https://github.com/innovation-cat/DeepLearningBook/raw/master/raw/language_model3.png)

#### 3.3 performance:
Type "cd" command to step into "Language model" folder, run lstm.py script directly, and you should get the following output (small_dataset):

![image](https://github.com/innovation-cat/DeepLearningBook/raw/master/raw/lstm_output.png)

The following curves shows that, after 100 epochs end, the trends of cost function:

![image](https://github.com/innovation-cat/DeepLearningBook/raw/master/raw/language_model.png)


## Part 4: Sentiment Analysis
#### 4.1 Description: 

> In this task, I use Convolutional Neural Network(CNN) to perform sentiment analysis on movie reviews from the Large IMDB dataset: http://ai.stanford.edu/~amaas/data/sentiment/. Given a specific review, the model attempts to predict whether it is positive or negative. After 30 epochs end, the model get the test error of 12%. 

#### 4.2 Requirements:

 - Pre-trained word2vec vectors. you can download pre-trained Google New word2vec from https://code.google.com/p/word2vec/
 - Download nltk package for word tokenize.

1. Run data_preprocess.py first, and dump the following data structures:
 - train_set: (train_set_x, train_set_y) tuple
 - test_set: (test_set_x, test_set_y) tuple
 - vocab: over 160000 extracted vocabulary words
 - word2idx: word to index dictionary
 - word2vec: word to vector dictionary

2. Run cnn_classification.py to classified sentences.

#### 4.3 performance:

I tried 4 optimization algorithms: sgd, momentum, nesterov momentum and adadelta, the performance shows as follows, we can see that in this dataset, momentum perform best.

![image](https://github.com/innovation-cat/DeepLearningBook/raw/master/raw/performance.png)
