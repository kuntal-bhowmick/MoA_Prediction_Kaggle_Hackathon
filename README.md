# MoA_Prediction_Kaggle_Hackathon
This is a repository of codes used by me in Kaggle Competition [Mechanisms of Action (MoA) Prediction](https://www.kaggle.com/c/lish-moa)

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
I have mainly used different variants of BERT and Roberta in this competition. In BERT, I have used DistilBERT,Bert Multilingual,Bert base and Bert large where each of them had around 5 different models based on different Learning Rate,Input text length,Pseudo Labelling etc.

## Preprocessing : 
I have done minimal preprocessing in BERT and Roberta models.

## Loss function : 
I have used Focal Loss as we had imbalanced dataset in this competition.

## Callbacks : WIP 

## Ensemble : 
I have used 2 layer ensembling here. At first layer, I have created weighted average ensembling separately for Bert Base,Bert Large,Distillbert,Bert ML and Roberta.
So , if I have 5 different models of Bert Base based on different LR and Input text length then I took weighted average of those and created one blended BERT base model.Similarly, I had blended models of XLM Roberta,Bert Multilingual,Bert Large and DistilBert as well where each of them are constructed using 4-5 different model variants using weighted average.
Finally in 2nd layer, I took weighted average of all of these blended models. This 2 layer ensembling had given me better results for sure , it helped me to finish very close to Top 5% otherwise with single layer ensemble I would have been around Top 10% only.

## My Performance : 
  Private/Final Rank : 37/4373 (Top 1%)
