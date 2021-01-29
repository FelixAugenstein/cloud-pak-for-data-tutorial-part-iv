<h1 align="center" style="border-bottom: none;">:bar_chart: IBM Cloud Pak for Data Tutorial: Part IV</h1>
<h3 align="center">In this hands-on tutorial you will set up and run Jupyter Notebooks from within IBM Watson Studio to develop a machine learning model.</h3>

## Prerequisites

1. Sign up for an [IBM Cloud account](https://cloud.ibm.com/registration).
2. Fill in the required information and press the „Create Account“ button.
3. After you submit your registration, you will receive an e-mail from the IBM Cloud team with details about your account. In this e-mail, you will need to click the link provided to confirm your registration.
4. Now you should be able to login to your new IBM Cloud account ;-)

## Cloud Pak for Data Tutorials Part I to V

This tutorial consists of 5 parts, you can start with part I or any other part, however, the necessary environment is set up in part I.<br>
[Part I - data visualization, preparation, and transformation](https://github.com/FelixAugenstein/digital-tech-tutorial-watson-studio)<br>
[Part II - build and evaluate machine learning models by using the AutoAI](https://github.com/FelixAugenstein/digital-tech-tutorial-watson-studio-part-ii/)<br>
[Part III - graphically build and evaluate machine learning models by using the SPSS Modeler flow](https://github.com/FelixAugenstein/digital-tech-tutorial-watson-studio-part-iii/)<br>
[Part IV - set up and run Jupyter Notebooks to develop a machine learning model](https://github.com/FelixAugenstein/digital-tech-tutorial-watson-studio-part-iv/)<br>
[Part V - deploy a local app to test your model](https://github.com/FelixAugenstein/digital-tech-tutorial-watson-studio-part-v/) 

The first 4 parts of this tutorial are based on the [Learning path: Getting started with Watson Studio](https://developer.ibm.com/series/learning-path-watson-studio/).
## Create the first Jupyter Notebook

Create a Jupyter Notebook for predicting customer churn and change it to use the data set that you have uploaded to the project.

1. In the Asset tab, click Add to Project.

![Create Notebook](readme_images/create-notebook.png)

2. Select the Notebook asset type.
3. On the New Notebook page, configure the notebook as follows:

- Select From file tab and upload the customer-churn-notebook-py3.7.ipynb file from this repository.
- Enter the name for the notebook (for example, ‘customer-churn-notebook-py3.7’).
- Select the Python 3.7 to work with the notebook 'customer-churn-notebook-py3.7'
- Click Create Notebook. This initiates the loading and running of the notebook within IBM Watson Studio.

![Upload Notebook](readme_images/upload-notebook.png)

## Run the notebook

The notebook page should now be displayed. If the notebook is not currently open, you can start it by clicking the Edit icon displayed next to the notebook in the Asset page for the project. The notebook should look like this:

![Jupyter Notebook](readme_images/jupyter-notebook.png)

From the notebook page, make the following changes:

1. Scroll down to the third cell, and select the empty line in the middle of the cell. If not already open, click the 1001 data icon at the upper part of the page to open the Files subpanel.

![Pandas Dataframe](readme_images/pandas-dataframe.png)

2. In the right part of the page, select the Customer Churn .csv data set. Click insert to code, and select Insert pandas DataFrame. This adds code to the data cell for reading the data set into a pandas DataFrame.

Afterwards your Jupyter Notebook should look like this:

![After Import](readme_images/after-import.png)

3. Make sure you assign the dataframe to the variable "df". Therefore change the variable `df_data_X` to, for instance, `df_data_1` depending on your generated variable. When you execute cell 4 in the notebook, the data frame appears as the following:

![Dataframe Head](readme_images/dataframe-head.png)

4. Select File > Save to save the notebook.

<h3>Background on running Jupyter Notebooks</h3>

When a notebook is run, each code cell in the notebook is executed, in order, from top to bottom.

Each code cell is selectable and is preceded by a tag in the left margin. The tag format is In [x]:. Depending on the state of the notebook, the x can be:

- A blank, which indicates that the cell has never been run
- A number, which represents the relative order that this code step was run
- An *, which indicates that the cell is running

There are several ways to run the code cells in your notebook:

- One cell at a time. Select the cell, and then press Play in the toolbar, or use the shortcut on Mac `Shift + Enter`.
- Batch mode, in sequential order. From the Cell menu, there are several options available. For example, you can Run All cells in your notebook, or you can Run All Below, which starts running from the first cell under the currently selected cell, and then continues running all of the cells that follow.
- At a scheduled time. Press the Schedule button that is located in the upper-right section of your notebook page. Here, you can schedule your notebook to be run once at some future time or repeatedly at your specified interval.

## Data understanding and visualization

During the data understanding phase, the initial set of data is collected. The phase then proceeds with activities that enable you to become familiar with the data, identify data quality problems, and discover first insights into the data. In the Jupyter Notebook, these activities are done using pandas and the embodied `matplotlib` functions of pandas. The `describe` function of pandas is used to generate descriptive statistics for the features, and the `plot` function is used to generate diagrams showing the distribution of the data.

Execute all code cells until cell 8.

![Pandas Functions](readme_images/pandas-functions.png)

## Data preparation

The data preparation phase covers all activities that are needed to construct the final data set that will be fed into the machine learning service. Data preparation tasks are likely to be performed multiple times and not in any prescribed order. Tasks include table, record, and attribute selection as well as transformation and cleansing of data for the modeling tools. In the Jupyter Notebook, this involves turning categorical features into numerical ones, normalizing the features, and removing columns that are not relevant for prediction (such as the phone number of the client). The following image shows a subset of the operations.

Execute all code cells until cell 13.

![Data Preparation](readme_images/data-preparation.png)

## Modeling and evaluation

In the modeling phase, various modeling techniques are selected and applied and their parameters are calibrated to achieve an optimal prediction. Typically, there are several techniques that can be applied, and some techniques have specific requirements on the form of the data. Therefore, going back to the data preparation phase is often necessary. However, in the model evaluation phase, the goal is to build a model that has high quality from a data analysis perspective. Before proceeding to final deployment of the model, it’s important to thoroughly evaluate it and review the steps that are executed to create it to be certain that the model properly achieves the business objectives.

In the Jupyter Notebook, this involved splitting the data set into training and testing data sets (using stratified cross-validation) and then training several models using distinct classification algorithms such as `GradientBoostingClassifier`, support vector machines, random forest, and K-Nearest Neighbors.

Execute all code cells until cell 21.

![Build & Train Models](readme_images/build-train-models.png)

Following this step, we continue with printing the confusion matrix for each algorithm to get a more in-depth view of the accuracy and precision offered by the models.

Execute all code cells until cell 25.

![Confusion Matrix](readme_images/confusion-matrix.png)

Optional: Execute all code cells until cell 27.

## Deploying your model to Watson Machine Learning

Note: In the new Watson Machine Learning version you do not have credentials anymore. You have to create an API-Key. If you don't have one already create a new API-Key [here](https://cloud.ibm.com/iam/apikeys). If your WML service is deployed in US-South use the URL https://us-south.ml.cloud.ibm.com. 
You will also need a deployment space. If you haven't created a depeloyment space you can do that [here](https://dataplatform.cloud.ibm.com/ml-runtime/spaces?context=cpdaas). You can access your deployment spaces from your [Cloud Pak for Data Homepage](https://dataplatform.cloud.ibm.com).

In the last section of the notebook, we save and deploy the model to the Watson Machine Learning service. To access the service, we first need to create an API key. You need to be on the IBM Cloud Page, select the Manage box and navigate to the Access page. 

![Create API 1](readme_images/1_create_api.png)

Now click on API keys on the left hand-side and there you can create a new API key. Remember to write down your key or copy it to avoid losing it.

![Create API 2](readme_images/2_create_api.png)

Paste the API key into this notebook cell, behind the variable `apikey` and execute the code cell:

![Insert API 3](readme_images/3_insert_api.png)

Now we need to access our Deployment Space, which we created in the second tutorial:

[Part II - build and evaluate machine learning models by using the AutoAI](https://github.com/FelixAugenstein/digital-tech-tutorial-watson-studio-part-ii/)<br>

 Navigate to your Deployment and then go to the settings column, where you can find the Space ID. 

![Space ID 4](readme_images/4_space_id.png)

Copy and paste it in the Notebook.
And run the remaining Cells.

![Space ID 5](readme_images/5_space_id.png)


After the model is saved and deployed to Watson Machine Learning, we can access it in a number of ways.

In the Jupypter Notebook, we can pass data to the model scoring endpoint to test it.

Therefore execute all remaining code cells.

![Score Model](readme_images/score-model.png)

Select File > Save to save the notebook.

If we now go back to our Deployment Space, we can find the new model listed in the in the Deployments tab. The Model has been successfully deployed. 

![Model Deployed 6](readme_images/6_model_deployed.png)

If we click on the Model, we can navigate to a test environment.

![Model Test 7](readme_images/7_model_test.png)

On the Test tab, we can pass in a scoring payload JSON object to score the model (similar to what we did in the notebook). To run a test use the following JSON Code: 

```
{"fields": ["state", "account length", "area code", "international plan", "voice mail plan", "number vmail messages", "total day minutes", "total day calls", "total day charge", "total eve minutes", "total eve calls", "total eve charge", "total night minutes", "total night calls", "total night charge", "total intl minutes", "total intl calls", "total intl charge", "customer service calls"], "values":[[2,162,415,0,0,0,70.7,108,12.02,157.5,87,13.39,154.8,82,6.97,9.1,3,2.46,4]]}
```
After pasting the code in between the brackets after input_data: , press Predict to score the model.

![Model Test 8](readme_images/8_model_test.png)

The prediction result is given in terms of the probability that the customer will churn (1/True) or not (0/False). You can try it with other values.

## If you have any questions just contact me

Felix Augenstein<br>
Digital Tech Ecosystem & Developer Representative @IBM<br>
Twitter: [@F_Augenstein](https://twitter.com/F_Augenstein)<br>
LinkedIn: [linkedin.com/in/felixaugenstein](https://www.linkedin.com/in/felixaugenstein/)
