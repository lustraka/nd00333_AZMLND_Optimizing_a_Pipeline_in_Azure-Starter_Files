# Optimizing an ML Pipeline in Azure

## Overview
This project is part of the Udacity Azure ML Nanodegree.
In this project, we build and optimize an Azure ML pipeline using the Python SDK and a provided Scikit-learn model.
This model is then compared to an Azure AutoML run.

## Summary
We use a bank marketing dataset containing selected features related to a Portuguese retail bank's telemarketing campaings
(telemarketing attributes, product details, client information) enriched with social and economic influence features. We seek to 
**predict the success of telemarketing calls** for selling bank long-term deposits.

The standard Scikit-learn Logistic Regression model (LR) reached accuracy 0.898, which was higher then accuracy of the AutoML (0.739), as its hyperparameters was optimized for accuracy. On the other side, the AutoML showed AUC 0.737, which is higher then AUC of the LR model (0.583). Because AUC is more relevant metrics for classification tasks, we can conclude, that the best performing model was provided by the AutoML.

![Model Metrics (click to see the image)](img/AML-Results?raw=true)

Figure 1: Accuracy and AUC of two models

## Scikit-learn Pipeline
**Explain the pipeline architecture, including data, hyperparameter tuning, and classification algorithm.**
![HyperDrive Accuracy (click to see the image)](img/AML-HyperDrive-Acuracy-2.png?raw=true)

Figure x: HyperDrive optimizing for accuracy

![LR ROC Curve (click to see the image)](img/AML-ROC-LR.png?raw=true)

Figure x: ROC curve of the Logistic Regression

**What are the benefits of the parameter sampler you chose?**
**What are the benefits of the early stopping policy you chose?**

We used the random hyperparameter sampler, because it supports discrete and continuous hyperparameters and early termination of low-performance runs, which was enabled by the bandit policy. Benefit of both these design decisions is lower costs of the experiments.

## AutoML
**In 1-2 sentences, describe the model and hyperparameters generated by AutoML.**
![Voting Ensamble Clfs (click to see the image)](img/AML-VE-clfs.png?raw=true)
Figure x: Classifiers and their weights in the Voting Ensamble

![ROC of Voting Ensamble Clfs (click to see the image)](img/AML-VE-clfs-ROC.png?raw=true)

Figure x: ROC curves of the Voting Ensamble

![AutoML-ROC (click to see the image)](img/AML-AutoML-ROC.png?raw=true)

Figure x: AutoML ROC

## Pipeline comparison

![Pipeline Architecture](http://www.plantuml.com/plantuml/png/NP3FoXD14CJl_HHzZ1SH3nvsGuWQmOE2g0TlePDKrd7dpz3J4rZ8mpl9VlbOSgtvLNNLR8k9MWsUkayIH_uDZo0wmbmSU2SczFuT7vEl8POrTJju6FZ3GwAL9SwA2wBngU7i8QCCO8adhj75Sz8WvYvW5tErygQdxeSYY-9keBNRc8gBRmVO_iz-MZMYcKRglauPkjERDxiCxoAkLB9tHjslZACxJzHo9C2WL2Ha3-rdWcLecQySGzHFL2pbt9PHJjuTfoVsSufdDrG5tGlTk7_fq1FQb3kuG7XHJcliswLw2CwUz7dAuy37QkdxjyMOHTxBsp9heSqbvc_vSX5V3QmerLlPKFSJWoi6PViB3ka4VwLjCzJW_mC0)

Figure x: Pipeline architecture

**Compare the two models and their performance. What are the differences in accuracy? In architecture? If there was a difference, why do you think there was one?**

## Future work
**What are some areas of improvement for future experiments? Why might these improvements help the model?**

`FixMe`: Data leakeage and purpose of ML solution: planning campaing versus continuous support during a campaign?
`FixMe`: After using random hyperparameter sampling in the initial search, we can then refine the search space with the grid or Bayesian sampling to improve results.

## Wrap up
The compute cluster deleted using SDK (see [udacity-project.ipynb](https://github.com/lustraka/nd00333_AZMLND_Optimizing_a_Pipeline_in_Azure-Starter_Files/blob/master/udacity-project.ipynb). The compute instance deleted using Azure ML Studio GUI. The VM disconnected.

## References
+ [Bank Marketing Data Set](https://archive.ics.uci.edu/ml/datasets/Bank+Marketing)
+ [\[Moro et al., 2014\]](https://core.ac.uk/download/pdf/55631291.pdf) S. Moro, P. Cortez and P. Rita. A Data-Driven Approach to Predict the Success of Bank Telemarketing. Decision Support Systems, Elsevier, 62:22-31, June 2014 (preprint dated 2014-02-19)
+ [Train scikit-learn models at scale with Azure Machine Learning](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-train-scikit-learn?view=azure-ml-py)



<!--
![(click to see the image)](img/?raw=true)

@startuml
:Connect to Bank Telemarketing Data
20 columns<
:Delete 6 columns
(to prevent data leakage and uninformative inputs);
:Prepare data
<i>train.get_X_y()</i>;
fork
:HyperDrive pipeline|
split
:Specify
parameter
sampler;
split again
:Specify early
stopping
policy;
split again
:Configure
training
job;
end split
:Configure HyperDrive run;
:Submit HyperDrive run;
fork again
:AutoML pipeline|
:Configure AutoML run;
:Submit AutoML run;
end fork
:Evalute results>
:Register the model|
@enduml
-->
