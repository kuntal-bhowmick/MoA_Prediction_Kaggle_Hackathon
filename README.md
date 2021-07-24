# MoA_Prediction_Kaggle_Hackathon
This is a repository of codes I have used in Kaggle Competition [Mechanisms of Action (MoA) Prediction](https://www.kaggle.com/c/lish-moa)

## Competition Overview :
What is the Mechanism of Action (MoA) of a drug? And why is it important?

In the past, scientists derived drugs from natural products or were inspired by traditional remedies. Very common drugs, such as paracetamol, known in the US as acetaminophen, were put into clinical use decades before the biological mechanisms driving their pharmacological activities were understood. Today, with the advent of more powerful technologies, drug discovery has changed from the serendipitous approaches of the past to a more targeted model based on an understanding of the underlying biological mechanism of a disease. In this new framework, scientists seek to identify a protein target associated with a disease and develop a molecule that can modulate that protein target. As a shorthand to describe the biological activity of a given molecule, scientists assign a label referred to as mechanism-of-action or MoA for short.

How do we determine the MoAs of a new drug?

One approach is to treat a sample of human cells with the drug and then analyze the cellular responses with algorithms that search for similarity to known patterns in large genomic databases, such as libraries of gene expression or cell viability patterns of drugs with known MoAs.

In this competition, you will have access to a unique dataset that combines gene expression and cell viability data. The data is based on a new technology that measures simultaneously (within the same samples) human cells’ responses to drugs in a pool of 100 different cell types (thus solving the problem of identifying ex-ante, which cell types are better suited for a given drug). In addition, you will have access to MoA annotations for more than 5,000 drugs in this dataset.

As is customary, the dataset has been split into testing and training subsets. Hence, your task is to use the training dataset to develop an algorithm that automatically labels each case in the test set as one or more MoA classes. Note that since drugs can have multiple MoA annotations, the task is formally a multi-label classification problem.

How to evaluate the accuracy of a solution?

Based on the MoA annotations, the accuracy of solutions will be evaluated on the average value of the logarithmic loss function applied to each drug-MoA annotation pair.

## My Solution Description :
Different variant of Deep Learning Neural Networks and TabNet have been main models I have used in this competition.

### Preprocessing : 
I have used a bunch of Feature Selection and Feature Engineering steps in this competition.
#### Feature Selection:
I have used PCA,VarianceThreshold and KMeans for Feature Selection purpose.
##### PCA : 
I have used different variants of PCA based on different n_components value in different models and some these models provided decent improvement in ensembling.
I have applied PCA separately on Gene varaible and Cell variable and then combined both of them to create the final dataset.
#### Normalization:
I have used QuantileTransformer to change the data distribution and get as much normal distribution as possible.

### Models :
#### 1. TabNetRegressor :
#### 2. DeepLearning : 
I have created a DL model consisting of 3 layers where each of these layers are made of DropOut, BatchNorm and WeightNorm with couple of dense layers.

### Loss function : 
I have used Log Loss as the loss function in this competition.

### Callbacks : WIP 

### Ensemble : 
I have used 2 layer ensembling here. At first layer, I have created weighted average ensembling separately for NNs and TabeNet.
So , if I have 3-4 different models of NNs based on different LR and different number of components used in PCA then I took weighted average of those and created one blended Neural Network model.Similarly, I had blended models of TabNet as well where each of them are constructed using 4-5 different model variants using weighted average.

### My Performance : 
  Private/Final Rank : 37/4373 (Top 1%)
