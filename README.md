## Description:

Our main Aim is to predict wether earthquake will happen or not at a given day and place. So we definitely would not like the model with higher False Neagtive values , since its more dangerous to predict as no earthquake while in reality earthquake happend than predicting earthquake will happen given in reality it did not. We can allow False positive more than False negative

Input to model from dataset has many important features to consider as time,latitude & longitude,depth of quake,magnitude,place, rest other features are error and non supporting features for classification.RandomForestCLassifer
![usgsdata](https://user-images.githubusercontent.com/100826424/219334865-6c910e6e-fbe4-4ab8-8926-e15dbacdd464.JPG)

Same parameters were used for randomforest as well to compare the algorithms used with gridsearchCV along with another hyperparamter max_features= ['auto','sqrt','log2'] that will let select features based on log(featues), sqrt(features) etc.

To create an orchestration pipeline for training and inference in Apache Spark using AWS Glue, follow these steps:
step 1 : upload a CSV file into the source folder in Amazon S3.
![s3](https://user-images.githubusercontent.com/100826424/219334796-976d0721-725d-424d-b589-b92a6dd0cc10.JPG)

step 2 : create AWS Glue crawler that creates the schema of the raw file from the stage folder in Amazon S3 and stores it in the database.
![crawler](https://user-images.githubusercontent.com/100826424/219334766-d4b0ea56-d9f7-4e64-b1be-c129b9fc7e20.JPG)

step 3 : create a Glue job in the AWS Glue console.
![jobs](https://user-images.githubusercontent.com/100826424/219334910-afa02216-3d92-4a7b-92b9-15db579725f5.JPG)

step 4 : create a notebook in Job  and handle the dataset by reading it from the catalog inside the aws glue.

step 5 : An AWS Glue job transforms, compresses, and partitions the raw file into Parquet format.

step 6 : The AWS Glue job also moves the file to the transform folder in Amazon S3.

step 7 : created  job for cleaning the dataset ,training and inference

step 8 : Once jobs are created then I created triggers to automate the jobs

step 9 : added all the triggers,jobs,crawlers in aws workflow to automate the pipeline run.

created df for metrics and storing it in s3 for future reference

configurations
Define the job parameters, including the name of the job, the IAM role to be used, and the number of worker nodes. Define the source data either by connecting to an Amazon S3 bucket or pointing to a file in the Glue data catalog. Use Spark's data processing capabilities to clean and preprocess the data. Train a machine learning model on the preprocessed data using the Spark MLlib library.
storing the processed data in amazon s3
Define a new task in AWS Glue that performs inference using the stored model. Connect the inference task to the output of the data processing stage to make predictions on new data. Store the predictions in an Amazon S3 bucket or in the Glue data catalog. Finally, monitor the performance of the pipeline and make necessary adjustments to optimize the accuracy of the predictions.
Workflow-pipeline
![aws glue capstone](https://user-images.githubusercontent.com/100826424/219335117-0159f6bf-d093-4a6b-a175-e16129ad9dff.JPG)

The above workflow runs as follows:
The Usgs datastart-copy is the trigger created which runs the following steps automatically: create a crawler which help us to get the dataset from s3
Usgs dataset-status will check whether the crawler is completed
Then it allow us to create a job the data cleaning step
Usgs  job-status will help us to check whether the previous job is completed
Then it allows us to run the next crawler which help us to load the cleaned data from s3,training and inference and store the output in s3.
This outline provides a general approach for creating an orchestration pipeline for training and inference in Apache Spark using AWS Glue, with the exact steps varying depending on the specific requirements of the use case.
