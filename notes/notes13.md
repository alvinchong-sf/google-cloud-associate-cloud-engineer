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


## Operations Suite (Formerly Stackdriver)
1.  Monitoring
2.  Logging
3.  Error Reporting
4.  Debugger (APM)
5.  Trace (APM)
6.  Profiler (APM)

eg. (dynatrace, New Relic, PagerDuty, AppDynamics, LightStep, BlueMedora, DataDog, (x)Matters, Grafana Labs, Splunk)

-  A suite of tools for logging, monitoring and application diagnostics
-  Available for GCP and AWS
-  VM monitoring with agents

### Cloud Monitoring
-  Collects measurements, or metrics, to help you understand how your applications and system services are performing
-  Collects metrics to provide insights
-  Dashboards and Charts
-  Workspaces are needed to use cloud monitoring
-  Agents are recommended to monitor VMs
-  Works together with cloud logging
-  Support to monitor GKE
-  Alerting

### Cloud Logging
-  Central repository for log data from multiple sources
-  Real-time log management and analysis
-  Tight integration with monitoring
-  Platform, system and application logs
-  Export logs to other sources
-  Logs Viewer only shows logs from one project
-  Log Entry records a status or an event
-  Logs are a named collection of log entries within a GCP resource
-  Retention period how logs are kept
-  Audit logs who did what, where and when
-  Access Transparency Logs actions taken by Google staff
-  Agent Logs

### Error Reporting
-  Real time error monitoring and alerting
-  Counts, analyzes and aggregates all the errors in your GCP environment
-  Alerts you when a new application error occurs
-  Integrated into Cloud Functions and GAE Standard
-  Issue tracking integration
-  In beta for GCE, GKE, GAE Flexible, AWS EC2
-  Go, Java, Node.js, .NET, PHP, Python, Ruby

### Debugger
-  Inspect the state of a running application in real time, without stopping or slowing it down.
-  Debug a running application with no latency
-  "Snapshot" the call stack in your application
-  Logpoints allow you to inject logging into running services
-  Can be hooked into remote Git repo - Github, GitLab, Bitbucket
-  Can be installed on non-GCP environments
-  Go, Java, Node.js, .NET, PHP, Python, Ruby

### Trace
-  Collects latency data from App Engine, HTTPS load balancers and applications
-  Helps to understand how long it takes your application to handle incoming requests (latency)
-  Collects latency data from cloud resources and apps
-  Integrated with GAE Standard
-  Can be install on GCE, GKE, and GAE
-  Can be installed on non-GCP environments
-  Go, Java, Node.js, .NET, PHP, Python, Ruby

### Profiler
-  Continuosly gathers CPU usage and memory allocation information from your applcations
-  Helps discover patterns of resource consumption
-  Low-profile
-  Needs profiling agent to be installed
-  Can be install on GCE, GKE, and GAE
-  Can be installed on non-GCP environments
-  Go, Java, Node.js, .NET, PHP, Python, Ruby

