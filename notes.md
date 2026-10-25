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

## video 3: Loss function and programming

How to calculate loss function and how to use it to train your model. 
how the training happens = how to minimize error 

- figure out what weights minimize cost function (error)
- mean squared error performs poorly on logistic regression. it ends up with a non-convex function with many local minumum (making it difficulat to find a global minimum)

- you use **log loss function**. 
the log of 1 is always 0. Everything raised to the power of 0 is 1. 

2 separate equations: 
- log of y if y =1 
- log of y if y = 0
both negatives 

log (fw(x),y) = -y * log(fw*x) - (1-y) * log (1 - fw*x)

this equation applies to only one item, not all samples. You need to generalize to all samples. 

log (fw(x),y) = -y1 * log(fw*x1) - (1-y1) * log (1 - fw*x1)

you consider and sum all sampples in the same equation. 
understand what the sigma is about (i = 1, i < m). i is all the outputs in your dataset. 

We neeed yo fnd the optimal paramteters to minimize loss (errro) o the trianing set. then we can use the model to predict more data. 

**programming** 

You can import logisitc regression from sklearn 
penalty, defai;s is good. 
maxiter: max number of iterations to fit the model. you verify on the validation set if you are overtraining. 

outputs; model.coef_ (mx), model.incertept_ (c), model.score(x_test, y_test) score (accuract score of the model), y_pred = model.predict(X_test) predictions of y values. 

model.classes -- the classes (0,1 or ternary 0,1,2, or names)

model.predict_proba(X_test) pass x inpyuts and gives binary classification and binary probability. you wcan see how confixdetn the model is about its predictions (models tend to be overconfident!)

predict can also be useful for performance metrics when you are making decisions about hyperparameters. 

## video 4: notebook 

you can't fit a straight line in the future --> the problem of linear regression. 

added notes in the notebnook. 

# class 4

## video 1: metrics 

regression: mean squared error, r2, p-values, f-stats, aic/BIC 
classificatin=on: ROC curve, lift chart, accuracy score, F1 score, recall / precision 

**choosing a metric** -
which metric do you use to determinance the significance of preedictors? 
often it'sd a good idea to use multiple metrics instead of a single one. 

**Classification metrics** 
= how accurate predictions are to the test set --> accuracy score 

accuracy_score(y_test, x_test) --> score only 
or 
model.score(X_test, y_test) --> predictions + score 

called a harshs metric. does not tell how a classifier performs for particular classes. it just aggregates numbers. 
what if you are interested in a specific class? how is the performance for a specific number? is it over-predicting classes? 

**Prcision / Recall** is more sofisticated. 
P: how many selected were . tp / tp + fp 
R: how many correctw were found  tp  / tp + fn 

classification_report(y_test. y_predicted) 
provided P, R, F1: harmonic mean, accuracy score, by category  

Depending on the problem, Precision or Recall might be more important. And then you wanan find a tradeoff, maybe improving one at the cost of reducing the other one. 

**Accuracy revisited** 
accuracy: tp + tn / tp + fp + tn + fn 
used when true positives and true negatives are more importnat. 

**F1-score**
harmonic mean of precision and recall. Better when there are imbalances classes. it is always betweeb 0 and 1 

f1 = 2 PR / P+R 

extreme examples: 
of women who do a mammogram only 10% are called back and only 0.5% has cancer. 
my model can be 99.5% accurate AND still misdiagnose the women who have cancer. 
look at the **confusion matrix** with actual and predicted values. you can use them to see the misclassifications

How do you optmise these scores? 
In general you use the metric to optimise a mode. sometimes it is not possible. 

Our loss/cost function should reflect the problem we are solving and the training tecnique. then we hope it will create odels that do well on the dataset. 

Trade offs: 
- precision / recall often trade off against the other. 
- varying the threasong in logistic regression will impact precision and recall. 



## video 2: k-nearest neighbours 

ML model, 2 part algorightm 

1. retrieve the most similar cases 
2. comupte avergae of similar cases (regression) 
or 
2. take the max of k votes for ordinal type (classification) -- more often 

**Classification** 
Look for most similar instances to predict new cases. 

