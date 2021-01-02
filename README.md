# SageMaker Deployment Project

This project uses IMDB dataset to perform sentiment analysis on it using a simple _PyTorch LSTM model_. This model was trained on `ml.p2.xlarge` _AWS Sagemaker notebook instance._ and deployed on `ml.m4.xlarge` _AWS Sagemaker notebook instance._ The trained LSTM model can be deployed as a simple web app which can take user input and predict if the provided movie review was _positive or negative_. This was a project assignment for Udacity Machine Learning Nanodegree. 

### Prerequisite

- You need to have an AWS account using which you can create a Sagemaker notebook instance. 
- You can clone this repo on your instance using the terminal of your notebook instance. 
- You need to select `conda-python3` kernel in the notebooks.
- You need to install _sagemaker_ using the following command in the notebook itself: 
         `!pip install sagemaker==1.72.0`
- You will need to create a _Lambda_ function for pre-processing the input movie review provided by the end-user. 
- You will alse need to use _AWS API Gateway_ to be able to get a public endpoint for the deployed LSTM model. 

### Project Structure
**SageMaker Project.ipynb**
- The main Python Notebook that performs the pre-processing and uploads the train and test data to _S3_.
- It also defines the the estimator and provides an entry point for the custom model and fits the model
- Deploys the trained model
- Uses the model for prediction on the test dataset

**train/model.py**
- This file defines the layers of the LSTM model and the forward function 

**train/train.py**
- This file has functions to load and train the model
- It also defines the hyperparameters provided by the estimator's arguments

**serve/predict.py**
- This file contains the code for serialize the input and output. 
- Code for converting the movie review into model compatible format by calling the preprocessing code
- Code responsible for predicting the output

**website/index.html**
- This is the simple html file that contains the form for taking input form the user
- You will need to **add your own deployed model's endpoint** in the `action` of the form 

### Evaluation Score
- The accuracy of the LSTM model was 81.07%

Please see the [README](https://github.com/udacity/sagemaker-deployment/tree/master/README.md) in the root directory for instructions on setting up a SageMaker notebook and downloading the project files (as well as the other notebooks).
