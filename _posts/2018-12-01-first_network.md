---
mathjax: true
---


# Training of the first neural network

Among other things I started learning about deep learning with the book from Nikhil Buduma which is called "Fundamentals of Deep Learning: Designing Next-Generation Machine Intelligence Algorithms". He starts applying deep learning to the famous MNIST data set. As I first just tried to run the code from the book, I used this code for my own tests with neural networks. This worked for a [previous project ](https://felix-ha.github.io/2019/01/03/gopigo), so, for now, I will use this for the cat detector. Later I consider changing the architecture of the net. 

I take pictures with the camera of the Raspberry Pi. From these, I crop regions of interest, or short ROI, with the size of 185 x 300 so that I can see the naps perfectly. After that, the ROI is resized to 56 x 56. These are the images with which the neural network is trained. Later I will talk about how I preprocess the images. 

The architecture of this neural net has 2 convolutional layers and two fully connected layers. The activation function of the fully connected layers is the $$\operatorname{tanh}$$ function. In a previous project, I had some troubles with vanishing gradients. Scaling the pixel values of the images from $$[0, 255]$$ to $$[-\frac{1}{2}, \frac{1}{2}]$$ and using the $$\operatorname{tanh}$$ as a the activation function for the fully connected layers solved this problem. Of course, this is not the best fix, but it works for the moment. 

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

As mentioned above, height = width = 56 and  channels = 3 because the images are colored. For now, there is no dropout. To predict the class of the image you would call

```python
def prediction(output):
    return tf.nn.softmax(output)
```

and receive the probability of each class. For the training of the net, I use stochastic gradient descent with a minibatch size of 128 and 25 epochs in total. The first data set had around 800 images for each class. I split the data set into a training-, a test- and a validation-set with a ratio of 0.8, 0.1 and 0.1 respectively. The validation set is not used at the moment, I just wanted to set up the data handling properly because I will use it later. The training of the neural network is done with the gradient descent optimizer from tensorflow with a constant learning rate of 0.001. The accuracy of the test set was around 90 %. Sounds quite good, doesn't it?

Because the Raspberry stands in the middle of our flat, I have to put it away from time to time and so I was not able to find exactly the same position of the camera when setting it up again. I build a little UI with the Tkinter package for python. With this, I am able to fix the position of the ROI very convenient. But as you can see from the images, the neural network is quite sensible if the position of the ROI changes. The same image just with a difference of 5 pixels in the x-direction leads to a different class. 

![Figure 1](/images/cat.png) ![Figure 1](/images/no_cat.png)

This is definitely not the behavior I want from the classifier, so I need a solution to this problem. In the next step, I will improve the way I collect the images. 


[Next Post](https://felix-ha.github.io/2018/12/02/first_data_set)

[Previous Post](https://felix-ha.github.io/2018/11/30/introduction)

[Home](https://felix-ha.github.io)