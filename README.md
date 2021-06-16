# Optimizing an ML Pipeline in Azure

## Overview
This project is part of the Udacity Azure ML Nanodegree.
In this project, we build and optimize an Azure ML pipeline using the Python SDK and a provided Scikit-learn model.
This model is then compared to an Azure AutoML run.

## Summary
We use a bank marketing dataset containing selected features related to a Portuguese retail bank's telemarketing campaings
(telemarketing attributes, product details, client information) enriched with social and economic influence features. We seek to 
**predict the success of telemarketing calls** for selling bank long-term deposits.

**In 1-2 sentences, explain the solution: e.g. "The best performing model was a ..."**

## Scikit-learn Pipeline
**Explain the pipeline architecture, including data, hyperparameter tuning, and classification algorithm.**

**What are the benefits of the parameter sampler you chose?**

**What are the benefits of the early stopping policy you chose?**

## AutoML
**In 1-2 sentences, describe the model and hyperparameters generated by AutoML.**

## Pipeline comparison
**Compare the two models and their performance. What are the differences in accuracy? In architecture? If there was a difference, why do you think there was one?**

## Future work
**What are some areas of improvement for future experiments? Why might these improvements help the model?**

`FixMe`: Data leakeage and purpose of ML solution: planning campaing versus continuous support during a campaign?

## Proof of cluster clean up
**If you did not delete your compute cluster in the code, please complete this section. Otherwise, delete this section.**
**Image of cluster marked for deletion**

## References
+ [Bank Marketing Data Set](https://archive.ics.uci.edu/ml/datasets/Bank+Marketing)
+ [\[Moro et al., 2014\]](https://core.ac.uk/download/pdf/55631291.pdf) S. Moro, P. Cortez and P. Rita. A Data-Driven Approach to Predict the Success of Bank Telemarketing. Decision Support Systems, Elsevier, 62:22-31, June 2014 (preprint dated 2014-02-19)
