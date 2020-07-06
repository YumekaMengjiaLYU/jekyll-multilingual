![Screen Shot 2020-06-28 at 3.21.19 PM.png](https://www.dropbox.com/s/kqa7800rmmka9qd/Screen%20Shot%202020-06-28%20at%203.21.19%20PM.png?dl=0&raw=1)# Machine Learning Engineer Nanodegree
## Capstone Project
Mengjia Lyu  
June 26, 2020

## I. Definition

### Project Overview
Starbucks is the largest coffeehouse chain in the world. With its large app user base, targeted advertising can effectively increase the frequency of transactions per customer. Business insights are invaluable when it comes to targeted advertising. 

In order to maximize the efficacy of app advertising, we need to predict with reasonable accuracy what kinds of offers are most likely to lead to purchases for different customers. Machine learning algorithms can be employed to learn from data on transactions, customer demographics and offers sent.


- _Has an overview of the project been provided, such as the problem domain, project origin, and related datasets or input data?_


### Problem Statement
In this section, you will want to clearly define the problem that you are trying to solve, including the strategy (outline of tasks) you will use to achieve the desired solution. You should also thoroughly discuss what the intended solution will be for this problem. Questions to ask yourself when writing this section:
- _Is the problem statement clearly defined? Will the reader understand what you are expecting to solve?_
- _Have you thoroughly discussed how you will attempt to solve the problem?_
- _Is an anticipated solution clearly defined? Will the reader understand what results you are looking for?_

### Metrics

For any binary classification problem, accuracy is an important metrics as it measures the proportion of correct predictions.

We will use also AUC (Area Under the ROC Curve) to measure the performance of a model or result in my project. AUC can measure how well predictions are ranked by the probabilities^[See Reference [9]]. Then we can generate a list of possibles customers based on the ranked predictions given by AUC.  
## II. Analysis


### Data Exploration

Three datasets are provided by Starbucks for this problem:
#### The _portfolio_ dataset 
- `portfolio` contains information on offers and includes the following fields:
	- `id:`offer id represented by a string 
	- `offer_type:`the specific offer type that encompasses 
	    - BOGO (Buy one get one free) 
	    - informational (for example, seasonal products)
	    - discount
	- `difficulty:`the minimum amount of money required to spend for the offer to take effect
	- `reward:`the dollar value rewarded for completing an offer
	- `duration:`the shelf time of the offer
	- `channels:`the channels via which the offers are sent, encompassing mail, mobile, social and web
- first 10 rows sample of the dataset
![Screen Shot 2020-06-28 at 3.21.19 PM.png](https://www.dropbox.com/s/kqa7800rmmka9qd/Screen%20Shot%202020-06-28%20at%203.21.19%20PM.png?dl=0&raw=1)

- After checking for missing values, we find out that the `portfilio` dataset does not contain any missing values.
- As `channel` is a categorical variables, it is one-hot encoded to dummy variables `channel_email`, `channel_mobile`, `channel_social` and `channel_web`. 
- As `offer_type` also is a categorical variables, it is one-hot encoded to dummy variables `offer_bogo`, `offer_dicount` and `offer_informational`


#### The _transcript_ dataset 
- `transcript` contains information on customers' transaction history in one month and includes the following fields:
	- `value:`dictionaries whose key is either `offer id` or `amount` and whose value represents the corresponding offer id or amount of money incurred in the transaction
	- `event:`the event of encompassing four types
		- transaction
		- offer received
		- offer viewed
		- offer completed   
	- `person:` customer id represented by a string
	- `time:`the time in hours since start of the test
- first 10 rows sample of the dataset
![Screen Shot 2020-06-28 at 3.45.41 PM.png](https://www.dropbox.com/s/00ea8l7oe4ite7q/Screen%20Shot%202020-06-28%20at%203.45.41%20PM.png?dl=0&raw=1)
- After checking for missing values, we find out that the `portfolio` dataset does not contain any missing values.
-  As `event` is a categorical variable, it is one-hot encoded to dummy variables. 
-  As `value` is a list of dictionaries, it is unpacked according to the specific key.
-   - if the key is an offer, the value is moved to a new column  
-   - if the key is a transaction, the value is in a new column 
#### The _profile_ dataset 
- `profile` contains customers' demographic information and includes the following fields:
    - customer id represented by a string 
    - the age of the customer
    - the date when customer created an app membership account
    - the gender of the customer
    - customer's income
    - first 10 rows sample of the dataset
![Screen Shot 2020-06-28 at 3.48.02 PM.png](https://www.dropbox.com/s/flcdmsapkiq761c/Screen%20Shot%202020-06-28%20at%203.48.02%20PM.png?dl=0&raw=1)

-  As can be seen from the sample, the dataset contains missing values.
- After checking for missing values, we find out that the `portfilio` dataset contains 2175 missing values for both `income` and `gender` variables, making up 12.79% of the tatal data.
    - To deal with missing data, normally list-wise deletion or imputation is adopted. Upon a closer look, I discover that all customers whose `income` and `age` are missing have an age of 118 years, which is cleary a made-up number. Using t-test, it can be found out that the missing values are randomly distributed across all observations. Therefore we remove all rows with NaN values.
- The variable `became_member_on` is converted to `membership_time` which denotes the number of days the customer has been a Starbucks member. 
- As `gender` is a categorical variable, it is one-hot coded into three dummy variables `gender_female`, `gender_male` and `gender_other`.

Lastly we check for extreme outliers. According to the definition^[Stats: Measures of Position] that outliers are more than 3.0 times the interquartile range below the first quartile or above the third quartile, no extreme outliers are found.

We want to find how to best predict whether an offer would be responded to based on demographic, profiling and portfolio data. Therefore we combine all three datasets in the end.
To make a more educated, we only consider offers that have been **viewed**. In this case, we ensure that the customer is conscious of the offer details and actively make a decision as to whether to respond to the offer or not.

Our predictors are:
- Continuous variable
    * difficulty
    * age
    * income
    * duration
    * reward
    * membership_time
* Dummy variables
    - offer_bogo
    - offer_discount
    - offer_informational
    - channel_email
    - channel_mobile
    - channel_social
    - channel_web
    - gender_female
    - gender_male
    - gender_other

Our target variable is:
- outcome

### Exploratory Visualization
In this section, you will need to provide some form of visualization that summarizes or extracts a relevant characteristic or feature about the data. The visualization should adequately support the data being used. Discuss why this visualization was chosen and how it is relevant. Questions to ask yourself when writing this section:


The dataset is visualized through histograms.![Screen Shot 2020-06-28 at 10.32.49 PM.png](https://www.dropbox.com/s/4jkse2u7lnxczdc/Screen%20Shot%202020-06-28%20at%2010.32.49%20PM.png?dl=0&raw=1)

The features `age`, `income` and `membership_time` have relatively smooth and Gaussian like distributions. Other features like `difficulty`, `duration` and `reward` cannot be approximated as Gaussian, which we wil take account when considering algorithms. 

![Screen Shot 2020-06-29 at 10.41.28 AM.png](https://www.dropbox.com/s/1znyyyw4vesjukf/Screen%20Shot%202020-06-29%20at%2010.41.28%20AM.png?dl=0&raw=1)

Looking at the correlation pairplot, we can see that two feature pairs seem to be significant correlated between each other: 1.`difficulty` and `duration`. 2.`difficulty` and `reward`.  
### Algorithms and Techniques

- _Are the algorithms you will use, including any default variables/parameters in the project clearly defined?_

We start with the Naive Bayes algorithm which is also our benchmark model.
Then we Decision Trees, Support Vector Machines, Random Forests
The final classifier is a XGBoost classifier,

The measurements of performance used are accuracy score and AUC.
- The default variables
- _Are the techniques to be used thoroughly discussed and justified?_
- _Is it made clear how the input data or datasets will be handled by the algorithms and techniques chosen?_
- 

### Benchmark
I used Naive Bayes Classifier from _sklearn_ as our benchmark model. A naive bayes classifier _naively_ assumes that features in  the dataset are mutually independent, and can be trained easily and fast. 

As there isn't any related literature in the problem,  a simple classifier like naive bayes classifier makes a great candidate for benchmarking other more sophisticated model.

The Naive Bayes classifier achieved an accuracy of 74.28%.



## III. Methodology


### Data Preprocessing
The steps of data preprocessing done in the "Starbucks_Project" notebook are as follows:

 #### Feature Selection
 #### Feature Transformation
 
 #### Split into Training/Validation Sets  
 

_If the algorithms chosen require preprocessing steps like feature selection or feature transformations, have they been properly documented?_
- _Based on the **Data Exploration** section, if there were abnormalities or characteristics that needed to be addressed, have they been properly corrected?_




### Implementation
In this section, the process for which metrics, algorithms, and techniques that you implemented for the given data will need to be clearly documented. It should be abundantly clear how the implementation was carried out, and discussion should be made regarding any complications that occurred during this process. Questions to ask yourself when writing this section:
- _Is it made clear how the algorithms and techniques were implemented with the given datasets or input data?_
- The a implemented 3 different algorithms, including Neural Network, Naive Bayes, 

- _Were there any complications with the original metrics or techniques that required changing prior to acquiring a solution?_

### Refinement
In this section, you will need to discuss the process of improvement you made upon the algorithms and techniques you used in your implementation. For example, adjusting parameters for certain models to acquire improved solutions would fall under the refinement category. Your initial and final solutions should be reported, as well as any significant intermediate results as necessary. Questions to ask yourself when writing this section:
- _Has an initial solution been found and clearly reported?_
- 
- _Is the process of improvement clearly documented, such as what techniques were used?_
- 
- _Are intermediate and final solutions clearly reported as the process is improved?_
I searched for the best hyperparameters following the guide in this^[See Reference 7] [asdfhodgf]https://www.analyticsvidhya.com/blog/2016/03/complete-guide-parameter-tuning-xgboost-with-codes-python

## IV. Results
_(approx. 2-3 pages)_

### Model Evaluation and Validation
In this section, the final model and any supporting qualities should be evaluated in detail. It should be clear how the final model was derived and why this model was chosen. In addition, some type of analysis should be used to validate the robustness of this model and its solution, such as manipulating the input data or environment to see how the model’s solution is affected (this is called sensitivity analysis). Questions to ask yourself when writing this section:
- _Is the final model reasonable and aligning with solution expectations? Are the final parameters of the model appropriate?_
- The final model is reasonable and well aligned with our expectations.
- _Has the final model been tested with various inputs to evaluate whether the model generalizes well to unseen data?_
- _Is the model robust enough for the problem? Do small perturbations (changes) in training data or the input space greatly affect the results?_
- _Can results found from the model be trusted?_

### Justification
In this section, your model’s final solution and its results should be compared to the benchmark you established earlier in the project using some type of statistical analysis. You should also justify whether these results and the solution are significant enough to have solved the problem posed in the project. Questions to ask yourself when writing this section:
- _Are the final results found stronger than the benchmark result reported earlier?_
- _Have you thoroughly analyzed and discussed the final solution?_
- _Is the final solution significant enough to have solved the problem?_


## V. Conclusion
_(approx. 1-2 pages)_

### Free-Form Visualization
In this section, you will need to provide some form of visualization that emphasizes an important quality about the project. It is much more free-form, but should reasonably support a significant result or characteristic about the problem that you want to discuss. Questions to ask yourself when writing this section:
- _Have you visualized a relevant or important quality about the problem, dataset, input data, or results?_
- _Is the visualization thoroughly analyzed and discussed?_
- _If a plot is provided, are the axes, title, and datum clearly defined?_

### Reflection
In this section, you will summarize the entire end-to-end problem solution and discuss one or two particular aspects of the project you found interesting or difficult. You are expected to reflect on the project as a whole to show that you have a firm understanding of the entire process employed in your work. Questions to ask yourself when writing this section:
- _Have you thoroughly summarized the entire process you used for this project?_
- _Were there any interesting aspects of the project?_
- _Were there any difficult aspects of the project?_
- _Does the final model and solution fit your expectations for the problem, and should it be used in a general setting to solve these types of problems?_

### Improvement
To achieve the 
In this section, you will need to provide discussion as to how one aspect of the implementation you designed could be improved. As an example, consider ways your implementation can be made more general, and what would need to be modified. You do not need to make this improvement, but the potential solutions resulting from these changes are considered and compared/contrasted to your current solution. Questions to ask yourself when writing this section:
- _Are there further improvements that could be made on the algorithms or techniques you used in this project?_
To achieve 
- _Were there algorithms or techniques you researched that you did not know how to implement, but would consider using if you knew how?_
In addition, I would consider using algorithms like if I knew how to implement it.
- _If you used your final solution as the new benchmark, do you think an even better solution exists?_
- 

-----------

**References**
[1] [Quick and Easy Data Analysis for Your Machine Learning Problem](https://machinelearningmastery.com/quick-and-dirty-data-analysis-for-your-machine-learning-problem/)
[2][Understanding Data Normalization in Machine Learning](https://towardsdatascience.com/understand-data-normalization-in-machine-learning-8ff3062101f0)
[3][Tour of Data Preparation Techniques for Machine Learning](https://machinelearningmastery.com/data-preparation-techniques-for-machine-learning/)
[4][Feature Scaling for Machine Learning](https://www.analyticsvidhya.com/blog/2020/04/feature-scaling-machine-learning-normalization-standardization/)
[5][XGBoost hyperparameter tuning in Python using grid search](https://www.mikulskibartosz.name/xgboost-hyperparameter-tuning-in-python-using-grid-search/)
[6][Selecting Optimal Parameters for XGBoost Model Training](https://towardsdatascience.com/selecting-optimal-parameters-for-xgboost-model-training-c7cd9ed5e45e)
[7][Complete Guide to Parameter Tuning in XGBoost with codes in Python](https://www.analyticsvidhya.com/blog/2016/03/complete-guide-parameter-tuning-xgboost-with-codes-python/)
[8][Stats: Measures of Position](https://people.richland.edu/james/lecture/m170/ch03-pos.html#:~:text=Extreme%20outliers%20are%20any%20data,an%20extreme%20outlier%20if%20...)
[9][MLmuse: Correlation and Collinearity — How they can make or break a model]https://blog.clairvoyantsoft.com/correlation-and-collinearity-how-they-can-make-or-break-a-model-9135fbe6936a

[10][The 5 Classification Evaluation Metrics Every Data Scientist Must Know]https://towardsdatascience.com/the-5-classification-evaluation-metrics-you-must-know-aa97784ff226

- Does the project report you’ve written follow a well-organized structure similar to that of the project template?
- Is each section (particularly **Analysis** and **Methodology**) written in a clear, concise and specific fashion? Are there any ambiguous terms or phrases that need clarification?
- Would the intended audience of your project be able to understand your analysis, methods, and results?
- Have you properly proof-read your project report to assure there are minimal grammatical and spelling mistakes?
- Are all the resources used for this project correctly cited and referenced?
- Is the code that implements your solution easily readable and properly commented?
- Does the code execute without error and produce results similar to those reported?![Screen Shot 2020-06-28 at 3.21.19 PM.png](https://www.dropbox.com/s/kqa7800rmmka9qd/Screen%20Shot%202020-06-28%20at%203.21.19%20PM.png?dl=0&raw=1)