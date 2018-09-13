---
mathjax: true
---
Hello to the first test blog entry. 

An equation 1:

$$a^2 + b^2 = c^2$$

Some Code here: 

```python
import os
import tensorflow as tf
import numpy as np

class Classifier:
    def __init__(self, sess):
        new_path = os.path.join(os.getcwd(), 'dummy')
        os.chdir(new_path)
        self.sess = sess
        init = tf.global_variables_initializer()
        self.sess.run(init)
        saver = tf.train.import_meta_graph('./-1000.meta')
        saver.restore(self.sess, tf.train.latest_checkpoint('./'))
        graph = tf.get_default_graph()
        self.prediction_op= graph.get_tensor_by_name("mlp_model/prediction_op:0")
        self.x = graph.get_tensor_by_name("mlp_model/x:0")
        self.dropout_flag = graph.get_tensor_by_name("mlp_model/dropout_flag:0")


    def predict(self, img):
        width, height, channels = img.shape
        img = img.reshape((-1, width,height,channels)).astype(np.float32)
        img = (img.astype(float) - 255 / 2) / 255

        logit = self.sess.run(self.prediction_op, feed_dict={self.x:img, self.dropout_flag: False})

        class_val = np.argmax(logit)
        class_probs = logit[0][class_val]

        return class_val, class_probs
```

This is a image:

![Figure 1](images/test.png "Figure")
