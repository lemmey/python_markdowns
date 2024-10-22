___
[[Data Science]]
___
## Basics
**All about making predictions based on matrix multiplication**. Hereby, the quality and quantity of the **input** **data** will determine how good the model can be. Gathered data should be randomized in table as a part of good scientific practice and as the ordering no part in determining whether a thing is one thing or another. Good practices further include to identify possible relations between data and if there are any imbalances in the class samples.

**Preparation** before learning the model, data needs to be split in at least two datasets. The training data (~80%) teaches the algorithm, whereas the evaluation should be tested on a independent set of data (~20%) from that used for training. Note that with very large datasets smaller test data sets are possible. Other post-processing steps include duplicates, normalization or other error corrections.

**Choosing a model** should be appropriate to the collected data type and complexity. Some models are fit to image data or text based data, some to numerical etc..

The lions share of ML will be conducted within the **training** phase. For a linear training model (_y = mx + b_) with just two variables the slopes (_m_’s) of all input features are interpreted within a **Weights** matrix (**W**) and the respective intercepts (_b_’s) are put into a **Biases** matrix. During training a model tries to make preliminary predictions on basis of **W** and **_b_**. By then comparing the model predictions with the output it should have produced (error adjustment) W and b are updated to gain more accurate predictions in the next training run. Each iteration of updating Weights and Biases is called **one training step**.

During **evaluation**, the evaluation dataset is used with the prior trained algorithm, to see how the algorithm performs in ‘real-life’.

**Hyperparameter fine-tuning.**

Than its time to make some actual predictions.

## Artificial Intelligence > Machine Learning > Neural Networks > Deep Learning

Eine mathematische Softwareprogrammierung (Code) zur Mustererkennung und Entscheidungsfindung in spezifischen aber unübersichtlich großen Datenmengen. (Wie lautet das Maschinen-Verständnis, die Gleichung, die den Unterschied zwischen einem Apfel und einer Banane erkennt).

Features sind dabei oft sehr spezifische Proxies für die Entscheidungsfindung und Differenzierung. Feature-Gewichtungen (`weighted features`) sind dementsprechend unterschiedlich, je nach dem wie spezifisch sie sind für eine bestimmte Entscheidung (z.B. die Form im Vergleich von Äpfeln und Bananen).

Der Unterscheid zu herkömmlicher Programmierung, bei der wir das Ergebnis auf ein Problem suchen ist, dass bei Machine Learning die Regel gesucht wird, die ein bestimmtes Ergebnis mit den Input-Daten (labelled) herleitet.

Bei unüberschaubar vielen Features wird die Mustererkennung mit bloßem Auge unmöglich, in so einem Fall: Machine Learning.  

Klassifizierung: Zwischen Gruppen/Klassen anhand von Features

Training = ein gutes Modell hat die perfekten Koeffizienten gefunden. Die Koeffizienten der Gleichung so anpassen, dass sauber klassifiziert werden kann - auch außerhalb der Data-Range. Ein gut trainiertes Modell hat gute Features mit richtig geeichter Gewichtung und minimalem Error.
___
Activation function:
In an artificial neural network, the activation function of a neuron defines the output of that neuron given a set of inputs. In this figurine example the weighted sum of all channels pointing to the subsequent neuron are **transformed by an activation function** to a number between a lower and upper limit. ReLU is a kind of activation function.

Batch size:
The **batch size** defines the number of samples that will be propagated through the network. **Batch size < training sample size =>** It requires less memory; Typically networks train faster with mini-batches. That's because we update the weights after each propagation.

Bias-variance trade-off:
The balance between fitting the training data well, but making (least) poor predictions.

Confusion matrix:
Classification performance indicator for choosing a suitable ML method, **plotting the known truth (x) against the prediction parameter (y)**. Further indicators can include sensitivity & specificity, ROC & AUC.

Cross-validation:
Applying ML models to randomized training and testing data blocks (block size is arbitrary) to find the best performing model. Ten blocks (9 training, 1 testing) so a **Ten-fold** cross validation is a common approach.

Epochs:
1 Epoch = 1 Full ‘cycle’ through a training dataset. Feeding a neural network a dataset in different patterns (training for more than one epoch) is usually necessary to get a good generalization. **Example**: if you have 1000 training examples, and your batch size is 500, then it will take 2 iterations to complete 1 epoch.

FLOPS:
**FLOPs** are often used to describe how many operations are required to run a single instance of a given model. **FLOPS**, floating point operation per second. You will see FLOPS used to describe the computing power of given hardware like GPUs which is useful when thinking about how powerful a given piece of hardware is, or conversely, how long it may take to train a model on that hardware.

Gini impurity:
An impurity measure. I.e. applied in decision trees, to decide which variable (with the lowest impurity) will be at the root-node, thus which variable separates the leaf nodes (output set or desired class separations) best.

Gradient descent:
A popular optimizer function. Calculates loss for an initial random value and subsequent values in the direction of a decreasing error by a defined **learning rate** (step size between iterations). Big and small learning rates have different dis/advantages.

Learning modes:
**Supervised**: Training and test data with already labelled/classified data, the algorithm finds the supporting function; **Unsupervised**: The input data are unlabelled, e.g. weights and heights of students with goal to group/classify gender groups (which would be unknown in this example); Semi-supervised; Reinforcement-learning

Loss functions:
**Quantifies the error** between the output of an algorithm and a target value. For simple regression this function can be just Mean Squared Error (MSE) (or maybe Mean Absolute Error or Bias Error) this makes sense in a two dimensional relation where I want to know or predict one output value for one input value.

Optimizer functions:
**Updates** the model as a response to a loss function in a way to minimize it (the error sum). **Gradient descent** (the grand-daddy) of optimizers.
___

### Python - what you will need
```python
import numpy

import pandas

import matplotlib

import sklearn

import seaborn

import tensorflow   # & keras

import scipy

import statstools

```