# Bias Mitigation of predictive models using AI fairness 360 toolkit

How do we remove bias from the machine learning models and ensure that the predictions are fair? What are the three stages in which the bias mitigation solution can be applied? This code pattern answers these questions and more to help developers, data scientists, stakeholders take informed decision by consuming the results of predictive models.

Fairness in data, and machine learning algorithms is critical to building safe and responsible AI systems from the ground up by design. Both technical and business AI stakeholders are in constant pursuit of fairness to ensure they meaningfully address problems like AI bias. While accuracy is one metric for evaluating the accuracy of a machine learning model, fairness gives us a way to understand the practical implications of deploying the model in a real-world situation. 

Fairness is the process of understanding bias introduced by your data, and ensuring your model provides equitable predictions across all demographic groups. Rather than thinking of fairness as a separate initiative, it’s important to apply fairness analysis throughout your entire ML process, making sure to continuously reevaluate your models from the perspective of fairness and inclusion. This is especially important when AI is deployed in critical business processes, like credit application reviews and fraud detection, that affect a wide range of end users. 

## How does the fairness algorithm work?

The bias mitigation algorithm can be applied in three different stages of model building. These stages are `pre-processing, in-processing & post-processing.` The below diagram demonstrates how it works. 

![](https://github.com/IBM/bias-mitigation-of-machine-learning-models-using-aif360/blob/main/images/aif-360-flow.png)

Machine learning models are increasingly used to inform high-stakes decisions about people. Although machine learning, by its very nature, is always a form of statistical discrimination, the discrimination becomes objectionable when it places certain privileged groups at systematic advantage and certain unprivileged groups at systematic disadvantage. Bias in training data, due to either prejudice in labels or under-/over-sampling, yields models with unwanted bias.

The `AIF360 Python package` contains nine different algorithms, developed by the broader algorithmic fairness research community, to mitigate that unwanted bias. They can all be called in a standard way, very similar to scikit-learn’s fit/predict paradigm. In this way, we hope that the package is not only a way to bring all of us researchers together, but also a way to translate our collective research results to data scientists, data engineers, and developers deploying solutions in a variety of industries. You can learn more about AIF 360 [here](http://aif360.mybluemix.net/).

In this Code Pattern, we will demonstrate the working of AI fairness 360 algorithm under different stages of building the model and deployment by using existing code pattern [Fraud Prediction](https://developer.ibm.com/patterns/fraud-prediction-using-autoai/).

## Architecture diagram

![]()

### Flow

1. Log in to Watson Studio powered by spark, initiate Cloud Object Storage, and  create a project.
2. Upload the .csv data file to Object Storage.
3. Load the Data File in Watson Studio Notebook.
4. Install `aif 360` Toolkit in the Watson Studio Notebook.
5. Analyze the results after applying the bias mitigation algorithm during pre-processing, in-processing & post-processing stages.

## Included components

* [IBM Watson Studio](https://www.ibm.com/cloud/watson-studio): Analyze data using RStudio, Jupyter, and Python in a configured, collaborative environment that includes IBM value-adds, such as managed Spark.

* [IBM AI Fairness 360 toolkit](https://www.ibm.com/blogs/research/2018/09/ai-fairness-360/): AI Fairness 360 (AIF360), a comprehensive open-source toolkit of metrics to check for unwanted bias in datasets and machine learning models, and state-of-the-art algorithms to mitigate such bias. 

* [IBM Cloud Object Storage](https://console.bluemix.net/catalog/services/cloud-object-storage): An IBM Cloud service that provides an unstructured cloud data store to build and deliver cost effective apps and services with high reliability and fast speed to market. This code pattern uses Cloud Object Storage.


## Featured technologies

* [Artificial Intelligence](https://developer.ibm.com/technologies/artificial-intelligence/): Any system which can mimic cognitive functions that humans associate with the human mind, such as learning and problem solving.
* [Data Science](https://developer.ibm.com/code/technologies/data-science/): Systems and scientific methods to analyze structured and unstructured data in order to extract knowledge and insights.
* [Analytics](https://developer.ibm.com/code/technologies/analytics/): Analytics delivers the value of data for the enterprise.
* [Python](https://www.python.org/): Python is a programming language that lets you work more quickly and integrate your systems more effectively.

## Steps using AIF 360 on Watson Studio


1. [Create an account with IBM Cloud](#1-create-an-account-with-ibm-cloud)
1. [Create a new Watson Studio project](#2-create-a-new-watson-studio-project)
1. [Add Data](#3-add-data)
1. [Create the notebook](#4-create-the-notebook)
1. [Insert the data as dataframe](#5-insert-the-data-as-dataframe)
1. [Run the notebook](#6-run-the-notebook)
1. [Analyze the results](#7-analyze-the-results)

## 1. Create an account with IBM Cloud

Sign up for IBM [**Cloud**](https://console.bluemix.net/). By clicking on create a free account you will get 30 days trial account.

## 2. Create a new Watson Studio project

Sign up for IBM's [Watson Studio](http://dataplatform.ibm.com/). 

Click on New Project and select per below.

![](https://github.com/IBM/bias-mitigation-of-machine-learning-models-using-aif360/blob/main/images/create_prj.png)

Define the project by giving a Name and hit 'Create'.

![](https://github.com/IBM/bias-mitigation-of-machine-learning-models-using-aif360/blob/main/images/def-prj.png)

## 3. Add Data

[Clone this repo](https://github.com/IBM/bias-mitigation-of-machine-learning-models-using-aif360)
Navigate to [data/assets](https://github.com/IBM/bias-mitigation-of-machine-learning-models-using-aif360/tree/main/data/assets) and save the file by name `fraud_data.csv` on the disk. The zip file `Pipeline_LabelEncoder-0.1.zip` also needs to be saved onto the disk. 

Click on Assets and select Browse and add the csv file from your file system. Repeat the step and add the zip file as an asset. 

![](https://github.com/IBM/bias-mitigation-of-machine-learning-models-using-aif360/blob/main/images/add_asset.png)

## 4. Create the notebook

* Open [IBM Watson Studio](https://dataplatform.ibm.com).
* Go to the project and click on Add 
* Click on `Create notebook` to create a notebook.
* Select the `From URL` tab.
* Enter a name for the notebook.
* Optionally, enter a description for the notebook.
* Enter this Notebook URL for Pre-processing  : https://github.com/IBM/bias-mitigation-of-machine-learning-models-using-aif360/blob/main/notebooks/Pre-processing.ipynb
* Enter this Notebook URL for In-processing   : https://github.com/IBM/bias-mitigation-of-machine-learning-models-using-aif360/blob/main/notebooks/In-processing.ipynb
* Enter this Notebook URL for Post-processing : https://github.com/IBM/bias-mitigation-of-machine-learning-models-using-aif360/blob/main/notebooks/Post-processing.ipynb
* Select the runtime (2 vCPU and 8 GB RAM.)
* Click the `Create` button.

After the notebooks are imported, click on `Not Trusted` and select the option as Yes to trust the source of the notebooks.

![](https://github.com/IBM/bias-mitigation-of-machine-learning-models-using-aif360/blob/main/images/not_trusted.png)

`This notebook has been created to demonstrate the steps for building the model using Watson Studio platform for fraud prediction usecase. For other usecases, the notebook has to be modified to read the new dataset and the same steps can be executed.`

## 5. Insert the data as dataframe

Click on 0010 icon at the top right side which will bring up the data assets tab.

![](https://github.com/IBM/bias-mitigation-of-machine-learning-models-using-aif360/blob/main/images/add.png)

Click on Insert to code dropdown and select the option Insert Pandas Dataframe.

![](https://github.com/IBM/bias-mitigation-of-machine-learning-models-using-aif360/blob/main/images/insert_dataframe.png)

## 6. Run the notebook

When a notebook is executed, what is actually happening is that each code cell in
the notebook is executed, in order, from top to bottom.

Each code cell is selectable and is preceded by a tag in the left margin. The tag
format is `In [x]:`. Depending on the state of the notebook, the `x` can be:

* A blank, this indicates that the cell has never been executed.
* A number, this number represents the relative order this code step was executed.
* A `*`, this indicates that the cell is currently executing.

There are several ways to execute the code cells in your notebook:

* One cell at a time.
  * Select the cell, and then press the `Play` button in the toolbar.
* Batch mode, in sequential order.
  * From the `Cell` menu bar, there are several options available. For example, you
    can `Run All` cells in your notebook, or you can `Run All Below`, that will
    start executing from the first cell under the currently selected cell, and then
    continue executing all cells that follow.

## 7. Analyze the results

After we run all cells in the notebook, the results are displayed at the end of each notebook per below.

### Pre-processing results

`Before pre-processing`

![](https://github.com/IBM/bias-mitigation-of-machine-learning-models-using-aif360/blob/main/images/before-pre-proc.png)

**`We can observe that, priviledged group had 37% more chance of getting a favorable outcome because of the bias in the dataset.`**

`After pre-processing`
![](https://github.com/IBM/bias-mitigation-of-machine-learning-models-using-aif360/blob/main/images/after-pre-proc.png)

**`We can observe that, after applying bias mitigation algorithm, there is no unfair advantage between priviledged & unpriviledged groups.`**

### In-processing results

![](https://github.com/IBM/bias-mitigation-of-machine-learning-models-using-aif360/blob/main/images/in-proc.png)

**`We can observe that, after applying bias mitigation algorithm during training, the equal opportunity difference has reduced from 17% to just 3%. The Average odds difference has reduced from 22% to 13% thereby making the model unbiased to a good extent. There's reduction in the numbers before and after de-biasing the dataset metrics.`**

### Post-processing results

![](https://github.com/IBM/bias-mitigation-of-machine-learning-models-using-aif360/blob/main/images/post-proc.png)

**`We can observe that, after applying bias mitigation algorithm on predicted labels, there's a change in balanced accuracy and equal opportunity difference indicating the fairness of the results.`**

This code pattern will be very helpful for developers, machine learning engineers, data scientists, architects, business stakeholders to make unbiased decisions on basis of the model results.


## Troubleshooting

[See DEBUGGING.md.](DEBUGGING.md)

## Citation for data :

`The dataset which is referenced in this code pattern is created and owned by R.K.Sharath Kumar, Data Scientist, IBM India Software Labs.`

## License

This code pattern is licensed under the Apache Software License, Version 2.  Separate third party code objects invoked within this code pattern are licensed by their respective providers pursuant to their own separate licenses. Contributions are subject to the Developer [Certificate of Origin, Version 1.1 (DCO)](https://developercertificate.org/) and the [Apache Software License, Version 2](http://www.apache.org/licenses/LICENSE-2.0.txt).

Check the [ASL FAQ link](http://www.apache.org/foundation/license-faq.html#WhatDoesItMEAN) for more details

