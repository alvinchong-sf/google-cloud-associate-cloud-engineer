# IAM
Cloud IAM let's you manage access control by defining who, has what access, for which resource.

## Principle of Least Privilege
A user, program, or process should have only the bare minimum privileges necessary to perform its function.

## Policy

### Members
1.  Google Account, Gmail
2.  Service Account
3.  Google Groups
4.  G Suite Domain
5.  Cloud Identity Domain, AllAuthenticatedUsers, AllUsers

### Roles
-  Permissions
   -  Collection of permissions
   -  You cannot grant a permission to the user directly
   -  You grant a role to a user and all the permissions that the role contains.

```bash
    Permissions
    compute.instances.list
    compute.instances.get
    compute.instances.start
    compute.instances.stop
    compute.instances.setMachineType
    compute.instances.delete
```

Three different types of roles
1.  Primitive (avoid these roles if possible)
    1.  Owner
    2.  Editor
    3.  Viewer

2.  Predefined (finer-grained access control than the primitive roles, created by Google)

3.  Custom (Tailor permissions to the needs of your orginization)

### Conditions
Used to define and enforce contional, attribute-based access control for Google Cloud resources.

Conditions allow you to choose granting resouref access to identities only if configured conditions are met

### Metadata
1.  etags - Concurrency control
2.  version - Specifies schema version

### Audit Config
Used to configure audit logging.


## Service Accounts
1.  User-managed (User created)
2.  Default (Using some GCP services)
3.  Google-Managed

### Service Account Permissions
### Access Scopes
Legacy Method

### Best Practices
-  Audit service accounts and keys using either serviceAccount.keys.list() method or the Logs Viewer page in the console.

-  Delete service account external keys if you don't need them

-  Grant the service account only the minimum set of permissions required to achieve their goal

-  Create service accoutns for each service with only the permissions required for that service


## Cloud Identity

### Device Management
Whitelist of approve applications, enfore work profiles

### Security
2 Step Verification

### Single Sign-on (SSO)
IDP (Identity Provider)

### Reporting
Audit logs, export logs to Big Query

### Directory Management
google Cloud Directory Sync

## IAM Best Practices

### Least Privilege
-  Apply only the minimal access level required for what's needed.
-  Predefined roles over primitive roles
-  Grant roles at the smallest scope
-  Child resources cannot restrict access granted on it's parent
-  Restrict who can create and manage service accounts
-  Be cautious owner roles

### Resource Hierarchy
-  Mirror your Google Cloud resource hirearchy structure to your orginization structure
-  Use projects to group resources that share the same trust boundary
-  Set policies at the organization level and at the project level rather than at the resource level
-  Use the security principle of least priviledge to grant IAM roles
-  Grant roles for users or groups at the folder level instead of setting it at the project level, if spanning across multiple projects

### Service Accounts
-  When using service accounts, treat each app as a seperate trust boundary
-  Do not delete service accounts that are in use by running services
-  Rotate user managed service account keys
-  Name service account keys to reflect use and permissions
-  Restrict service account access
-  Don't check in service account keys into source code

### Auduting
-  Use Cloud Audit Logs to regularly audit IAM policy changes
-  Audit who can edit IAM policies on projects
-  Export audit logs to Cloud Storage for long-term retention
-  Regularly audit service account key access
-  Restrict log access with logging roles

### Policy Management
-  To grant access to all projects in your Organization, use an orginization-level policy
-  Grant roles to a Google group instead of individual users where possible.
-  When granting multiple roles to a particular task, create a Google group instead.

