# Capstone Project

This project addresses a classification problem using both Hyperparameters HyperDrive and Automated Machine Learning (AutoML) to optimize and deploy the best model. The objective is to utilize both the HyperDrive and AutoML APIs provided by Azure to develop and refine this project.
The dataset for this project pertains to the survival probability of Titanic passengers, which has been sourced from Kaggle. The comprehensive steps involved in this project are as follows:

1. Dataset Selection:
- Select the Titanic passenger survival probability dataset as the primary dataset for this project.
2. Data Importation:
- Import the chosen dataset into the Azure workspace for further analysis and model training.
3. Model Training:
- Automated Machine Learning (AutoML): Leverage Azure's AutoML to automate the process of model selection and hyperparameter tuning.
- HyperDrive: Employ HyperDrive to further fine-tune hyperparameters and optimize model performance.
4. Model Comparison:
- Evaluate and compare the performance of the models generated by AutoML and HyperDrive to determine the most effective model.
5. Model Deployment:
- Deploy the best-performing model to a production environment for real-world application.
6. Endpoint Testing:
- Test the deployed model's endpoint to ensure it operates correctly and delivers accurate predictions.

## Project Set Up and Installation
*OPTIONAL:* If your project has any special installation steps, this is where you should put it. To turn this project into a professional portfolio project, you are encouraged to explain how to set up this project in AzureML.

## Dataset
This is the Titanic dataset taken from Kaggle with link: https://www.kaggle.com/c/titanic/data 
Below is description of data:
- Survived: if the passenger survived or not (True/False)
- Pclass: the	Ticket class	(1 = 1st, 2 = 2nd, 3 = 3rd)
- Sex:	Gender	(Male, Female)
- Age: the passenger's age (20, 30, 45, ...)
- SibSp: the	number of siblings / spouses	(0, 2, 3, ...)
- Parch: the	number of parents / children (0, 1, 2, ...)
- Ticket:	the ticket id (A/5 21171, ...)
- Fare: the	Passenger fare (10.34, 8.50, ...)
- Cabin: the	cabin id	(A12, B34, ...)
- Embarked: the	Port of Embarkation	(C = Cherbourg, Q = Queenstown, S = Southampton)
### Task:
1. Dataset description
- The Titanic survival dataset consists of 12 features and a total of 891 records. The dataset is sourced from Kaggle and provides historical data on Titanic passengers, including their demographic details, ticket information, and survival status.
- Survival Status: 342 passengers survived. 549 passengers did not survive.
- Survival Rate: The survival rate is approximately 38% across the dataset.
- The goal of this project is to build a classification model that can predict the survival probability of passengers based on the provided features. 
- To get the dataset, we can download from Kaggle. Import Dataset: Upload the dataset to the Azure workspace for further processing and analysis.

2. Hyperparameter Tuning
- Select Hyperparameters: hyperparameters such as C (regularization parameter) and max_iters (maximum iterations) for tuning.
- Submit Run: Execute the model training run with the selected hyperparameters and record the run with the highest accuracy.
- Register Best Model: Save and register the model that achieved the best performance during hyperparameter tuning.

3. Auto ML
- Dataset Preparation: Use the same Titanic survival dataset.
- Configure AutoML Settings: Set up AutoML with primary metrics, maximum iterations, and timeout settings to automate the process of model selection and tuning.
- Register Best Model: Save and register the best-performing model.

4. Model Comparison
- Evaluate Models: Compare the accuracy and performance of the models trained using hyperparameter tuning and AutoML.
- Select Best Model: Identify the model with the superior accuracy for deployment.

5. Model Deployment
- Deploy Model: Deploy the best model.
- Prepare for Inference: Download the environment and the score.py script from the best run to configure the inference pipeline.
- Check Endpoint Status: Verify that the endpoint deployment is healthy and ready for use.

6. Endpoint Testing
- Send Post Request: Send a post request to the deployed model's endpoint to obtain predictions.
- Compare Predictions: Evaluate the predictions against the ground truth values to assess the model's performance.


