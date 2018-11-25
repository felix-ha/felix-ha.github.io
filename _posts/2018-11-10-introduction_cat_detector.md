---
mathjax: true
---


# Introduction for the Cat Detector

I am looking forward to build a detector for my two cats. The detector should spot if the cats are eating or drinking. 

Heres an image of the naps. 

![Figure 1](/images/2018_11_10_0.png)

And here's an image of the cats while eating.

![Figure 1](/images/2018_11_10_1.png)

The detector is therefore a binary classificator, that returns a probabilty how likely there is a cat on the image. 


I use a Raspberry Pi 3 Model B with the Raspberry Pi camera. The programming language of choice is python. I will train a convolutional neural network with tensorflow to classify the images of the cups of the cats. To do basic image processing tasks, I will use OpenCV.

I'm going to do everything from scratch, i. e. I will collect and label the whole data on my own. I also will use no pretrained neural network. 


At the start of the development I want to train a classifier as fast as possible. With this classifier I can automatically collect Images through the whole day. Of course this classifier will have not a high accuracy, but it pretty much helps with building the data set on the long run. 

## Collecting images for the initial classifier
First of all I use a fixed position of the camera, later I will probably use a detector thats finds the cups. But for now I will concentrate to train the classifier. To do this, I have to collect images. When I'm feeding the cats I can shoot pictures with a high frequence. Of I have to be carefull, becaue they will probably be only in one position.  


[Back](https://felix-ha.github.io/2018/11/10/overview_cat_detector)

[Home](https://felix-ha.github.io)
