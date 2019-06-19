---
layout: post
title:  "10 Ways to Quickly Test For Data Engineering Skills"
date:   2019-06-18 19:57:43 -0400
categories: recruiting data science dataengineer
---

## So ... Data Science Is Hot ...

Data science is inside of a hype cycle right now. What may not be a commonly known is that data science is not just about the algorithm. Often times, machine learning is surrounded by a massive infrastructure. According to Nick Handel's talk about creating machine learning infrastructure at an early stage, models need the following parts to work:

1. Connections to data sources
2. Validation of raw and transformed data
3. Feature collection and extraction for multiple data sets
4. Backfill historical features to test new ideas
5. A means to serve models
6. A means to monitor models live

And for online learning [Hakon Hapnes Strand's](https://www.quora.com/How-do-you-take-a-machine-learning-model-to-production) post on quora goes into depth with that. 



Those 6 tasks are the main roles of a data engineer. They prep, collect & move data. They also monitor and deploy models for the data scientist.

While it's reasonable to look directly for certain creditials, you'll want to know what you're getting into. It's somewhat difficult to test 100% of those skills immediately in a 1 day hackathon-like setting. This post aims to at least point recruiters into the right direction for what to see in a single day.


## Here Are 10 Ideas to Test For a Data Engineering Position:


### 1. Get Them to Deploy the Iris Model Into Production Using a Micro Service


Here, you want to test for minimal machine learning understanding, and figure out if your potential recruit has the capacity to deploy the models your data scientist create. Taking the iris data set, analyzing and making predictions, then having the engineer create a micro service to access the model at all times would be ideal. Here are some steps you'd like to look out for.


#### Importing the important stuff
```py
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd
from sklearn import tree
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score
from sklearn.externals import joblib
from sklearn.model_selection import train_test_split
```

#### Loading the data set
```py
iris = sns.load_dataset("iris")
print(iris.head())
```

```py
y = iris.species
X = iris.drop('species',axis=1)
```


```py

X_train, X_test, y_train, y_test = train_test_split(X, y, 
                                                    test_size=0.3, 
                                                    random_state=100, 
                                                    stratify=y)
clf = tree.DecisionTreeClassifier()
clf.fit(X_train,y_train)
```

```py
from sklearn.datasets import load_iris
iris=load_iris()
tree.export_graphviz(clf,
out_file='iris.dot',  feature_names=iris.feature_names,  
                         class_names=iris.target_names,  
                         filled=True, rounded=True,  
                         special_characters=True)
```


```py
print ('Accuracy Score');
print (accuracy_score(y_test, y_pred)* 100);

#Accuracy Score
#95.5555555556
```


After that's complete, they need to actually deploy the model for production. There's a single major option for doing that, picklization of the models and accessing them behind a parallel server. We can use the BentoML system to make this work.


An example of them deploying a model is below:


#### Defining the BentoML model
```py
import pandas as pd
import bentoml
from bentoml.artifact import PickleArtifact
from bentoml.handlers import DataframeHandler

@bentoml.artifacts([PickleArtifact('iris_lr')])
@bentoml.env(conda_dependencies=["scikit-learn", "pandas"])
class IrisModel(bentoml.BentoService):

    @bentoml.api(DataframeHandler, typ='series')
    def predict(self, series):
        """
        predict expects pandas.Series as input
        """        
        return self.artifacts.iris_lr.predict(series)
```


```py
from iris_lr import IrisModel

# Initialize bentoML model with artifacts

bento_model = IrisModel.pack(
    iris_lr=clf
)

# Save bentoML model to directory
saved_path = bento_model.save("/tmp/bento")

# print the directory containing exported model archive (prefixed with model name and version)
print(saved_path)
```


#### Loading and Using A Model
```py
import bentoml

# Load exported bentoML model archive from path
bento_model = bentoml.load(saved_path)

# Call predict on the restored sklearn model
bento_model.predict(iris)
```

#### Copy the model into another folder
```py
import shutil
shutil.rmtree('./model', ignore_errors=True)
shutil.copytree(saved_path, './model')
```



#### Create a docker build of the model

```bash
docker build -t iris-lr-model .
```

```bash
docker run -p 5000:5000 iris-lr-model
```

It's now possible to use the model as a micro service. 

```bash
curl -i \
--header "Content-Type: application/json" \
--request POST \
--data '["some new text, sweet noodles", "happy time", "sad day"]' \
localhost:5000/predict
```

### 2. Parallelize Feature Extraction and Preparation in the Best Ways Possible

Give them options to parallelize feature extraction for any particular dataset. If they're able to profile it to prepare the features as quickly as possible, you'll be able to know:

1. That they know how to consider profiling the applicaiton
2. That they can think of ways to make apps faster.

### 3. Go through A Set of Tutorials Using Google CoLab

Colab allows users to run complex training jobs from their laptop. Following a tutorial of using Google Co-Lab to run a complex model will allow the user to 

Follow the tutorial [here](https://colab.research.google.com/github/bentoml/BentoML/blob/master/examples/tf-keras-text-classification/tf-keras-text-classification.ipynb)

### 4. Get Them to Create a Quick Library for a Common Task

One of the major tasks for data engineers. Generally there will be some tasks that the data scientist will need to run repeatedly. If the data engineer is able to create common systems and proceedures, that gives you some inference of what they're capable of doing.


### 5. Take OpenAI's GPT-2 Model and Push that to Production

Take the first point, and copy the process for OpenAI's GPT-2 model. Have them create a service that would allow them to run containerized versions of the GPT-2 model so that it can be used for essentially everything.

### 6. Use A Deployed GPT-2 Model to Determine A Task

By copying Siraj Raval's tutorial on how to build an education start-up, you'll see that he was able to take the simple GPT-2 model to determine if a person was plagurizing their work.

### 7. Test To See How Flexibly They'll Try New Solutions (introduce to new libraries)

Introduce dask as an alternative to Spark. See if they can use it. The idea here is that you're looking to see if the employee is able to quickly adapt to new circumstances. Dask is not necessarily difficult to pick-up. 

### 8. Create a Simple Metastore for Files Using MongoDB

This is an extension to point 4. Using mongodb, create a simple class/library that will allow people to store files in a data lake or storage space (such as s3) and use know where relavant files are. This mimics a lot of functionality of Hadoop, yet would be good for small start-ups that don't want to handle the overhead that hadoop has in regards to devops. 

### 9. Try Deploying and Using An Online Learning Algorithm

Generate fake data, using `make_classification` and `make_regression`, then have them perform an incremental regression on that fake data. This can be one of the goals of the hackathon challenge.

### 10. Have Them Use Dask and Kubernetes to See If They Can Handle Massive Features

Generate fake data, using `make_classification` and `make_regression`, then have them perform an incremental regression on that fake data. Creating 10 million rows with 25 features, then having SGDClassifer run with that information will allow you to see if they can run an online algorithm appropiately at a large scale.


This is doable with `Dask-ML`. It's a spark-like adapter for all Sklearn machine learning algorithms.

**Example Of Dask-ML:**
```py
from sklearn.ensemble import GradientBoostingClassifier
import sklearn.datasets
import dask_ml.datasets
from dask_ml.wrappers import ParallelPostFit

X, y = sklearn.datasets.make_classification(n_samples=1000,
                                            random_state=0)


clf = ParallelPostFit(estimator=GradientBoostingClassifier())
clf.fit(X, y)

X_big, _ = dask_ml.datasets.make_classification(n_samples=100000,
                                                chunks=10000,
                                                random_state=0)
clf.predict(X_big)


clf.predict_proba(X_big).compute()[:10]
```



BONUS:

Get your candidate to log information about a model to an external interface, then check on the status for a bit.