### Access
Below is how we can access the dataset:
1. Go to Kaggle, login and get the dataset (https://www.kaggle.com/c/titanic/data)
2. Upload the dataset to github repo and choose to copy the 'raw' data option
3. Read the dataset using Dataset.Tabular.from_delimited_files.

## Automated ML
please rephrase the text in more detail manner: Setting the automl Experiment timeout minutes: 30 minnutes timeout Max concurrent iterations: 5 times Primary metric: accuracy Automl config: Task: classification task Label column: Survived Featurization: auto feature engineer Debug log: automl_errors.log
Here’s a more detailed version of the text:

Setting Up AutoML
To configure AutoML for the Titanic survival classification task, several key parameters must be defined:

1. Experiment Timeout
Timeout Duration: The total time allocated for the AutoML experiment is set to 30 minutes. This means the entire process will stop if it reaches this time limit, ensuring efficient use of resources and preventing excessively long runs.

2. Concurrent Iterations
Maximum Concurrent Iterations: The experiment is configured to run up to 5 iterations concurrently. This allows multiple models to be trained and evaluated simultaneously, speeding up the process and optimizing the use of computational resources.

3. Primary Metric
Evaluation Metric: The primary metric selected for evaluating the model's performance is accuracy. This metric measures the proportion of correctly classified instances out of the total instances, making it a suitable choice for binary classification tasks like predicting survival.

4. AutoML Configuration
- Task Type: The task is defined as a classification task. This indicates that the goal is to predict categorical outcomes—specifically, whether a passenger survived or not.
- Label Column: The label column, which contains the target variable, is set to 'Survived'. This column indicates the survival status of each passenger.
- Featurization: Featurization is set to automatic. This means AutoML will automatically handle feature engineering, including data preprocessing, transformation, and selection of the most relevant features to improve model performance.
- Debug Logging: Debug logging is enabled, and the logs will be saved to a file named automl_errors.log. This file will capture any errors or issues that occur during the AutoML process, aiding in troubleshooting and ensuring a smooth experiment run.

### Results
*TODO*: What are the results you got with your automated ML model? What were the parameters of the model? How could you have improved it?

*TODO* Remeber to provide screenshots of the `RunDetails` widget as well as a screenshot of the best model trained with it's parameters.

## Hyperparameter Tuning
*TODO*: What kind of model did you choose for this experiment and why? Give an overview of the types of parameters and their ranges used for the hyperparameter search


### Results
1. Register the Titanic dataset to workspace
![image](https://github.com/user-attachments/assets/3a8e5225-c81a-4957-bea5-bac0ce9a9f12)

2. Register the best model from automl
- This is the models tested by Auto ML. We can see that the Voting Ensemble is the best model for accuracy

![image](https://github.com/user-attachments/assets/7d9878c5-ee02-4b4e-90d5-eb5e9ddb9854)

- The model accuracy is 84%
- The model is registered
- The model is deployed successfully

![image](https://github.com/user-attachments/assets/5ec6f71f-2e6e-4df6-943c-4cf443e2d47a)

3. Run Details
- The Run Details show the status of the experiment

![image](https://github.com/user-attachments/assets/625ce318-de77-4b8b-b227-1c31e4a22668)

- The best run from automl

![image](https://github.com/user-attachments/assets/2a20f4eb-1198-401f-87fe-b84e452d800c)

![image](https://github.com/user-attachments/assets/e15de51f-bd5a-4430-a4d0-269d2f1e7838)

4. Best model registration
![image](https://github.com/user-attachments/assets/63c940a6-2b8b-4dcd-8a16-35388110cee9)

![image](https://github.com/user-attachments/assets/448f3939-92b7-4c93-af82-46d8e3769586)


## Model Deployment
*TODO*: Give an overview of the deployed model and instructions on how to query the endpoint with a sample input.

## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:
- A working model
- Demo of the deployed  model
- Demo of a sample request sent to the endpoint and its response

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
