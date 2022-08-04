# Big Data Project

## Project Description
Project for uChicago MSCA program for Big Data Class. Performed with Ziyoda Saidova, and Petra Hutabarat for Instructor Ashish Pujari. The project was to use pySpark and big data platforms to conduct EDA, and machine learning analysis on large dataset of our choice. We decided to conduct analysis on Chicago taxi rides data.

We primarly used Jupyter Notebooks using PySpark in conjunction with GCP services. We created the data lake using GCP Cloud Storage, and the neccesary Spark cluster using GCP dataproc services. We also used a Google VM to facilitate the transfer of the data from the public api to our data lake. All the data came from [City of Chicago Data Portal](data.cityofchicago.org). The instructions are meant to be an example of how to use the Google Cloud Platform, so the instructions will be generalized as possible.

## Content Description

Providing brief description of each of the items in the repository. Will cover how to use and implement after descriptions as well.

#### code
Contains jupyter notebooks written in pyspark. Will eventually be uploaded to cluster in order to run.

#### data
Importantly does not include the main taxi ride data. Includes helper data that will be joined with overall taxi data to map community names to numbers in order to make data more descriptive

#### gcp_code
Command line code to use within GCP cli, to both upload the data, and create cluster with the correct parameters.

#### Group_4_Big_Data_Project.pptx
Final presentation summarizing results, methods, and proccess.

## Project Setup

Now walk through setting up and running the project on GCP. This process can be used for any large dataset that where using spark would be useful to handle the volume of data. 

### GCP Account Setup

First step is to create your free or paid Google Cloud Platform account. Use any gmail address you have and you will be credited $300 to start your project. You can contribute additonal value as neccesary if the project becomes larger, but $300 was more than enough for our project. Visit the [Google Cloud Platform Website](https://cloud.google.com/) and "Get Started for Free" using an existing email address. You will need to add a credit card for billing, but it will not be used unless you exceed the $300 amount.

After this I reccomend creating a project for your work. You can add collaborators to your project that will be able to access all the resources you create within the project.

### Storage Bucket Setup

With GCP console search "Cloud Storage". This will take you the Cloud Storage product where you can create your storage bucket. Give the bucket a descriptive name as you will refer to it later. Specify the details of the buckets including choosing a storage area close to you, and security settings. Our project was relatively non-sensitive so we had standard security procedures

### Adding Data to Storage Bucket

There are a few different ways to add data to the storage bucket, but I will only cover what we used. This involves using a Google Virtual Machine that made adding large data sets to the bucket more feasible, having run into time out and storage issues intitially. You always have the option of simply uploading files directly through the UI for smaller files as well.

Begin by navigating to the VM Instances product in  Google Cloud Console. Create a VM, assigning the specification that are optimal for your project. We used a standard E2 series, and default machine type. The most import specification to change is in the Boot Disk storage. You need to allocate enough boot disk space to store your data set. For example our total data size was around 20gb so had to set the storage to exceed that.

Now you can use the `cline_data_import.md` file in the GCP_code folder to upload the data to the Virtual Machine and move it to the bucket. Make sure to replace the bucket name, and data api links with your own. We used a piece-meal approach, uploading one year at a time. This made testing our eventual spark code on a smaller subset of the data easier.

I highly recommend deprecating your Virtual Machine after the upload proccess, as you will be charged hourly for it. It will not be neccesary for the rest of the project.

### Creating Data Cluster

Now that we have set up our storage, we set up our compute resource. We will use the Google Dataproc product in order to do so. The easiest way to do this is simply input the code in the `GCP-SparkNLP.txt` in the GCP command line interface. This will spin up a cluster that is connected to your created bucket. Make sure to change the bucket-name in your code, as well as make any adjustments you feel are neccesary including specifying your region.

The code provided will automatically install some niche packages for NLP that you can use if your project needs it. The code was provided by Instructor Ashish Pujari, with some tweaks to the disk size and worker number to improve performance.

The alternate method of creating a cluster, which could be easier for a first time user, would be to navigate to the Dataproc service within the console and manually create the cluster. This provides an easier to use interface for specifying the details of your cluster.

Again I highly reccomend deprecating the cluster when you are not using it. It's fairly straightfoward to recreate the cluster, and any notebooks you write will be stored in the bucket when you create them

### Using Compute Resources

Go to your created cluster and navigate to the "web interfaces" tab. This will provide you with all the jupyter and jupyter lab resources to start uploading and writing your code! I recommend using jupyter to start as it is easier to upload existing notebooks there. Upload the notebooks found in the code folder and run the code to replicate our results. Or start a new notebook to write your own.

Make sure to select the correct kernel. For our work we used the pyspark kernel to handle the distributed database. If you would like to run our code you will need to change the file structure of the imports to replicate your project (specifying the bucket and file path). You will also need to upload the helper data from the data folder to fully replicate our code.

With all this setup you should be ready to run your own Big Data Project

## Code Overview

Providing a brief overview of what is in each notebook, and what could be useful for your project.

#### `Data_Cleaning_EDA.ipynb`

Includes code to import data into notebook, clean and add helper columns for analysis. Also provides examples of visualizing data using matplotlib in conjunction with spark.

#### `EDA_Modelling_Taxi_Demand.ipynb`

Provides example of few different models including linear regression, gradient boosted tree, and decision tree models. Also provides some eda on the problem. Includes references to weather and holiday data that aren't currently included.

#### `EDA_Modelling_Taxi_Fare.ipynb`

Provides example of using linear regression and random forest models in spark. Also provides EDA.

## Conclusion

For summarized results of analysis and infrastructure refer to the included powerpoint. Big thanks to Ziyoda Saidova and Petra Hutabarat on the project. Also big thanks to Ashish for teaching us how to use all these technologies. For any questions feel free to reach out to arjun1508@gmail.com
