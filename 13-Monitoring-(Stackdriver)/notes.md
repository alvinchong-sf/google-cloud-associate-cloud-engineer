## Big Data
-  Massive amounts of data
-  Characteristics of Big Data on traditional databases
   -  Too expensive to store
   -  Traditional databases are not cost effective
   -  No flexibility for storing unstructured data
   -  Cannot accommodate real time data
   -  Lack support for petabyte-scale data volumes
-  Apache Hadoop & NoSQL to the rescue
   -  Extremely complex to deploy and manage
-  Help companies make better decisions - business value
   -  Gain useful insight
   -  Increase revenue
   -  Get or retain customers
   -  Improve operations
   -  Better with Machine Learning

### Big Data Services

#### BigQuery
-  Fully managed, petabyte scale, low cost analytics data warehouse
-  Streaming and Batch Ingest to BigQuery
-  Free Bulk Loading(Data Transfer Service)
-  Real Time analytics
-  Automatic high availability
-  Automatic backup and restore
-  Standard SQL
-  Big Data ecosystem integration
-  Web UI, bq, API
-  Data governance
-  Geo-expansion
-  IAM, VPC mgmt
-  Data encryption

#### Pub/Sub
-  Fully-managed, realtime messaging service
-  Send and receive messages between independent applications.
-  Creates messages and sends (publishes) them to the messaging service on a specified topic

#### Composer
-  Fully managed workflow orchestration service, built on Apache Airflow

#### Dataflow
-  Fully managed processing service for executing Apache Beam pipelines for batch and realtime data streaming
-  Almost like an ETL(export transform load) tool

>  <-- Pipeline -->
>  Source --> Read Transform --PCollection--> Transform --PCollection--> Write Transform --PCollection--> Database

#### Dataproc
-  Fully managed Spark and Hadoop service
-  Can be used to replace on-prem Hadoop infrastructure

##### Dataproc vs Dataflow

| Dataproc                                      | Dataflow            |
|-----------------------------------------------|---------------------|
| Managed                                       | Severless           |
| Dependencies to tools in the Hadoop ecosystem | Apache beam runtime |

#### Cloud Datalab
-  An easy-to use interactive tool for data exploration, analysis, visualization, and machine learning
-  Datalab -> Collect data -> Organize data -> Create model -> Train model -> Deploy trained model -> Datalab

#### Cloud Dataprep
-  Serverless, intelligent data service for visually exploring, cleaning, and preparing structured and unstructured data for analysis, reporting, and machine learning.


## Machine Learning
-  Functionality that enables software to perform tasks without any explicit programming or rules.
-  Trained to recognize patterns in collected data using algorithmic models
-  Collected data includes video, images, speech or text
-  Cloud is an efficient place for ML due to the use of massive computation at scale
-  Better with Big Data

#### What can Machine Learning do?
-  Categorize images such as photos, faces, or satellite imagery
-  Look for keywords in text documents or emails
-  Flag potentially fraudulent transactions
-  Enable software to respond accurately to voice commands
-  Translate languages in text or audio

### Machine Learning Platform

#### Sight
1.  Vision
    1.  Pre-trained machine learning models that allow you to assign labels to images and quickly classify them into millions of predefined categories

2.  Video Intelligence
    1.  Pre-trained machine learning models that automatically recognize a vast number of objects, places, and actions in stored and streaming video

#### Language
1.  Natural Language
    1.  Derive insights from unstructured text using Google machine learning
2.  Translation
    1.  Translation enables you to dynamically translate between languages using Google's pre-trained or custom machine learning models

#### Conversation

1.  Dialog Flow
    1.  Natural language understanding platform that makes it easy to design and integrate a conversational user interface into your application or device

2.  Speech-to-Text
    1.  Accurately convert speech into text using Google's AI technologies

3.  Text-to-Speech
    1.  Enables develoeprs to sysntesize natural- sounding speech with 100+ voices, available in multiple languages and variants

4.  AutoML
    -  Fully Managed Suite of machine learning products
    


