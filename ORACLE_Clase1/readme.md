# Rabbitmq

```
docker run -d --name server-rabbitmq -p 9000:15672 -p 8080:5672 rabbitmq:management-alpine
```

# Oracle Cloud
```
1. Compute (VM Instances)
oci compute instance list # List all VM instances
oci compute instance launch --availability-domain <AD> --compartment-id
<compartment-ocid> --shape <shape> --image-id <image-ocid> # Create a new
VM instance

oci compute instance action --instance-id <instance-ocid> --action START # Start
a VM instance
oci compute instance action --instance-id <instance-ocid> --action STOP # Stop a
VM instance
oci compute instance terminate --instance-id <instance-ocid> --force # Terminate a
VM instance
oci compute instance get --instance-id <instance-ocid> # Get details of a specific
VM instance
oci compute image list --compartment-id <compartment-ocid> # List available
VM images
```
# 2. Oracle Kubernetes Engine (OKE)
```
oci ce cluster create --compartment-id <compartment-ocid> --name
<cluster-name> --vcn-id <vcn-ocid> # Create a new Kubernetes cluster
oci ce cluster list --compartment-id <compartment-ocid> # List all Kubernetes
clusters
oci ce cluster delete --cluster-id <cluster-ocid> --force # Delete a Kubernetes
cluster
kubectl get nodes # List all nodes in the cluster
kubectl get pods -A # List all running pods across namespaces
kubectl apply -f <file.yaml> # Deploy an application using a YAML file
kubectl delete -f <file.yaml> # Remove an application

```
3. Object Storage (Buckets & Files)
oci os bucket list --compartment-id <compartment-ocid> # List all storage buckets
oci os bucket create --compartment-id <compartment-ocid> --name
<bucket-name> # Create a new storage bucket

oci os object put --bucket-name <bucket-name> --file <file> # Upload a file to a
bucket
oci os object get --bucket-name <bucket-name> --name <file> --file
<destination-path> # Download a file from a bucket
oci os object delete --bucket-name <bucket-name> --name <file> --force # Delete
a file from a bucket
oci os bucket delete --bucket-name <bucket-name> --force # Delete a storage
bucket

```
4. Identity & Access Management (IAM)
oci iam user list # List all users
oci iam policy list --compartment-id <compartment-ocid> # List all IAM policies
oci iam group list # List all IAM groups
oci iam user create --compartment-id <compartment-ocid> --name <username>
--description "New User" # Create a new user
oci iam policy create --compartment-id <compartment-ocid> --name
<policy-name> --statements "[\"ALLOW GROUP Administrators TO MANAGE
ALL-RESOURCES IN TENANCY\"]" # Create a new policy

```
5. Oracle Cloud Database (Autonomous & VM-Based)
oci db autonomous-database list --compartment-id <compartment-ocid> # List all
Autonomous Databases
oci db system list --compartment-id <compartment-ocid> # List all Database
Systems
oci db autonomous-database create --compartment-id <compartment-ocid>
--db-name <db-name> --admin-password <password> # Create an Autonomous
Database
oci db autonomous-database stop --autonomous-database-id <db-id> # Stop an
Autonomous Database
oci db autonomous-database start --autonomous-database-id <db-id> # Start an
Autonomous Database
oci db autonomous-database delete --autonomous-database-id <db-id> --force #
Delete an Autonomous Database

```
6. Load Balancing & Networking
oci lb load-balancer list --compartment-id <compartment-ocid> # List all load
balancers
oci lb load-balancer create --compartment-id <compartment-ocid> --display-name
<lb-name> --shape-name flexible --subnet-ids <subnet-ocid> # Create a new load
balancer
oci network vcn list --compartment-id <compartment-ocid> # List all Virtual
Cloud Networks (VCNs)
oci network subnet list --compartment-id <compartment-ocid> # List all subnets
oci network security-list list --compartment-id <compartment-ocid> # List all
security lists
oci network security-list create --compartment-id <compartment-ocid> --vcn-id
<vcn-ocid> --display-name <name> # Create a security list
oci network security-list delete --security-list-id <security-list-ocid> --force #
Delete a security list

```
7. Oracle Cloud Logging & Monitoring
oci logging log list --compartment-id <compartment-ocid> # List all logs
oci logging log-group list --compartment-id <compartment-ocid> # List log
groups

oci monitoring metric list --compartment-id <compartment-ocid> # List available
monitoring metrics
oci monitoring alarm list --compartment-id <compartment-ocid> # List all alarms
oci monitoring alarm create --compartment-id <compartment-ocid> --display-name
<alarm-name> --metric-compartment-id <compartment-ocid> --namespace
<namespace> # Create an alarm


```
8. DevOps: OCI DevOps (Code Repos, Builds, Deployments)
oci devops project list --compartment-id <compartment-ocid> # List all DevOps
projects
oci devops repository list --compartment-id <compartment-ocid> # List code
repositories
oci devops build-pipeline list --compartment-id <compartment-ocid> # List build
pipelines
oci devops deployment list --compartment-id <compartment-ocid> # List
deployments
oci devops repository create --compartment-id <compartment-ocid> --name
<repo-name> # Create a new code repository
oci devops build-pipeline create --compartment-id <compartment-ocid> --name
<pipeline-name> # Create a build pipeline
oci devops deployment create --deployment-pipeline-id <pipeline-ocid>
--display-name <deployment-name> # Create a deployment

```
9. Oracle Cloud Security (Vault, Keys, Policies)
oci vault vault list --compartment-id <compartment-ocid> # List all vaults
oci vault key list --compartment-id <compartment-ocid> --vault-id <vault-ocid> #
List encryption keys

oci vault secret list --compartment-id <compartment-ocid> --vault-id <vault-ocid>
# List stored secrets
oci vault key create --compartment-id <compartment-ocid> --display-name
<key-name> --vault-id <vault-ocid> # Create a new encryption key
oci vault secret create --compartment-id <compartment-ocid> --vault-id
<vault-ocid> --secret-name <secret-name> --secret-content <secret-value> #
Create a new secret

```
```
```
```
```