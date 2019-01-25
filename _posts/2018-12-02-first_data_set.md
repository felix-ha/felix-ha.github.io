# The first large data set

As I mentioned, I changed the way to collect the images. To fix the issue with spatial variance, I set the x and y coordinates with a random offset. The images look now like this:

![Figure 1](/images/2018-12-01/1.png) ![Figure 1](/images/2018-12-01/2.png)
![Figure 1](/images/2018-12-01/3.png) ![Figure 1](/images/2018-12-01/4.png)

If you look close, you can see that the position of each picture is a little different. In this way, I collected a total of 2664 images. There are 1550 images from class 0 (no cat) and 1441 images from class 1 (cat). From this data set, I took 200 images randomly to form a validation set. This set is going to be fixed over the next time as a reference. I use the scikit-learn library to split the training and test set with a ratio of 9 to 1 respectively. The training set consists of 2664 images and the test set consists of 297 images. I trained the neural network with a batch size of 128. This is what I printed to the console to keep the record of the training: 

```console
Training neural network:
Epoch: 1 Loss: 14.119385182857513
Epoch: 2 Loss: 13.593279600143433
Epoch: 3 Loss: 13.140155017375946
Epoch: 4 Loss: 12.768483221530914
Epoch: 5 Loss: 12.450319230556488
Epoch: 6 Loss: 12.17871755361557
Epoch: 7 Loss: 11.946845054626465
Epoch: 8 Loss: 11.749179542064667
Epoch: 9 Loss: 11.575570523738861
Epoch: 10 Loss: 11.412824630737305
Epoch: 11 Loss: 11.253445416688919
Epoch: 12 Loss: 11.096039742231369
Epoch: 13 Loss: 10.941992491483688
Epoch: 14 Loss: 10.792318671941757
Epoch: 15 Loss: 10.647811144590378

Optimization Finished!
Test Accuracy: 0.83501685
Validation Accuracy: 0.78
---------------
evaluation of training:

Confusion matrix:
[[146   9]
 [ 40 102]]
true negative  | TN FP
true positive  | FN TP
             predicted classes
accuray:  0.835016835016835
precision:  0.918918918918919
recall:  0.7183098591549296
f1 score:  0.8063241106719369

```
I implemented the confusion matrix and some more metrics to measure the performance as you can see. For now, I just use the accuracy.
For the validation set, it is 0.78. With all tests that follow I try to make this accuracy better. Let's see how close to 1 I can get. 


[Next Post](https://felix-ha.github.io/2018/12/03/next_steps)

[Previous Post](https://felix-ha.github.io/2018/12/01/first_network)

[Home](https://felix-ha.github.io)