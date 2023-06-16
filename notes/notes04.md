## Cloud SDK

```bash
# gcloud command format
gcloud + compute + instances + create + example-instance-1 --zone=us-central1-a
```


## Commited Use Discounts(CUD)
-  Discounted prices when you commit to using a minimum level of resources for a specified term
-  1 or 3 year commitment
-  Commitment Types:
   -  Spend-based
   -  Resource-based
-  The commitment fee is billed monthly

### Spend-based commitment
-  Discount for a commitment to spend a minimum amount of a service (hours) in a particular region
-  25% discount for 1 year - 52% discount on a 3 year
-  Available for
   -  Cloud SQL database instances
   -  Google Cloud VMWare Engine
-  Applies only to CPU and memory usage

### Resource based commitment
-  Discount for commitment to spend a minimum amount for Compute Engine resources in a particular region.
-  Available for
   -  vCPU, Memory, GPU, and Local SSD
-  57% discount for most resources
-  70% for memory-optimized machine types
-  For use across Projects


### Sustained-use discounts
-  Automatic discounts for running COmpute Engine resources a significant portion of the billing month
-  Applies to vCPUs and memory for msot Compute Engine instance types
-  Does not apply to App Engine flexible, Dataflow and E2 machine types


### GCP Pricing Calculator
-  Quick estimate of what your usage will cost on Google Cloud
-  https://cloud.google.com/products/calculator

### Cloud Billing Budgets
-  Enables you to track your actual Google Cloud spend against your planned spend
-  Budget alert threshold rules that are used to trigger email notifications to help you stay informed about your spend
-  Define the scope of the budget
   -  Spend of billing account or more granular
-  Budget amount can be set to a specified total, or based on previous month's spend
-  Alert emails are sent to billing account admins and specific users when costs exceed a percentage of the budget
-  Email recipients can be customized by using Cloud Monitoring to specify other people to receive budget alert emails.
-  Use Pub/Sub for programmatic notifications or to automate cost management tasks.

### Limit and Quotas
-  Hard limit on how much of a particular Google Cloud resource your project can use
-  Rate Quota (Resets are specificed time)
-  Allocation Quota (must be explicitly released)

### Viewing your quota
-  IAM -> Quota
-  

### Billing Account Roles
1.  Billing Account Admin
    1.  Not allow to create billing account
2.  Billing Account Creator
    1.  Allow to create billing account
3.  Billing Account User
    1.  Allow to Link projects to billing account
    2.  Alows User to create new Projects linked to the billing account
4.  Billing Account Viewer
    1.  View transaction
    2.  View Cost and other account information
5.  Billing Project Manager
    1.  Link or Unlink projects from billing account
