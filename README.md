# SAS-Project-Unbalanced-Classes




<br />
<p align="center">
  <a href="#">
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/10/SAS_logo_horiz.svg/1280px-SAS_logo_horiz.svg.png" alt="Logo" height="80">
  </a>

  <h3 align="center">SAS Project</h3>
  <h3 align="center">Unbalanced Classes</h3>
  <h3 align="center">HSE 2021</h3>
  

  <p align="center">
    Prepared by <br />
   <b align="center"> Zobov Vladimir, 
    Karzanov Daniil, 
    Molostvov Pavel </b>
  
  <br />
  Supervisor: <b>Maria Vorobyova </b><br />

  </p>
</p>



main.ipynb notebook contains the python implementation of the following items:
* Data analysis  
For us, the most important thing is to minimize the number of real defaults that were classified as non-default, that is, after the selection of clients by the model, the bank would receive as few clients who would not be able to repay the loan, as possible. However, it is also important that the number of issued loans does not decrease significantly after the model has been run. That is why we will use two metrics to assess the model's performance: FOR (False Omission Rate) will show how many clients, of which the model offered to issue a loan, will be defaulters and FPR (False Positive Rate) will show how many of all non-defaulters were denied a loan by the model. By minimizing both metrics we will achieve the best model. 

* Feature engineering  
There are a few methods to deal with imbalanced target. We will try some under and over-sampling techniques as well as special models that rebalance the target while fitting. Also, we will try simply to increase the threshold, oftentimes it is sufficient to have really good results. 

* Undersampling  
Undersampling is a group of techniques that consists of reducing the data by eliminating examples belonging to the majority class with the objective of equalizing the number of examples of each class.

* * Random undersampling
* * Tomek link
* * InstanceHardnessThreshold
* * NeighbourhoodCleaningRule
* Oversampling  
Oversampling is the set of techniques that are based on duplicating examples from the minority class and adding them to the training dataset.
* * Random oversampling 
* * Smote
* * Adasyn
* Models that rebalance target while fitting  
Models that rebalance target while fitting is methods generating under-sampled or over-sampled subsets combined inside an ensemble.
* * EasyEnsembleClassifier
* * RUSBoostClassifier
* * BalancedBaggingClassifier
* * BalancedRandomForestClassifier
* Model evaluation and model selection  
![image](https://user-images.githubusercontent.com/49778314/121660273-cd72c000-caab-11eb-9a7e-c67b10779ab5.png)
We can see that there are 5 models that perform better than others: No resampling, Easy Ensemble, Balanced Random Forest, Random Underdampling, Random Oversampling. Now we will test them in terms of the best profit that they can give us. We will assume that the average debt on the credit card is the same for clients who default and not default. Also, we will assume that in case of default we lose all the money that the client paid from his credit card and we will use an interest rate of 20 because it is the nearest value to the real credit card interests in US dollars now.


* Profitability of model evaluation


![image](https://user-images.githubusercontent.com/49778314/121669354-e6cc3a00-cab4-11eb-8156-b9907de28135.png)


We can see that with the Stacking of Balanced Random Forest, Catboost and XGBoost we can get the best result by profit. Surprisingly, this model has been trained on resampled data (Stacking with Balanced Random Forest but trained on original data is not shown, but its result was worse), so we could conclude that additional balanced fitting after undersampling also has a positive influence on the model. This model gives us a 15% increase in revenue, which is a significant improvement for the bank. Also, we would like to draw your attention to the CatBoost model. Its financial result is as good as in the best model, but the number of clients in this model greater than in others. Bank may use this model if they are also interested in attracting clients to different products through credit cards.

* In addition,  
in place of a GUI, I have created the telegram bot in Scoring_bot/Scoring.py file that contains the best model. The bot allows a user to fill the form and learn if he or she may receive a loan.

Here is an example of how it works:

<p align="center">
  
    <img src="https://user-images.githubusercontent.com/34349664/147827903-2fbb6cf0-a622-41ec-aacb-b9f06a5553f2.png">
    <img src="https://user-images.githubusercontent.com/34349664/147827758-a167e77a-b4fd-4ee8-84e6-f46f6fa25397.png">
    <img src="https://user-images.githubusercontent.com/34349664/147827982-43fdbb55-bcc4-4b94-ad30-46bd4fadb948.png">
    <img src="https://user-images.githubusercontent.com/34349664/147828042-5eee63c2-d59a-4a6d-b76d-b232195c4387.png">
</p>
