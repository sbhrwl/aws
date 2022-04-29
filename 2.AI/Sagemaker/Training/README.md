# Training

## Overview of training and deploying a model with Amazon SageMaker
<img src="images/1.png">

## Training
- Distribute training across one or many instances 
- Managed model training infrastructure
- Scales to Petabyte datasets 
- Compute instances for training are automatically launched and released
  - Stores artifacts in S3 

### 1. To train models on SageMaker use										
- SageMaker Console 
- SageMaker SDK and 
- Jupyter Notebook

## 2. Training job
- To train a model in SageMaker, you create a training job. 
- The training job includes the following information:
  - The URL of S3 bucket where you’ve stored the training data.
  - The compute resources (EC2) that you want SageMaker to use for model training. 
    - Compute resources are ML compute instances that are managed by SageMaker.
  - The URL of the S3 bucket where you want to store the output of the job.
  - The Amazon Elastic Container Registry path where the training code (Algorithm) is stored."										

## 3. Sagemaker framework options for Training				
| Options | Usage Scenario |
| ------- | -------------- |
| Built-in Algorithms | Training algorithms provided by SageMaker, Easy to use and scale, Optimized for AWS Cloud |
| Pre-built Container Images | Supports popular frameworks like fAxNet. TensorFlow, scikit-learn, PyTorch Flexibility to use wide selection of algorithms |
| Extend Pre-built Container Images | Extend pre-built container images to your needs  |
| Custom Container Images | Custom algorithm. language and framework Images |

### 3.1 Local Mode										
- Train a ML model on Sagemaker notebook instance										
- Make Predictions on the Trained Model on the Sagemaker notebook instance (local mode)										
- Sagemaker notebook instance is a managed Jupyter Notebook Environment										
### 3.2 [Pre Built Container Images](https://docs.aws.amazon.com/sagemaker/latest/dg/prebuilt-containers-extend.html)
- Train and Host a ML model using SGM supported ML Frameworks Docker Images										
- SGM offers pre built container images for
  - Apache MxNet
  - Tensorflow
  - Scikit learn
  - PyTorch
  - Chainer
  - SparkML
- These Containers can be used as it is to train ML model, saving us time for installing different Libraries for Model training										
- SGM provides SDKs to tain and host models using above frameworks										
- By using pre built containers, we can train and deploy ML models models quickly and reliably at any scale										
#### Apache Spark with Sagemaker 
<img src="images/2.png">

- Sageklaker Apache Spark Library in Python and Scala
- Directly read DataFrames in Spark Clusters
- Sagemaker Estimator automatically converts DataFrames to Protobuf format
- Train and Host using Sageklaker 
### SGM Local mode Training with Pre built container										
- Amazon SageMaker supports local training using the pre-built TensorFlow and MXNet containers. 
- Amazon SageMaker allows you to pull the containers from SageMaker-specific environments into your working environment.
- This means that if you have a model working locally, it should also work when deployed in a production environment (given that all configurations are correct). 
- This allows you to develop and debug training code efficiently by giving you the convenience of applying fixes to errors and seeing the changes immediately if it works.
<img src="images/3.png">

### Set up TensorFlow Docker container and [use Sagemaker SDK to create a model on your local machine](https://aws.amazon.com/blogs/machine-learning/use-the-amazon-sagemaker-local-mode-to-train-on-your-notebook-instance/)
- Pull the TensorFlow Docker container into a local machine and 
- SageMaker Python SDK setup for code testing : Execute the `pip install -U sagemaker` command.
