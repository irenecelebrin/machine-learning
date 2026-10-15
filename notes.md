# Class 1

## Intro to machine learning

What is machine learning? 

- for leveraging things computers are good at to make life easier for humans --> compute a lot of data 

- train computers to do things humans are good at but not machines 

Why using ML? 

The world is complex --> teach the computer how to understand the world with probability. 
Preferrred fields of application: 
- computer vision
- NLP 
- speech recognition
- robotics 

However, humans understand context, computers do not. 

**How does it work?**

ML uses an algorithm that can learn from data 
it created a model that with x input, outputs y 

y = f(x)

what is the function? the model learns it by gathering a lot of data and making the parameters that best fit the data. 

Once the model (algorithm) with the function is created, predictions can be made about the future. 

Why does it take so long? 
Some models take minutes to train, other hours. 
ChatGP is 8 models with 220 billions parameters in it --> a lot of time to figure out 

training is repeating the same procedure over and over again, until the paramters are the best possible. 

**Gathering data**
To train a model, you need labelled data.
example label images of cats and dogs (are these cats? Y/N, are these dogs? (Y/N)
every image is Y (cat/dog) and x is all the features of the photo (pixels) --> then you can generalize and be able based on the features if something is a cat or dog. 

Training data requires a lot of human work & correct annotation. 

**MNIST dataset**

 --> examples of human writing of numbers. 

each xi (digit) is a combination of pixels (represented by y)
Each pixel value is black/white (0 or 1)

The image is a vector: xi = R884

the exaple is *supervised learning* --> dataset is annotated 
the problem is a *classification*
given a *training set* the functions wants to map 74 pixels to a integer number. some models won't return the exaact pixel numbers but probabilities --> confidence. 

**Face detection**

classification problem --> front face, non-face, profile-face 

each face is 0, 1 or 2 --> there is no in-between. 

t1 is the set of all possible faces --> we can map/transofrm the image to a particular face. 

*stock price prediction* 

- regression: problems where t is continutos (vs distinct)

- t is stock price, x is aqll the factors like income, debt, margins... 

**users of ML** 
- medical devices --> predict diagnosis 
- ESG --> brain signals 
- surveillance
- shops (amazon)
- netflix (recommendations)
- yahoo, msft, facebook --> ads 

*examples* 
- house of cards was created based on user prefercnes --> something a lot of users might like 
- targets knew a girl was pregnantn before her father, based on her shopping choices. 
- alphago --> becomes the best chess player in the world by plagying against itself 
- artork created by AI 

* Types of machine learning* 

*supervised* or *unsupervised* 

Supervised has: 
- training data --> annotated data 
- works on classificaiton --> target is distinct value 
- regression tasks --> target is continuous value

Unsupervised: 
--> works on clustering or associations 
- there is no right answer
- algorithm tries to find patterns or structures in data 
--> principal component analysis, k-mean clustering, pagerank

- it will group things togetehr but we don't know what the groups are 
-less unsuperviselearning in this module 

**reinforced learning**
- 3rd type of ML 

Machine learning is considered 
Narrow AI --> specific task 

What do you need to do ML: 
- a specific task 
- the experience: the data --> the more, the better 
- the performance measure 
- the learning algorithm --> the recipe to improve performance, choose parameters 
- the intelligence --> the model, the network 


## Regression 

*dependent* and *independent* values 

Horizontal access represents usually independent variable --> time
vertical to represent dependent variable --> value of a hourse

**Linear relatioship** 
the change in the value of X produces a change in the value of Y 
Once we think there is a relationship between variables, we can establish which relathioship there is --> use to make predicitons for other values 

Regression is when you try to zone it on a continuous value(s) instead of predicting a class or category. 

sometimes there are alternatives to linear relationshop --> how to cook a turkey? Linear models vs Pief Panofsky 

How do you get to the linear regression equation? You need to cook  a lot of turkeys 
is this a task for supervisded or unsupervised learning? 
--> supervised: you already have the data 
--> if we assume linear model, we need the mc and c of y = mx + c 
 
*Notation* 
there is no set notation
- we use what scikit learn uses 
- paramts that can be scaled to larger models 

x = w0 + w1x

**Warning on use of linear regression** 
It is based on the assumption that data points can be represented with a line
Sometimes the relationship is not linear. 
--> use a scatter plot and look at the data distribution 

*Other regression* 
- **polynomial regression** 
- **multiple linear regression** --> multiple variables, not just 1 
- weights are still linear in both instances. It's just different how they influcence the resulting data. 

**How do you detrmine the best line?** 

You try to find the smallest error in each prediciton (predicted value vs actual value in the dataset)

the prediciton is never gonna be perfect, there will always be some error. How to do it?
Measure the difference between what the model predicts and what the values are and sum it up. 
There is a known formula for linear regression. 
but more advanced ML algorithms require more complex formulas 

A method is **gradient descent** --> fit() methos in scikit learn 

**Building a model** 

import data
create the objects (x and y)
predict more values and see how good the model is 

## Example of linear regression 

Documentation on linear regression on scikit learn

https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html 

start from the examples --> set it up on a Jupiter notebook. 


To do: 
- import libraries and matplotlib 
- import data 
- plot the data --> scatter plot 
- find the correlation coefficient np.corrcoef()
- make sure x is a 2-dimenstional vector --> x-shpae and y.shape are 1 
more often than not, for each x value you will actually have an array of values, not just one value. 

-- reshape the array --> from 1 dimension to 2 --> from row to column 

- Build the model: import linear regression from scikit learn. use defulat values 
- fit the model --> provide x (2d vector) and y (1d vector),. If you put the original shape, you get an error 

model.coef --> coefficient 
model.intercept --> the slope

you can build the model by hand: w0 + np.dot(w1,x).reshape(-1,1)

== same as prod = model.predict(x) 

- Evaluation, calculate mean square error and r2 score 

- visualize the mode with a line plot on top of you scatter plot 

**Multiple linear regression** 

Diabetes dataset 
There are multiple features you need to make a prediction

-import dataset 
-print description --> multiple categories 
-read in pantas and do a boxplot 

- normalize the dataset --> to uniform them and and make it easier to plot. 

- x is the data 
- y is diabetes target 
- fit the data and look at the scores or error and r2 
- look at the coefficient --> some are small and others are large 
--> small coefficient --> it's not a good prediction variable 
--> the big ones are more likely to be contributors 
--> often removing the small variables make the model better and more accurate 
--> use pandas to clean up columsn and refit data 


# Class 2 

## Generalization 

Ultimate goal for machine learning 
Model's ability to give good outputs on inputs never seen before. 

Overfitting 
if you test the model on data usede to train it --> overfitting 
you need a test set 

Underfitting 
the model does not perform well --> the model  or the algorithm are not complex enough, training mechanisms are poor 

**How to build**: 
- aquire dataset 
- decide which model to use 
- train the data --> choose the parameters to tweat == the polynomial 
- test the model 

- almost always, the more the datapoints, the better. 

Building a model
- start with x (a matrix)
- y is the set of corresponding variables 
- a particular y is the result for a particular x 

Underfitting --> result of high bias,low variance --> assumption on how the data looks like, result is low variance = model is not very sensitive 

Overfittitng --> low bias, the model is very sensitivie to the training data == high variance 

All is about a tradeoff bewteen variance - bias 
What is the right measure? 
Depending on the model, something in the middle. --> ML is all about making a model able of generarilazion without ending in either of the 2. 
Detecting wether the model suffers from either of this is responsability of the model 

Overfitting: the major problem is overconfidence. 
Underfitting: high bias brings lower confidence 

**How to test a model**

Split the data you have in training and testing sets. 
Test set is always separate from the training set. 
80/20 or 75/25
- randomly select which elements are in the training / test set. 
- shuffle the data too, before slinging the test set 

fit the model on the training set 
evaluate on the test set 

use train_test_split 

*About the test set* 
- use the test set carefully, only for final evaluation 
- do not use in selecting hyperparameters for the training 
- you need a representative sample of cases: ordinary, edge cases... 

**how do you know if model is overfit / underfit**

- compare training score and test score 
--> if trainign score is low, model is underfit 
--> if trainining score is high and test score is very low, model is overfit

--for underfitting: train for longer, use a more complex model 
-- for overfitting: make the model simpler,get more data, use regularization (neural networks)

**how to decide the complexity of a model**
- start with simple models, so you can try different 
- don't just pick the one that gives highest score, bc that can be wrong 
- you need a mechanism to tets yout model. Use the test set? No, you would expose it to the model! 
- use Hypher paramter tuning --> but do not use the test set. Use a third set of data. 

**Hyperparameters** 

They are chosen rather than learned. 
- the degree of your mdoel (linear, quadratic, n-degree polynomial), which features to use in your model 
- the learning rate alfa
- the amount of regularization 
- the number of layers / neurons in a neural network 

**Polynomial curve fitting** 
What is f(x) 
- try polynomial degrees of M with weights --> is the line gonna be linear, cubic, quadratic... weights = coefficients, mx + c 
- this is the hypthosis space 
- w is vector 

How do we measure success? 
- measure of squared error
- rms (root mean squared error)

Among functions, chosose degree whcih minimizes error 
- the degree of a polynomial is a hyperparameters
- we need the degree that captures the trend of data best 

**Which degree of polynomial** 
with a polynomial 0 you get a straight line, bad 
with a quadratic polynomial, the line is diagonal, still not good
with a cubic polynomial, the line is pretty close to the trend 
with a 9-polynomial, the model predicts the value perfectly, too well! it would not be able to generalize. Overfitting

**RMS error**
if you look at rms of all models, they show consistent performance across models except the one with 9degree polynomial --> overfitting with training data performing super well and test set performing super bad 

**Selecting hyperparameters** 
There are a lot of methods 
- use feedback from **validation set** 

**Validation set** 
- split training data in training set and validation set (70/30)
- train different models on the trainign set 
- iterate through all the possible hyperparameters (eg polynomial m=1, m=2...)
    - fix the hyperparameter, start with m=1
    - train
    - validate with validation set 
    - store result of the hyperparameter
    - repeat from step 1 with the next hyperparameters 
- choose the model with the minimum error on the validation set 
- (optional) retrain the model on the complete training data (training and validation set)

**
Hyperparameters are not trained, we choose them. 
validation does not see the data directly, but it is still compromised. 
It does not give an idea of the overall model performance, that's why you still need a test set. 

**cross validation** 
the validation set can introduce bias, if the validation set is not reprensentative (for example samples are not shuffled) 
If you don't have enough data to have a validation set, you can do cross validation randomly generating the validation set each time and doing a number of runs. The select average of scores and select the model with the lowest error is these averages 

It is slow, if you have a big model with a lot of paramteters 

Types of cross-validation: 
- leave out one cross va,udation 
- k-fold 
-. 

k-fold: 
you split the dataset inot k foldes 
see slide 

## Notebook 

try with the cars dataset to use individual variables to train a model --> bad scores 

if you use 2 variables instead of 1, better scores --> see model 4 in the ntoebook 

Something not to do: 
use the score of the test set to tweak the features of your model. 

Use a validation set as middle step. --> use a cross validation score. 

--> 5 numbers in the output bc of 5 slices 
--> look at the avg of all scores to get your final score 

use 3 features. 

train the model 
use validation score from the training data 
--> once you are happy with the numbers, you go back and use those params to train the model 

**polynomial regression**

with a single feature. 

use scikit-learn. USe polynomial features to transofr the data to use it to train the model. 
x will be expaned to x, x2 etc. 
then you fit the coefficitents in the polynomial. 

the numbers need to be in a 2d array --> do a reshape. that will be your x. 

first yout train with the polynomialfeatues expanding to the power of 2 (althought the data goes up to 5) 

print scores for train data and test set. 
train performs well, test is a bit lower. 
explore what is the best hyperparamter to work better 
change polynomial to 1, 2, 3, 4, 5 (up to the max) to see which one works best. --> for loop to expand data, train the model, get the scores, and compare them. 
The best way to compare results is plotting a plot with the performance scores (skip 0 bc it's just gonna be a straight line) in test and training 

the best is actuallt with the ploynomial 1 --> with the others training improves and test gets worse. 

simple linear regression works the best 

--> AGAIN we used the test set to choose the hyperparatmers. Bad. you need to use a validation score dfor that. Otherwise in this case the test set is already compromised. 

# Class 3: Classification

## video 1 
outputs are not continuous but classes. 

Evaluating performance --> only on the test set 

Binary classification --> easiest form of classification 
Some models can address multi-class 

## video 2: logistic regression 

It only outputs a value that is between 0 and 1 
It's a classification model. The predicted value is a probability of something being true / false 

0.7 is 70% probability of success --> you need to decide a treshold. 

the equation y = w0 + w1x is likely to be < 0 and > 1 (the line / slope is long)
we want an estimation of p between 0 and 1. probability < 0 is impossibility, and > 1 just does not exist. 

Linear regression does not really work for logistic regression. The line is snot representative. 

s-shaped curve is better, it's a bit different then the formula y = c+ mx. The sigmoid curve is gonna be close to 1 or 0 forever bt never touching. 

**Sigmoid function** or **logisitic function** takes any real value number and maps to 0-1. 
It is used for neural networks and deep learning. 
How do we relate the linear regression function to the sigmoid curve? 

At the end of the day, a line is not the best way to show classification results. 
You need to pick a boundary / treshold and adjust FP/FN to that. 









