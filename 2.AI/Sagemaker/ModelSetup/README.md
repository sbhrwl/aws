# Using SageMaker for Model Training with XGBoost						
- Step 1	Upload Train, Validation and Test files to S3					
- Step 2	Select Algorithm Container Registry Path (Path varies by region)					
- Step 3	Configure Estimator (EC2 Instance) for training					
- Step 4	Specify algorithm specific hyper parameters					
- Step 5	Specify Channels					
- Step 6	Train/Fit the Model					
- Step 7	Deploy Model to the Endpoint (EC2 Instance)					
- Step 8	Run Predictions on the Endpoint					

## Upload Train, Validation and Test files to S3
### 1. Import Standard libraries and Sagemaker SDK
<img src="images/1.png">

### 2. write_to_s3
<img src="images/2.png">

### 3. Verify files in S3 Bucket		
<img src="images/3.png">

## Algorithm Setup
### 1. Establish a session with AWS and Get execution role				
<img src="images/4.png">

- **The above IAM role is derived from the user with which we logged in to work on sagemaker jupyter notebook instance**
- Note
  - IAM Role should have 										
    - Access to S3 bucket										
    - Access to spin up new instances to TRAIN the model and to store the trained model artifacts										

### 2. Get Image Registry path		
- Sagemaker maintains all the Algorithms as Docker Containers and these containers are stored in [Elastic Container Registry](https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-algo-docker-registry-paths.html) 
  - ECR ~ Docker Hub
- ECR is regional service and Algorithm path is different for each region
- SageMaker maintains a separate image for algorithm and region
<img src="images/5.png">

- Sagemaker now provides lookup capability with **get_image_uri** method, Specify										
  - Region										
  - Algorithm										
  - Version Tag (:1/latest)										
- get_image_uri method returns correct Registry path		
<img src="images/6.png">

### 3. Note down the Algorithm Path
<img src="images/7.png">

## Configure Estimator for Training
- Estimator is the EC2 Instance on which Sagemaker will 
  - Deploy the Algorithm (Algorith path from previous step) and 
  - Perform training of the data
										
#### Create an Instance of Estimator										
- Use method sagemaker.estimator.Estimator and specify										
  - Algorithm Container to use										
  - Role to use										
  - Number of instances to use										
  - Type of instance to use										
  - Location of Trained model artifacts (output) on S3										
  - Sagemaker session										
  - Base job name
  <img src="images/8.png">
  
## Specify Hyper Parameters		
### Configure Hyperparameters		
- Use method set_hyperparameters								
  - max_depth: Depth of Tree										
  - objective: BikeRental problem is regression problem										
  - eta: Learning rate										
  - num_round: Number of Trees										
<img src="images/9.png">

- Estimator instance with hyper parameters			
<img src="images/10.png">

## Specify Channels
### Configure Channels
- In Sagemaker terminology, Location of Data files is termed as Channels										
- Training Channel points to Training folder in S3										
- Validation Channel points to Validation folder in S3										
<img src="images/11.png">

- S3_Data_Type as **S3Prefix** implies that the provided path is a "Prefix" and not actual file name 										
<img src="images/12.png">

## Train/Fit the Model
### 1. Train
<img src="images/13.png">

### 2. What happens during Fit process?
- Training Instance is launched										
- Algorithm Container Image is downloaded from ECR										
- Container Image is deployed to the Training Instance										
<img src="images/14.png">

- iv. Model fits and calculates RMSE for each Tree
<img src="images/15.png">

### 3. Verify Training Job on console
<img src="images/16.png">

## Deploy the Model
- Endpoint is the EC2 Instance on which Sagemaker will 
  - Deploy the TRAINED MODEL (model.tar.gz file) and 
  - Enable us to perform Predictions against the trained Model
### Deploy Model to the Endpoint		
Specify
- Instance Count										
- Instance Type
<img src="images/17.png">

- Based on above specified parameters, 
  - Sagemaker will spin up the required number of instances, 
  - Host the Model on instances and 
  - Create an Endpoint.
- Endpoint will be used to make predictions
<img src="images/18.png">

### [Model Hosting: 3 Step Process](https://docs.aws.amazon.com/sagemaker/latest/dg/how-it-works-deployment.html)
- Create a model in SageMaker, 
- Create an endpoint configuration for an HTTPS endpoint and 
- Create an HTTPS endpoint

## Run Predictions
<img src="images/19.png">

## Connect to an existing endpoint for making predictions
### Step 1: Acquire Endpoint
- How Calls to an EndPoint are authenticated? (Endpoint Security)							
- We can accquire existing endpoint instance by using method RealTimePredictor by specifying EndpointName
- The role used to launch Jupiter Notebook instance should have all the needed permissions. 
- This role is authenticated by SageMaker sdk.
<img src="images/20.png">

### Step 2: Specify what kind of Request and Response will be served by the predictor						
- Request will be sent in CSV format
<img src="images/21.png">

- We will be parsing the reponse back manually
<img src="images/22.png">

### Step 3: Pass values to the predict method
- Values can be passed to predict method as an array
<img src="images/23.png">

- Send first 2 observations to the predict method										
<img src="images/24.png">

- Predict method will 
  - Use serializer (csv_serializer) to convert array values to CSV format and 
  - Forwards the request to the endpoint
### Step 4: Output from predict method
- predict method returns back BYTE array of predicted values (As we sent 2 Observations, we got 2 predicted values)
<img src="images/25.png">

#### How to send multiple observations in a call effectively?
- In step 3, we made a Call to the Endpoint via Internet.										
- Suppose, we have lot of observations for which we need to predict the Outcome				
##### Approach 1: Send all the observations together and make one call to the endpoint
- Drawback: Payload will become too large and may encounter errors									
##### Approach 2: Split the observations into smaller sets and make multiple calls to the endpoint		
- Drawback: This will involve too many roundtrips
- Approach 2 can be improved by sending reasonable size of subset (using array_split method of numpy) to the endpoint
<img src="images/26.png">

- Now we are sending 650 rows in each call to the endpoint to make predictions
<img src="images/27.png">

## Submitting Predictions to Kaggle
- Perform Inverse Transform
<img src="images/28.png">

- Create CSV for predicted values
- Submit results to Kaggle
<img src="images/29.png">
