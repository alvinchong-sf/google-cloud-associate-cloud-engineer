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