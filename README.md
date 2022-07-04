# Classification-of-Iris-flowers
Our goal is to classify and predict iris flower species from flower measurements using Linear Discriminant Analysis.
Description of the dataset
Type: Multiclass classification.
Dimensions: 150 instances, 5 attributes.
Inputs: Numeric.
Output: Categorical, 3 class labels.
UCI Machine Learning Repository: https://archive.ics.uci.edu/ml/datasets/Iris

R programming will be used for explorative analysis, modeling, prediction and computing the accuracy of prediction of the chosen final model.
Step 1: Data preparation 

•	Loading Packages in to R

Install.packages (“caret”)
Library(caret)
filename<-"C:/Users/indupravs/Downloads/Data Science Projects/IRIS/iris.data"
dataset<-read.csv(filename, header=FALSE)
colnames(dataset)<-c("Sepal.Length","Sepal.Width","Petal.Length","Petal.Width","Species")
colnames(dataset)

We will split the loaded dataset into two, 80% of which we will use to train our models and 20% that we will hold back as a validation dataset.

# Create a list of 80% of the rows in the original dataset we can use for training
validationIndex <- createDataPartition(dataset$Species, p=0.80, list=FALSE)
# Select 20% of the data for validation
validation <- dataset[-validationIndex,]
# Use the remaining 80% of data to training and testing the models
dataset <- dataset[validationIndex,]

Data Exploration and Descriptive Statistics

# dimensions of dataset
dim(dataset)
# list types for each attribute
sapply(dataset, class)
# take a peek at the first 5 rows of the data
head(dataset)
# list the levels for the class
levels(dataset$Species)
# summarize the class distribution
percentage <- prop.table(table(dataset$Species)) * 100
cbind(freq=table(dataset$Species), percentage=percentage)
# summarize attribute distributions
summary(dataset)			
