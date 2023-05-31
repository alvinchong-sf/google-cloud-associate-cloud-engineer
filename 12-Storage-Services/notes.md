# Cloud Storage
-  Consistent, scalable, large-capacity, highly durable object storage - not file or block
-  Worldwide accessibility and worldwide storage locations
-  Use for data files, text files, pictures, videos
-  Excels for content delivery, big data sets and backups
-  Buckets and Objects

## Cloud Storage buckets
-  basic container that holds your data
   -  Organize your data Access control
-  Upon creation
   -  Globally unique name
   -  Geographic location
   -  Storage class
   -  Access Control
   -  Labels(optional)
-  Location
   -  Region
   -  Dual-region
   -  Multi-region
-  Storage class
   -  Standard
   -  Nearline
   -  Coldline
   -  Archive
-  Bucket Access
   -  Uniform: Standalone IAM
   -  Fine-grained: IAM + ACLs

### Cloud Storage objects
-  Object (no limit ) --> Bucket
   -  Object Data
   -  Metadata
      -  Properties
         -  Name
         -  Storage class

### Storage Classes
-  Hot Data
   -  Standard
      -  Maximum availability
      -  No storage duration
      -  Analytical worklods and transcoding
      -  $0.02 /GB/month
      -  Nearline
   -  Nearline
      -  Low-cost for infrequently accessed data
      -  30 day min storage duration
      -  Data backup and data archiving
      -  $0.01/GB/month
      -  $ Data access

- Cold Data
  -  Coldline
     -  Very low-cost for infrequently accessed data
     -  90 day min. storage duration
     -  Data backup and data archiving
     -  $ 0.004 /GB/month
     -  $$ Data access
  -  Archive
     -  Lowest-cost archival storage
     -  365 day min. storage duration
     -  Cold data storage disaster recovery
     -  $0.0012/GB/month
     -  $$$ Data access

-  Availability is best at dual/multi regions compare to single region

### Access Control
-  IAM
   -  Standard IAM permissions (Recommended over ACLs)
   -  Permissions inherited hierarchically
-  Access Control List (ACL)
   -  defines who has access to your buckets and objects, as well as what level of access they have
-  Signed URLs
   -  time-limited read/write access URL
   -  Access the object for the duration of time you specify
   -  Allow users without credentials to perform specific actions on a resource
   -  Actions are taken as a user or service account
   -  Do not need account - just the URL
   -  `gsutil signurl -d 10m private-key.json gs://bowties/spring2021/plaidbowtie.jpg`
-  Signed Policy Documents
   -  Specify what can be uploaded to a bucket

### IAM and ACLs
-  IAM
   -  Recommended over ACLs
   -  Two levels of granularity project or bucket level
   -  Roles available: Primitive, Standard, Legacy
-  Access Control List (ACL)
   -  Granular permissions
   -  Entry = permission + scope
   -  CAUTION: ACLs overlap IAM roles

### Versioning
-  Object are immutable
-  Objects are never edited in place
-  Replacement is marked as end of object lifecycle and begining of a new one

### Object Lifecycle Management
-  Setting a Time to live (TTL) for objects
-  Delete or archive non-current versions
-  Downgrade storage class to save $$$
-  Use cases
   -  Downgrade the storage class of objects older than 365 days to Coldline Storage
   -  Delete objects created before January 1, 2020
   -  Keep only the 3 most recent versions of each object in a bucket with versioning enabled.

> Rules -> Conditions -> Action

### Cloud Storage considerations
-  Changes are in accordance to object creation date
-  Once an onject is deleted, it cannot be undeleted
-  Lifecycle rules can take up to 24 hours to take effect
-  Test lifecycle rules in development first


```bash
# ssh into cloud shell
gcloud compute ssh bowtie-instance --zone us-east1-b

# Add sign url with service account key to a specific object in storage bucket
gsutil signurl -d 10m your-private-key.json gs://your-bucket-name/your-object-name.jpg

# Get versioning
gsutil versioning get gs://your-bucket-name

# Set on versioning
gsutil versioning set on gs://your-bucket-name
```


