# Severless Services

## App Engine Overview
-  Fully managed, serverless platform to develop and host web apps
-  PaaS service
-  Code or containers - Python, Java, NodeJS, Go, Ruby, PHP, or .NET
-  Autoscaling based on load
-  Versions: Allow for rollbacks, migrating or traffic splitting
-  Support for connecting to external storage
-  Standard and Flexible environments

### Standard and Flexible environments

| Standard                                          | Flexible                        |
| ------------------------------------------------- | ------------------------------- |
| Apps run in sandbox environment                   | Apps run in docker containers   |
| Specific versions of runtime used                 | Any version of runtimes used    |
| Run for free or at a very low cost                | No free quota available         |
| Designed for sudden and extreme spikes of traffic | Desgined for consistent traffic |
| Pricing based on instance hours                   | Pricing based on Vm resources   |
| n/a                                               | Manged VMs                      |

### Deploying an applition
`gcloud app deploy`

### Managing Instances
-  Automatically create and shut down instances
-  Specify a number of instances to run
-  Specify a scaling type
-  Automatic scaling
   -  based on matrics like request rate and response latencies
-  Basic scaling
   -  creates instances when your application receives requests
-  Manual scaling
   -  Specifies the numebr of instances that continuously run



## Cloud Function
-  Serverless
-  FaaS: Function as a Service
-  Runtime: Python, Java, NodeJs, Go, .NET core
-  Event-driven:
   -  Triggers: HTTP, Pub/Sub, Cloud Storage (Firestore, Firebase)
-  Billing: time + resources provisioned(memory)
-  Free Tier

### How Cloud Functions work
-  Bind 1 trigger to 1 function at a time
-  Source code is stored in Cloud storage as a zip file
-  Pushes the code image to container registry
```bash
                                                               -----> Cloud
        (event data)                                           |
trigger ------------->  cloud function ------------> Server ---|
                        ^  (stateless)                         -----> VPC
                        |
                        |
                        v
                        Container/Artifact Registry
```   