Compute distance from target to every other instance/sample in the dataset. A lot of computation. So you calcukate what are the nearest neighbors. 
Often they use Euclidian distance between all attributes of target and sample. 
Scale matters --> if one predictor has a larger value, it will influece disproportionately the result, even when that feature is not that important. 

**Formalizing everything** 
you have training set 
you have a target xj 
calculate distance between xi, xj and select the k smallest ones 
classify / approximate (regression) xj based on the k newarest xi you found 

what if the prediction is made only based on the closest training point? Like in a scatter plot --> sometimes that's deceiving
with k = 5 you look at 5 samples and can make a better guess 

You can train your model with sklearn, test and evaluate. 

**choosing k**
you can end up overfitting (if too larfe) or underfitting (it too small) the model 

any guess? cross-validation, experiment 
use k-fold cross validation (another k)

knn can create complicated boundary shapes. 

**problem of dimensionaality** 
instances descrived by 20 attrobites but only 2 are relevant to the target function --> this easily mis-leads the model 
high dimensionality increases sparsity --> the more features, the further apart. 

**morever**
- what the model does is just storing values from training data, so it can use them to predict targets (lazy model)
- storing every data is wasteful. better generalization models would not have to do it, 
- quick to train (lazy model) but prediction is slow (when it needs to compute everything)

Lazy vs easer learning methods 
how models handle construction and prediction 
- lazy defers the computration to when prediction is needed 
- eager pre-computes a model during training, making prediction faster but requiriring more memory during training. (decision trees, support vector machines, neural networks)

compare classifiers: gaussianNB vs knn
knn has worse perf. 
why? 
big values mess up knn. Look at the params: mean radius mean is 14 vs worst concavity is 0.27 --> they affect the result very differently. and whe don't even know if any / both /either is relevant. 

## video 3: feature engineering 

maximise ffeatures / deal with them 

1. feature scaling --> put them in the same order. 

build data transformation ysing make_pipeline --> it will use a standard scaler 

retrain and test data after using knn --> better score than both previous models. 

2. Tranform data 
pre-processing the dataset (it happens in the model) with a function transofrmer 
in the model with make_pipelin you pass the function transformer (instead of the scaler) and use that data to train the model .


the features have an enormous value on the model outcome. the components of each x are the features. 
a combination of understanding data + model capabilities are a hige component to success 

**using extra feature** 
you can create an extra feature on top to help the model. 
add_radius --> compututing euclidian sistance and adding that to the training data 

boundaries are smoother --> model is doing better 

**how to optimize features**
you can also combine them --> instead of having 365 daily observations, use 12 monthly averages. 


# class 5: gradient descent 

how do weights work and affect a algorithms? 
Easier to understand with linear regression 

y = mx + c 
m is the slope 
c in the intercept 

y = w0 + w1x

the linea that minimizes error (predicted value vs actual value)
what is the error? also loss or residual 

How do you select the weights to find the paramts to mimize error? 

Recap: scores like f1, accuracy, R2 are great scores but we can't optmise using them directly. 

Also, choosing the wrong metric/ error type might result in meaningfless metrics. 

formula of mean squared error (or loss)

1/2m = normalized 
sigm = polinomial, where i = 1 
distance between the y data points, to the power of 2 

there might be variations, but the idea is the distance between what is predicted and what is there. 

you can overtrain to minimize loss --> does not mean thaat the metric will. be good in the test set. 

minimizing mean squared error = 

y = w1x 

we change w until the loss is at a minimum. How do we find the minimum? 

**slopes and how they are expressed** 

if every km you drive, you go up by 500m. slope = rise / run = 500/1000

slope = y2 - y1 / x2 - x1 

in mathematics, the slope is represented with m (mountaine??)

**slope of the curve** 
that's different from a line. The slope of a curve is always changing, depending on where you are. 

there is a tanget line to the curve, which in the graphic is 0. in other parts the tangents to the curve would be much steeper 

you need a more sophisticated way to represent it, bc it changes all the time. 

there is a point in a curve that gives the **optimum** the best point where the actual and predicted values are closest --> best way to get the weight. 

how do you get that w?? 

you shart with c 0 (line intercept with y ax at 0)

you start with w low --> calculate residuals. If high, you need to increase w 

you increae 2, you get lower residuals and error. with higher w, you cann approximate the best fit for all residuals. result_ low error 

if you increase again, the error will start increasing and getting worse. 

