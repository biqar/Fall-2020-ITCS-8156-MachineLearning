# Assignment #2 - Classification

<font color="red"> <b> Due: Oct 23 (Friday) 11:00 pm </b> </font>

<font color="blue"> type your name here </font>

## I. Introduction

Describe the objective of this assignment. You can briefly state how you accompilsh it.

## II. Data

Introduce your data and visualize them. Describe your observations about the data.
You can reuse the data that you examined in Assignment #0 (of course for classification). 

## III. Method

Summarize the pocket algorithm, discriminant analysis, and logistic regression.
The superclass *Classifier* defines common utility methods. 
Finish the normalize function for you. 
Do not forget explain your implementation. 

The explanation of your codes should not be the comments in a code cell. 
This section should include
 - review of the 4 classification models 
 - your implementation and description


### A. Super Classs Definition

We first define the super class for classification algorithms. You only need to complete the normalize() method. You don't need to modify anything else. 
```
import numpy as np
from abc import ABC, abstractmethod

# Super class for machine learning models 

class BaseModel(ABC):
    """ Super class for ITCS Machine Learning Class"""
    
    @abstractmethod
    def train(self, X, T):
        pass

    @abstractmethod
    def use(self, X):
        pass

    

class Classifier(BaseModel):
    """
        Abstract class for classification 
        
        Attributes
        ==========
        meanX       ndarray
                    mean of inputs (from standardization)
        stdX        ndarray
                    standard deviation of inputs (standardization)
    """

    def __init__(self, ):
        self.meanX = None
        self.stdX = None

    def normalize(self, X):
        """ standardize the input X """
        
        if not isinstance(X, np.ndarray):
            X = np.asanyarray(X)

        self.meanX = np.mean(X, 0)
        self.stdX = np.std(X, 0)

        # TODO: Finish this normalization
        Xs = 
        return Xs

    def _check_matrix(self, mat, name):
        if len(mat.shape) != 2:
            raise ValueError(''.join(["Wrong matrix ", name]))
        
    # add a basis
    def add_ones(self, X):
        """
            add a column basis to X input matrix
        """
        self._check_matrix(X, 'X')
        return np.hstack((np.ones((X.shape[0], 1)), X))

    ####################################################
    #### abstract funcitons ############################
    @abstractmethod
    def train(self, X, T):
        pass
    
    @abstractmethod
    def use(self, X):
        pass 
```

For the rest of implementation, inherit the class and make your own Pocket, QDA, LDA, and LogisticRegress classes. Each following subsection will have toy tests as we did in the note before applying to your data.

### B. Pocket Algorithm
todo: add pocket algorithm implementation here

### C. QDA
todo: add QDA algorithm implementation here

### D. LDA
todo: add LDA algorithm implementation here

### E. Logistic Regression
todo: add Logistic Regression algorithm implementation here

## IV. Experiments
Apply the classfiers on the data and discuss the results.
Please describe your codes for experiments. You may have subsections of results and discussions here.
Here follows the list that you consider to include:
- the classification results
- plots of classification results 
- model comparision 
- choice of evaluation metrics
- **Must partition data into training and testing**

## Conclusions

- Summarize your work here. 
- Which classifier do you think the best? 
- Discuss the challenges or somethat that you learned. 
- If you have any suggestion about the assignment, you can write about it. 

## References

List all your references here.

## Extra Credit

* [OPT 1] Search for a ordinal data set and apply your classifiers to it. 
  - Repeat the experiments on it. 
  - Do you have different observation from previous results? 
  - Were you able to observe that we discussed in class about logistic regression? 
  - For a full extra credit point, you need to discuss all bullet points in Results section.     


* [OPT 2] Partition your data into five sets. Selecting one test set and the other for training, repeat your experiments and observe/analyze the 5 different training/testing errors.  

## Grading

DO NOT forget to submit your data! Your notebook is supposed to run well after running your codes.

To help our TA's grading, please make an explicit section for each grading criteria. 

** Note: this is a WRITING assignment. Proper writing is REQUIRED. Comments are not considered as writing. ** 

points | | description
--|--|:--
5 | Overview| states the objective and the appraoch 
15 | Data | 
\- | 5 | description 
\- | 5 | plots for understanding or analysis 
\- | 5 | preliminary observation 
25 | Methods | 
\- | 10 | Summary of Classification models
\- | 5 | Explanation of codes
\- | 10 | Pocket, LDA, QDA, Logistic Regression
40 | Experiments 
\- | 5 | Discussion about evaluation metrics
\- | 5 | Discussion about train and test accuracies
\- | 20 | plots for results (5 for each algorithm)
\- | 10 | Discussions about classificaion model comparison
5 | Conclusions |
5 | Referemces |
5 | Grammar and spelling error (Proofread please) |
