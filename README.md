# Project-4-Group-1

Group members:

* Anton: [link to github](https://github.com/Anton0Lee)
* Lucas: [link to github](https://github.com/ljulbrich)
* Roy: [link to github](https://github.com/Roy-Ip)
* Theos: [link to github](https://github.com/Kapedes)

## Credit card approval

### Project Proposal

Our project proposal is doccumented in the following google docs link: [Google drive link](https://docs.google.com/document/d/1Ol1J2J28xPfOGt4Mhp_1h59lXy09CLNFtk_UX-2BcWE/edit#heading=h.z6ne0og04bp5).<br>
The goal of this project is to predict whether someone is likely to have their loan approved based off their demographics and loan repayment behaviours by using Deep Learning and Random Forests.<br><br>
We have successfully trained a random forest model to accuratly predict whether or not a loan would default with an 85% accuracy. We have documented our steps taken to do this in the methodoloy section below.<br>

### Datasets used

We had decided on using this dataset from Kaggle which provides information on 439,000 credit card users and their loan repayment behaviours: [Credit card approval dataset](https://www.kaggle.com/datasets/rikdifos/credit-card-approval-prediction/data?select=credit_record.csv). This dataset provided a good challenge as it was very unbalanced and had outliers which had to be removed in order to get an accurate prediction.

### Methodology

Firstly, we had to select the appropriate features to be used in our ML model. We had ended up dropping 20 individual features as they didn't provide any significant information to the dataset. We were able to find these outliers by exploring the dataset using power BI. `link to powerBI presentation here`. We had also attempted to find outliers using PCA and KMeans clustering, and mutual information classification. The mutual information classification provided a good visualisation on what features effect loan repayment behaviours.<br>
![Mutual info classification graph](https://github.com/Ljubrich/Project-4-Group-1/blob/main/Images/Mutual%20information%20classification.png)<br>
The PCA and KMeans clustering did not seem to seperate the data into meaningful clusters around the status feature. It did however get 100% in the first two PCA variables.<br>
![Status vs KMeans clustering](https://github.com/Ljubrich/Project-4-Group-1/blob/main/Images/Status%20vs%20KMeans.PNG)
<br>

Secondly, we started performing tests on a sequential deep learning network. We had experimented with different numbers of nodes per layer and layers, as well as number of epochs. We found that the most accurate results were achived with three hidden layers with 10, 28, 28 nodes. The first hidden layer used a ReLU activation function. The second two hidden layers used a sigmoid activation function. The output layer consisted of a single node as we were performing a binary classification; the activation was sigmoid. With this we were able to achive an accuracy of 70.61% with a loss of 60.58% at 20 epochs.<br>
![Sequential Deep Learning Model Results](https://github.com/Ljubrich/Project-4-Group-1/blob/main/Images/Sequential%20deep%20learning%20results.PNG)
<br>

Thirdly, the sequential deep learning model was optimised using Keras HyperParameter tuning. Unfortunately this provided less accuracy than the original deep learning model at 70.03% accuracy and 62.34% loss.<br>
![Keras Hyperparameters Tuned Results](https://github.com/Ljubrich/Project-4-Group-1/blob/main/Images/Keras%20tuner%20results.PNG)
<br>

Finally, we used a random forest model to perform the same predictions. With 100 estimators, we had achieved an accuracy of 84.55%.<br>
![Random Forest Model Results](https://github.com/Ljubrich/Project-4-Group-1/blob/main/Images/Random%20Forest%20results.PNG)<br>
<br>
We had further attempted to optimise the model using a grid search. However, the grid search had reduced the accuracy to 74.53%.<br>
![Grid Search Results](https://github.com/Ljubrich/Project-4-Group-1/blob/main/Images/Grid%20search%20results.PNG)<br>


### Data Delivery Methods

* The data came from two CSV files from kaggle: `application_record.csv` and `credit_record.csv`, both located in the Resources directory.
* The data from those two tables was merged into: `credit_card_data.csv` located in the main directory.
* After cleaning the dataset with feature selection, the final dataset was save as: `CleanedDataset.csv` and `Status.csv`, also located in the Resources directory.

These CSV files were accessed by our jupyter notebooks by using the Pandas and Pathlib libraries.

### File structure

* `Final Model.ipynb` This jupyter notebook contains our final machine learning model attempts
* `credit_card_data.csv` This CSV contains the merged dataset for this project
* `Images` This file stores all images which are found in the README.md file for this project
* `Keras Directory` This file stores all keras tuner builds, checkpoint weights, and trials
* `Resources` This file contains all CSV files used with and generated by our programs.
* `Feature selection and clustering` This file contains jupyter notebooks used in the mutual information classification and KMeans clustering.
* `Test & Attempts` This file contains all previous attempts to make an accurate machine learning model
