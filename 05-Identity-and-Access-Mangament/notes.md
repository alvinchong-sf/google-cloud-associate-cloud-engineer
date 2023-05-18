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