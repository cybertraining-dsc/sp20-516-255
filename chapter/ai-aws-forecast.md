#  AI Service [AWS Forecast](https://aws.amazon.com/forecast/) on AWS sp20-516-255, Porwal, Prafull

## Overview

Amazon Forecast is a fully managed service for time-series forecasting. AWS Forecast uses machine learning to combine time series data with additional variables to provide highly accurate forecasts. There is no infratructure to maintain or machine learning models to build, train, or deploy.  User's need to provide historical data and any additional data that may impact forecasts. Users only pay for what they  use, and there is no minimum fees and no upfront commitments.

Amazon Forecast can be used to generate predictions on time-series data to predict Operational metrics, Business metrics, Resource requirements and product demands. 

## Features of AWS Forecast 

* Amazon Forecast uses deep learning algorithms, such as DeepAR+ and traditional statistical methods for forecasting related time series data. Forecast works with any type of historical data and can combine affecting additional factors to produce more accurate forecasts than non machine learning tools or traditional tools.
* Provides set of pre-defined algorithms. No need to build, train, or deploy machine learning models, once data is provided, Forecast can load and inspect the data, select right algorithm , train a model, tune hyperparameter, model iteratively to provide accuracy metrics
* Provides visualized forecast for easy understanding and integrate with many existing tools.
* Tool generates probabilitic forecasts at different quantiles and for multiple backtest windows. User's can choose according to buisness needs and model accuracy

## Supported Domains 

* RETAIL  –  Retail demand forecasting

* INVENTORY_PLANNING  – Supply chain and inventory planning

* EC2 CAPACITY –  Amazon Elastic Compute Cloud (Amazon EC2) capacity

* WORK_FORCE  – Work force planning

* WEB_TRAFFIC – Estimating future web traffic

* METRICS  –  Business and Operational Metrics

* CUSTOM – All other types of time-series

## Predefined Algorithms 

Amazon Forecast provides the following predefined algorithms: 

* Autoregressive Integrated Moving Average (ARIMA) Algorithm : arn:aws:forecast:::algorithm/ARIMA

* DeepAR+ Algorithm : arn:aws:forecast:::algorithm/Deep_AR_Plus

* Exponential Smoothing (ETS) : arn:aws:forecast:::algorithm/ETS

* Non-Parametric Time Series (NPTS) : arn:aws:forecast:::algorithm/NPTS

* Prophet Algorithm : arn:aws:forecast:::algorithm/Prophet

* Supports hyperparameter optimization (HPO)

## How Amazon Forecast Works 

![](../images/sp20-516-255-AWS_Forecast.PNG){#fig:sp20-516-255-AWS_Forecast}

For any Amazon Forecast project user's work with 

* [Data Sets and Dataset Groups](https://docs.aws.amazon.com/forecast/latest/dg/howitworks-datasets-groups.html) : A dataset is the historical data used to train a predictor and a dataset group is a collection of complimentary datasets having details on set of changing parameters over a period. A dataset group can have up to three datasets: target time series, related time series, and item metadata. The datasets in Amazon Forecast can be managed by [Forecast APIs](https://docs.aws.amazon.com/forecast/latest/dg/api-reference.html). Each attribute in the dataset should ideally represent either feature or a dimension. Dimensions are aspects of data which do not change much over a period and Features represent any parameters which vary across time. Additional auditing columns like Timestamp can be present if needed.

* [Predictors](https://docs.aws.amazon.com/forecast/latest/dg/howitworks-predictor.html) – A predictor is a trained model which can make forecasts based on historical time-series data and can by created by using CreatePredictor operation. A prdictor is created using the dataset, a forecast horizon, evaluation parameters, featarization configuration and forcasting algorithms.

* [Forecasts] (https://docs.aws.amazon.com/forecast/latest/dg/howitworks-forecast.html) : A forecast can be created by using CreateForecast operation, queried by QueryForecast operation and extracted by CreateForecastExportJob operation. This operation creates forecast for every item in the dataset group that was used to train the predictor. 

## Steps:  

Forecast uses Amazon S3 to store the target time-series data used to train predictors and that can generate forecasts So a permission to S3 bucket and an IAM role for Forecast need to be setup as a pre-requisite. 

*  Step 1 - Import Training Data
*  Step 2 - Train a Predictor
*  Step 3 - Create a Forecast
*  Step 4 - Retrieve a Forecast

## Forecast Service Limits 

![](../images/CreateDataSetImportJob.PNG) {#fig:Create Dataset Limits}

![](../images/CreatePredictor.PNG) {#fig:Create Predictor Limits}

![](../images/General_Resource_Limits.PNG) {#fig:General Resource Limits}

## Data Security : 

User's retain ownership of the data and only authorized employees from AWS have access to the data processed by Amazon Forecast. Data Security is a shared responsibility between AWS and Customer. 

* Security of the cloud – AWS is responsible. 

* Security in the cloud – Customer's responsibility 

##  [Pricing](https://aws.amazon.com/forecast/pricing/) : 

Pay for what you use model with no minimum fees and upfront commitments. There are three different types of costs in Amazon Forecast:

* Generated forecasts: A forecast is a prediction of future values for a single time series over any time horizon. Forecasts are billed in units of 1,000 and are generated by default at three quantiles (10%, 50%, 90%).

* Data storage: Cost for each GB of data stored and used to train models by Amazon Forecast.

* Training Time: Cost for each hour of training required for a custom model based on data provided by customers. 

## Free Tier : 

Generated forecasts: Up to 10K time series forecasts per month

Data storage: Up to 10GB per month

Training hours: Up to 10 hours per month

## Alternative Products 

* Qubole.

* ServiceNow Now Platform.

* scikit-learn.

* Microsoft Knowledge Exploration Service.

* Google Cloud AutoML.

* BigML.

* Microsoft Recommendations API.

* Machine-learning in Python.

## References

https://aws.amazon.com/forecast/
https://aws.amazon.com/forecast/features/
https://docs.aws.amazon.com/forecast/latest/dg/howitworks-datasets-groups.html
https://docs.aws.amazon.com/forecast/latest/dg/api-reference.html
https://docs.aws.amazon.com/forecast/latest/dg/howitworks-predictor.html
https://docs.aws.amazon.com/forecast/latest/dg/forecast.dg.pdf
