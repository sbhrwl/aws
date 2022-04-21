# AI

## 1.DataWrangler
Data Wrangler										
-  Data Wrangler provides an end-to-end solution to 
a. Import, 
b. Prepare, 
c. Transform, 
d. Featurize, and 
e. Analyze data										
-  You can Integrate a Data Wrangler data flow into your machine learning (ML) workflows to simplify and streamline 
a. Data pre-processing and 
b. Feature engineering using little to no coding										
										
Import – 
- Connect to and import data from Amazon Simple Storage Service (Amazon S3), Amazon Athena (Athena), and Amazon Redshift.										
Data Flow – 
- Create a data flow to define a series of ML data prep steps. 
- You can use a flow to 
a. Combine datasets from different data sources, 
b. Identify the number and types of transformations you want to apply to datasets, and 
c. Define a data prep workflow that can be easily integrated into an ML pipeline.										
Transform – 
- Clean and transform your dataset using standard transforms like string, vector, and numeric data formatting tools. 
- Featurize your data using transforms like text and date/time embedding and categorical encoding.										
Analyze – 
- Analyze features in your dataset at any point in your flow. 
- Data Wrangler includes built-in 
a. Data visualization tools like scatter plots and histograms, as well as 
b. Data analysis tools like target leakage analysis and quick modeling to understand feature correlation.										
Export – 
- Data Wrangler offers export options to other SageMaker services, including 
a. Data Wrangler jobs, 
b. Feature Store, and 
c. Pipelines, 

Making it easy to integrate your data prep flow into your ML workflow. 
- You can also export your Data Wrangler flow to Python code										

## 2. Sagemaker Studio -> Data Flow		
<img src=images/"1.png">

## 3.FeatureStore
-  Amazon SageMaker Feature Store makes it easy 
a. for data scientists, machine learning engineers, and general practitioners 
b. to create, share, and manage features for machine learning (ML) development										
- Feature Store is a centralized store for features and associated metadata so features can be easily discovered and reused.										
-  You can create an online or an offline store.
a. The Online Store is used for low latency real-time inference use cases, and 
b. The Offline Store is used for training and batch inference.  										
<img src=images/"2.png">

## Feature Store Modes										
1. Online										
-  In online mode, features are read with low latency (milliseconds) reads and used for high throughput predictions. 
- This mode requires a feature group to be stored in an online store. 										
										
2. Offline										
-  In offline mode, large streams of data are fed to an offline store, which can be used for training and batch inference. 
- This mode requires a feature group to be stored in an offline store. 
- The offline store uses your S3 bucket for storage and can also fetch data using Athena queries. 										
										
3. Online and Offline										
- This includes both online and offline modes										

## Ingesting Data in Feature Store										
1. Streaming 										
-  A collection of records are pushed to Feature Store by calling a synchronous PutRecord API call. 
- This API enables you to maintain the latest feature values in Feature Store and to push new feature values as soon an update is detected.										
										
2. Ingest data in batches										
a. Author features using Amazon SageMaker Data Wrangler, 
b. Create feature groups in Feature Store and 
c. Ingest features in batches using a SageMaker Processing job with a notebook exported from Data Wrangler. 										
-  This mode allows for batch ingestion into the offline store. 
- It also supports ingestion into the online store if the feature group is configured for both online and offline use										
## 4.DataProcessingJob
-  Amazon SageMaker spins up a Processing job. 
- Amazon SageMaker 
a. Copies your script, 
b. Copies your data from S3 and then 
c. Pulls a Processing Container. 
- The Processing Container image can either be an Amazon SageMaker built-in image or a custom image that you provide. 										
<img src=images/"3.png">

### Processing Job										
-  The underlying infrastructure for a Processing job is fully managed by Amazon SageMaker. 
- Cluster resources are provisioned for the duration of your job, and cleaned up when a job completes. 
- The output of the Processing job is stored in the Amazon S3 bucket you specified.										
										
### Option for Processing Job										
- Data Processing with Apache Spark										
- Data Processing with scikit-learn										
- Use Your Own Processing Code										
