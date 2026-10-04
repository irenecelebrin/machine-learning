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



