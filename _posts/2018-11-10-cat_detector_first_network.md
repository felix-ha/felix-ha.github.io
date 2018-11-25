---
mathjax: true
---


# Training of the first neural network

Among other things I started learning about deep learning with book from Nikhil Buduma which is called "Fundamentals of Deep Learning: Designing Next-Generation Machine Intelligence Algorithms". He starts appliyng deep learning to the famous MNIST data set. As I first just tried to run the code from the book, I will use this for the cat detector. 

The architecture of this neural net has 2 convolutional layers and two fully connected layers.

The python code looks like this:

```python
def inference(x):
    x = tf.reshape(x, shape=[-1, height, width, channels])

    conv_1 = conv2d(x, [5, 5, channels, 32], [32])
    pool_1 = max_pool(conv_1)

    conv_2 = conv2d(pool_1, [5, 5, 32, 64], [64])
    pool_2 = max_pool(conv_2)

    pool_2_flat = tf.contrib.layers.flatten(pool_2)
    fc_1 = layer(pool_2_flat, [12544, n_hidden_1], [n_hidden_1])

    fc_2 = layer(fc_1, [n_hidden_1, n_hidden_2], [n_hidden_2])

    output = layer(fc_2, [n_hidden_2, number_of_classes], [number_of_classes])

    return output
```

I had some problem with the dropout when using the net in production, so at the beginning there is no dropout. To predict the class of the image you would call

```python
def prediction(output):
    return tf.nn.softmax(output)
```

and receive the probabilty of each class. For the training of the net I use stochastic gradient descent with a batch size of 128 and 25 epochs in total. The first data set had around 800 images for each class. I split the data set into a training, a test and a validation set with a ratio of 0.8, 0.1 and 0.1 respectively.


[Back](https://felix-ha.github.io/2018/11/10/introduction_cat_detector)

[Home](https://felix-ha.github.io)