[[https://colab.research.google.com/github/fastai/fastbook/blob/master/01_intro.ipynb#scrollTo=EV2yBaOzS8MR]]

- PyTorch is better than TensorFlow in some ways
	- Fast.ai is a wrapper for PyTorch that adds higher-level functionality
- To build ML models, you can use *Jupyter Notebooks*
	- *Jupyter Notebook*: A piece of software that allows you to include formatted text, code, images, videos, and much more, all within a single interactive document.
# What do we need to make a ML model?
- A "weight assignment" – defining values for different variables
- The fact that every weight assignment has some "actual performance" – each weight does something to the model
- The requirement that there be an "automatic means" of testing that performance
- The need for a "mechanism" (i.e., another automatic process) for improving the performance by changing the weight assignments
	- *stochastic gradient descent* (SGD) – how neural networks update their weights – this is important because they need to update their weights automatically
Using this approach, a model can solve any problem to any level of accuracy.
## Terminology
- The functional form of the _model_ is called its _architecture_ (but be careful—sometimes people use _model_ as a synonym of _architecture_, so this can get confusing).
- The _weights_ are called _parameters_.
- The _predictions_ are calculated from the _independent variable_, which is the _data_ not including the _labels_.
- The _results_ of the model are called _predictions_.
- The measure of _performance_ is called the _loss_.
- The loss depends not only on the predictions, but also the correct _labels_ (also known as _targets_ or the _dependent variable_); e.g., "dog" or "cat."
- *Transfer learning*: Using a pretrained model for a task different to what it was originally trained for.
# Limitations of ML
- A model cannot be created without data (we need _labels_ for that data too)
- - A model can only learn to operate on the patterns seen in the input data used to train it.
- This learning approach only creates _predictions_, not recommended _actions_.
- Bias in data can create negative feedback loops.
## Issues
- **Overfitting is the single most important and challenging issue** when training for all machine learning practitioners, and all algorithms.
- Be careful of bias in data!

Use `doc` to solve any questions/combat issues that are seen in fastai things: `doc(learn.predict)`

# Quote Overview
> _Machine learning_ is a discipline where we define a program not by writing it entirely ourselves, but by learning from data. _Deep learning_ is a specialty within machine learning that uses _neural networks_ with multiple _layers_. _Image classification_ is a representative example (also known as _image recognition_). We start with _labeled data_; that is, a set of images where we have assigned a _label_ to each image indicating what it represents. Our goal is to produce a program, called a _model_, which, given a new image, will make an accurate _prediction_ regarding what that new image represents.

> Every model starts with a choice of _architecture_, a general template for how that kind of model works internally. The process of _training_ (or _fitting_) the model is the process of finding a set of _parameter values_ (or _weights_) that specialize that general architecture into a model that works well for our particular kind of data. In order to define how well a model does on a single prediction, we need to define a _loss function_, which determines how we score a prediction as good or bad.

> To make the training process go faster, we might start with a _pretrained model_—a model that has already been trained on someone else's data. We can then adapt it to our data by training it a bit more on our data, a process called _fine-tuning_.

> When we train a model, a key concern is to ensure that our model _generalizes_—that is, that it learns general lessons from our data which also apply to new items it will encounter, so that it can make good predictions on those items. The risk is that if we train our model badly, instead of learning general lessons it effectively memorizes what it has already seen, and then it will make poor predictions about new images. Such a failure is called _overfitting_. In order to avoid this, we always divide our data into two parts, the _training set_ and the _validation set_. We train the model by showing it only the training set and then we evaluate how well the model is doing by seeing how well it performs on items from the validation set. In this way, we check if the lessons the model learns from the training set are lessons that generalize to the validation set. In order for a person to assess how well the model is doing on the validation set overall, we define a _metric_. During the training process, when the model has seen every item in the training set, we call that an _epoch_.

> All these concepts apply to machine learning in general. That is, they apply to all sorts of schemes for defining a model by training it with data. What makes deep learning distinctive is a particular class of architectures: the architectures based on _neural networks_. In particular, tasks like image classification rely heavily on _convolutional neural networks_, which we will discuss shortly.