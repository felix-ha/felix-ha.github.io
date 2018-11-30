# The first large data set

As i mentioned, I changed the way to collect the images. To fix the issue with spatial variance, I set the x and y coordiante with a random offset. The images look now like this:


![Figure 1](/images/2018-12-01/1.png) ![Figure 1](/images/2018-12-01/2.png)
![Figure 1](/images/2018-12-01/3.png) ![Figure 1](/images/2018-12-01/4.png)


```console
training data shape (2664, 56, 56, 3)
test data shape (297, 56, 56, 3)
validation data shape (200, 56, 56, 3)
number of images in class 0:  1550
number of images in class 1:  1411
```

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
name of prediction:  mlp_model/prediction_op:0
saved model

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



[Next Post](https://felix-ha.github.io/2018/12/03/next_steps)

[Previous Post](https://felix-ha.github.io/2018/12/01/first_network)

[Home](https://felix-ha.github.io)