--> the error slope is a u --> first super high, then goes down and then up again. lowest point is the optimum = best w and best error. 

Calculus is all about finding the slope of complex curves / figures. 


Note: to solve complex functions you can use derivatives 
x2 = 2x 
x3 = (3x)2

**you can calculate the slope of a curve at any value of x using the derivatives**

ghe slope of a crurve is generated by mean sqaured error. 
derivative of L with respect to weight w 

chain rule gives the derivative of mean squared error. 

this method is what you use when you have few and simple params. 
if you have a lot of params, you use **gradient descent** 

w t+5 = wt - aDl(wt)

aDL = derivative / differentiation of L with respect to w and multiple by learning rate a (how much you change params??)

Procedure: 
1. inizialize weights to something, maybe 0 
2. calculate loss function 
3. find gradient of l(w0) --with the derivaative 
4. calculate w1 = wo - aDL(w0) --> new iteration 
5. repeat the rpodcued until you reach a mimimum 

if we pick a different loss function, the idea is the same. 

Loss lansscape --> going random is not very useful. 
you can compute the gradient. 

Waves: you can see the waves and colors. How do you find the biggest wave? follow the grandiett of the wave height surface. 

**what is a slope** 
in multiple dimensions, the gradient is the vector of the slpers. out weights have multiple dimensions. 

with x and y, you know that wehen x changes of a certain amount, y changes --> you can calculate the grandient from this change. 
Dl / Dw0 --> dervative of loss / derivative of weight 0 

--> this is a partial derivative. 

what is the change if we only change w1 --> another partial derivative. 

the gradient is the direction of the greatest increase. but you wanna find the minimum. That's why you multiple by -aDL 
--> you want min gradient, not max 

grandiet is vector formed by all partial derivatives. 

sometimes you want a globala minimum and get stuck with local minimum. 

when you move from w2 to w3, you make sure everything is updated simulataneosly. 

**example with lots of weights** 

Each x has multiple feautres (x1, x2, x3, x4)

you want to find a vector for w = (w1, w2, w3, w4)

for wt+1 = wt - aDL(wt) 
you wanna calculate the partial derivatives on its own, bc weights might behave differently. 

w0 = w0 - a(DL/Dw0) 
w1 same as above 
w2 same as above 

with a scaling step you update the weights. 

wj is whatever it was before - the learning rate - the mean squared error derivative. 

**learning rate** 
another tricky hyperparmeter, you might need to iterated. 
if you look at hte curve of the lerning rate, a good learning rate goes down and stays low, although it never touches the axis. 

For logistic regression, you use log loss. Another derivative, different from that of mean squared error. But you still use grandient descent to calculate loss. 

**types of gradient descent** 

- it can vary in therms of the number of training patterns used to calculate error. 

- patterns inlcude how stable the gradient is that is used to calculate the model. 
--> calculate the loss curve using only a handful of samples vs calculate for everything. --> compromise between fidelity of error descents and computational efficienncy.

**Bathc gradient descent** --> takes into account every sample in the dataset. 
You get a sample, calculate the gradient fo the error between the prediciton and the target. 

**sthocastic gradient descent** you calculate grandient descent only on one picked sample. --> the order of dsamples in the dataset is important. It's important that you select randomly. (that why it's called sthocastic, bc sampled asre shuffled or selected randomly)

SGD has sample size = 1

**mini-batch gradient descent** 
you don't want a sample of 1 bc of noise --> could be outlier.
you take 10 sampels, calculate error across all 10, and update after each batch has been evaluated. 
you do not calculate for each observation, but for a group.

The loss can vary. it can still be bad if you pick outliers. if the batch size is sufficient, you can have a good result. 
sometimes people talk of mini-batch as SDG (not one but a small sample)

**Optmisation methods** 
a lot of techniques of SDGs. 
- SDG
-SDG with momentum
- Nesterov momentum
...
- Adam default in SKlearn 
see cheatsheet. 

*Epochs** 
number of e. is the n. of times a lesrning algo will work through the training set. 
it is comprised of 1 or more batches
it's like a for loop on the training set, and epoch is a loop throught the training set. 
within this loop there is another loop that examines the elements in the batch. 
it is commont to model error over time on the x axis (time is x, y is error) --> it gives an idea of the learning rate. 







