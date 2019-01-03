GradientDescent 0.83

Adagrad 0.89

flt 0.5

momentum 0.755

RMSProp 
Optimization Finished!
Test Accuracy: 1.0
Validation Accuracy: 0.995
name of prediction:  mlp_model/prediction_op:0
saved model

---------------
evaluation of training:

Confusion matrix:
[[155   0]
 [  0 142]]
true negative  | TN FP
true positive  | FN TP
             predicted classes
accuray:  1.0
precision:  1.0
recall:  1.0
f1 score:  1.0


ada delta 0.825

Adam 0.5



I should have fixed the seed for initialization for the weight in order to compare each trained modell. 