## Cloud SQL
-  Fully managed, relational database service (RDBMS)
-  DBaaS (Database as a Service)
-  Low latency, transactional, relational db workloads
-  MySQL, PostgreSQL, and SQL Server: New
-  Replication: Read Replicas
-  High Availability
-  On-demand and automatic backups
-  Point in time recovery
-  30 TB storage capacity (HDD or SSD)
-  Automatic storage increase
-  Encryption at rest and in transit
-  Billed for instance, persistent disk and egress traffic
-  Connecting to Cloud SQL
   -  Connecting to Cloud SQL with Public or Private IP
   -  Cloud SQL Proxy
   -  Authorize a network
   -  External Applications

### Backups
-  Types of backups
   -  On-demand
      -  Create at any time
      -  Persist until you delete them
   -  Automated
      -  4 hour backup window
      -  Occur everyday
      -  7 most recent backups are retained
   -  Point in time recovery (PITR)
      -  Recover an instance to a specific point in time
      -  Always creates a new instance

## Cloud Spanner
-  Fully managed relational database service that is both strongly consistent and horizontally scalable
-  DBaaS(Database as a Service)
-  Supports schemas, ACID transactions, and SQL queries
-  Globally distributed
-  Handles replicas and sharding
-  Automatic scaling and node redundancy
-  Up to 99.999% availability
-  Data layer encryption, audit logging, IAM integration
-  Designed for financial services, ad tech, retail and global supply chain, gaming
-  Pricing: $0.90/node/hr + $0.30/GB/mo.

## NoSQl Databases
1.  Cloud Bigtable
    1.  Fully managed, wide-column NoSQL database designed for terabyte to petabyte-scale workloads that offers low latency and high throughput.
    2.  Built for real time app serving & large-scale analytical workloads
    3.  Regional Service
    4.  Automated replication
    5.  Store large amounts of single-keyed data
    6.  Add nodes when oyu need them
    7.  Cluster resizing
    8.  Ideal data source for MapReduce operations
    9.  High-priced
    10.  Storage engine uses
         1.  Batch MapReduce operations
         2.  Stream processing/analytics
         3.  Machine-learning applications
    11.  Use Cases
         1.  Time-series data
         2.  Marketing data
         3.  Financial data
         4.  IoT data
         5.  Graph data

2.  Cloud Datastore
    1.  Fully Managed, highly scalable NoSQL document database built for automatic scaling, high performance, and ease of application development
    2.  High-availability of reads and writes
    3.  Atomic transactions
    4.  Automatic Scaling
    5.  SQL -like query language (GQL)
    6.  Strong and eventual consistency
    7.  Encryption at Rest
    8.  Being retired in favor of Cloud Firestore in 2021
    9.  Datastore emulator
        1.  Provides local emulation of the production Datastore environment
        2.  Component of the Google Cloud SDK's gcloud tool
    10.  Use cases
         1.  Product Catalogs
         2.  User profiles
         3.  Transaction based on ACID properties

3.  Firestore for firebase
    1.  Flexible, scalable NoSQL cloud database to store and sync data for client and server-side development
    2.  Collection stores Document and doc store Data
    3.  Serverless
    4.  Multi-region replication
    5.  Expressive querying
    6.  Realtime updates
    7.  Offline support
    8.  Secure
    9.  Realtime Database
    10.  Simpler version of Firestore
    11.  Firebase: A mobile app development platform that provides tools and cloud services to help enable developers to develop apps faster and more easily

4.  Memorystore
    1.  Fully managed service for either Redis or Memcached in-memory data store to build application caches
    2.  High Availability
    3.  Scale as needed
    4.  Secure
    5.  Always up to date
    6.  Use cases
        1.  Caching
        2.  Gaming (leaderboards, user profiles)
        3.  Stream processing