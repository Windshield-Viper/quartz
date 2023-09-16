[Getting started with NLP for absolute beginners](https://www.kaggle.com/code/jhoward/getting-started-with-nlp-for-absolute-beginners)
[Book chapter](https://github.com/fastai/fastbook/blob/master/10_nlp.ipynb)
Deep learning can be used on natural language datasets with great results. 
- Training a language model uses **self-supervised learning** – using data that doesn’t need to be explicitly labeled.
- To get best results, it’s often important to fine-train the language model as well as the classification model on the type of text you want to analyze (this is the [ULMFit approach](https://arxiv.org/abs/1801.06146))
	- For example, to train a movie review classifier, you could use this process:![[Other/Images, Other Attachments/Pasted image 20230916142813.png|400]]
## Steps to creating a language model:
- Tokenization:: Convert the text into a list of words (or characters, or substrings, depending on the granularity of your model)
- Numericalization:: Make a list of all of the unique words that appear (the vocab), and convert each word into a number, by looking up its index in the vocab
- Language model data loader creation:: fastai provides an `LMDataLoader` class which automatically handles creating a dependent variable that is offset from the independent variable by one token. It also handles some important details, such as how to shuffle the training data in such a way that the dependent and independent variables maintain their structure as required
- Language model creation:: We need a special kind of model that does something we haven't seen before: handles input lists which could be arbitrarily big or small. There are a number of ways to do this; in this chapter we will be using a _recurrent neural network_ (RNN). 
## More on tokenization
- Because language can have many different ideas about what a “word” is, there are multiple approaches to tokenization.
	- It can be word-based, splitting on spaces
	- It can be subword based
	- Or it could be character based
- 