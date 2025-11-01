# AWS CLOUD
# EC2 (Elastic Compute Cloud)

```
# Listar todas las inastancias
aws ec2 describe-instances

# Iniciar una instancia
aws ec2 start-instances --instance-ids <id>

# Detener una instancia 
aws ec2 stop-instances --instance-ids <id>

# Terminar una instancia
aws ec2 terminate-instances --instance-ids <id>

# Crear un par de claves 
aws ec2 create-key-pair --key-name <name>

# Listar grupos de seguridad
aws ec2 describe-security-groups 

```
# S3 (Simple Storage Service)
```
# Listar los Almacenes S3
aws s3 ls

# Crear un almacen S3
aws s3 mb s3://<bucket>

# Subida de datos o achivos
aws s3 cp <file> s3://<bucket>

# Eliminar archivos
aws s3 rm s3://<bucket>/<file>

# Eliminar almacen S3
aws s3 rb s3://<bucket> --force

# Sincronizacion local y con el S3
aws s3 sync <local-dir> s3://<bucket>/

```
# IAM (Identidad and Access Management)
```
# Listar los usarios de IAM
aws iam list-users 

# Crear un usuario
aws iam create-user --user-name <name>

# Creacion de un rol
aws iam create-role --role-name <name> --asume-role-policy-document file://policy.json 

# Listar las politicas
aws iam list-policies

```
# VPC (Virtual Private Cloud)
```
# Listar VPCs
aws ec2 describe-vpcs

# Craer una VPC
aws ec2 create-vpc --cidr-block <CIDR>

# Delete o borrar una VPC
aws ec2 delete-vpc --vpc-id <id>

# Crear una Subnet
aws ec2 create-subnet --vpc-id <id> --cidr-block <CIDR>

# listar grupos de seguridad
aws ec2 describe-segurity-groups

# Listar compuerta de enlace de internet
aws ec2 describe-internet-gateways

```
# Lambda Functions (Serveless Computing)
```
# Listar todas las funciones lambdas
aws lambda list-functions

# crear function lambda
aws lambda create-functon --function-name <name> --runtime <runtime>
--role <role> --handler <handler>

# cargar codigo de la fumction lambda
aws lambda update-function-code --function-name <name> --zip-file
fileb://<file>.zip

# delete o borrar una lambda
aws lambda delete-function --function-name <name>

# Invocar una funcion 
aws lambda invoke --function-name <name> output.json

```
# AMAZON EKS (Elastic Kubernetes Service)
```
# Listar EKS Cluster 
aws eks list-clusters

# Muestra o describe un EKS cluster
aws eks describe-cluster --name my-cluster

#– Create an EKS cluster
aws eks create-cluster --name my-cluster --role-arn
arn:aws:iam::account-id:role/EKSRole --resources-vpc-config
subnetIds=subnet-xxxxxxx,securityGroupIds=sg-xxxxxxx

#– Configure kubectl to use the EKS cluster
aws eks update-kubeconfig --name my-cluster

# Para chequear los nodos de trabajo
kubectl get nodes

# Para listar los PODs activos o running
kubectl get pods -A

```
# AMAZON ECS (Elastic Container Service)
```
# – Listar ECS clusters
aws ecs list-clusters

# – Listar ECS services
aws ecs list-services--cluster my-cluster

# Describe an ECS service
aws ecs describe-services --cluster my-cluster --services my-service

```
# AWS CloudFormation
```
# Listar all stacks
aws cloudformation list stacks

# Create a stack
aws cloudformation create-stack --stack-name my-stack --template-body file://template.yml

```
# CI/CD (CodePipeline, CodeBuild, CodeDeploy)
```
# AWS CodePipeline
# – Listar all pipelines
aws codepipeline list-pipeline

# – Start a pipeline execution
aws codepipeline start-pipeline-execution --name my-pipeline

# AWS CodeBuild
# – Listar all CodeBuild projects
aws codebuild list-proyects
# – Start a build
aws codebuild start-build --proyect-name my-proyect 

# AWS CodeDeploy
#– List all CodeDeploy applications
aws deploy list-aplications

#– Deploy an application
aws deploy create-deployment --aplication-name MyApp
--deployment-group-name MyDeploymentGroup --s3-location
bucket=my-bucket,key=app.zip,bundleType=zip 
```
# Security & Compliance
```
#– List CloudTrail logs
aws cloudtrail describe-trails

#– List all secrets
aws secretsmanager list-secrets

#– Recuperar un secreto / Retrieve a secret
aws secretsmanager get-secret-value --secret-id my-secret 

```
# Monitoring & Logging (CloudWatch)
```
# Listar métricas disponibles /List available metrics.
aws cloudwatch list-metrics

# – Create una CloudWatch alarm
aws cloudwatch put-metric-alarm --alarm-name cpu-high --metric-name
CPUUtilization --namespace AWS/EC2 --statistic Average --period 300
--threshold 80 --comparison-operator GreaterThanThreshold --dimensions
Name=InstanceId,Value=i-xxxxxxxxxx --evaluation-periods 2
--alarm-actions arn:aws:sns:region:account-id:my-topic

#– List all log groups
aws logs describe-log-groups 

#– recuperar los logs/ Retrieve log events
aws logs get-log-events --log-group-name my-log-group --log-stream-name
my-log-stream

```
# Networking (VPC, ELB, Route 53)
```
# Amazon VPC
#– List all VPCs
aws ec2 describe-vpcs

#– List all subnets
aws ec2 describe-subnets

# Elastic Load Balancer (ELB)
#– List all load balancers
aws elbv2 describe-load-balancers

# Amazon Route 53
# – List hosted zones
aws route53 list-hosted-zones 

```
# Amazon ECR (Elastic Container Registry)
```
#– Authenticate Docker with ECR
aws ecr get-login-password | docker login --username AWS --password-stdin
<aws_account_id>.dkr.ecr.<region>.amazonaws.com

#– Listar all ECR repositories
aws ecr list-repositories

```
# AWS Systems Manager (SSM)
```
#– List managed instances
aws ssm describe-instances

#– Run a command on an EC2 instance - Ejecutar un comando en una instancia EC2
aws ssm send-command --document-name "AWS-RunShellScript" --targets
"Key=instanceIds,Values=i-xxxxxxxxxx" --parameters commands="sudo apt
update"

```
# AWS Auto Scaling
```
#– List Auto Scaling groups
aws autoscaling describe-auto-scaling-groups 

#– Update the desired capacity
aws autoscaling update-auto-scaling-group --auto-scaling-group-name
my-asg --desired-capacity 3

#– Manually scale an Auto Scaling group

aws autoscaling set-desired-capacity --auto-scaling-group-name my-asg
--desired-capacity 2 

```
# AWS Elastic Beanstalk
```
#– List all environments
aws elasticbeanstalk describe-environments

#– Create an application
aws elasticbeanstalk create-application --application-name my-app

#– Deploy a new version
aws elasticbeanstalk update-environment --environment-name my-env
--version-label new-version 

```
# AWS Step Functions
```
#– List all state machines
aws stepfunctions list-state-machines

#– Start a state machine execution
aws stepfunctions start-execution --state-machine-arn
arn:aws:states:region:account-id:stateMachine:MyStateMachine

#– Get execution details
aws stepfunctions describe-execution --execution-arn
arn:aws:states:region:account-id:execution:MyStateMachine:MyExecution 

```
# AWS Glue (ETL Service)
```
#– List all Glue databases
aws glue get-databases 

#– List all tables in a database
aws glue get-tables --database-name my-database 

#– Start a Glue job
aws glue start-job-run --job-name my-glue-job 

```
# AWS SNS (Simple Notification Service)
```
#– List all SNS topics
aws sns list-topics

#– Publish a message to an SNS topic
aws sns publish --topic-arn arn:aws:sns:region:account-id:MyTopic
--message "Test Message"

```
# AWS SQS (Simple Queue Service)
```
#– List all SQS queues
aws sqs list-queues 

#– Send a message
aws sqs send-message --queue-url
https://sqs.region.amazonaws.com/account-id/my-queue --message-body "Hello World" 

```
# AWS Outposts(Managed on-prem cloud/On-premises AWS)
```
# List and Describe Outposts
# List all AWS Outposts
aws outposts list-outposts

# Get details of a specific Outpost
aws outposts get-outpost --outpost-id <outpost-id> 

# List instance types in an Outpost
aws outposts get-outpost-instance-types --outpost-id <outpost-id> 

# Manage Outpost Resources
# List all Outpost sites
aws outposts list-sites

# List Outpost orders
aws outposts list-orders

# List EC2 instances in an Outpost
aws outposts list-outpost-instances --outpost-id <outpost-id>

# Deploy and Configure Outposts
# Order an Outpost
aws outposts create-order --line-items "[{\"catalogItemId\": \"item-id\",
\"quantity\": 1}]" --outpost-id <outpost-id>

# Update Outpost configuration
aws outposts update-outpost --outpost-id <outpost-id> --name <new-name> 

# Networking and Storage on Outposts
# List network devices in an Outpost
aws outposts list-outpost-network-devices --outpost-id <outpost-id>

# List S3 buckets on an Outpost
aws s3 ls --outpost-id <outpost-id> 
aws s3 mb s3://<bucket-name> --outpost-id <outpost-id> # Create an S3 bucket in
Outpost

# Deploy EC2 Instances in Outposts
# Launch an EC2 instance in Outpost
aws ec2 run-instances --image-id <ami-id> --instance-type <type> --subnet-id
<outpost-subnet-id> 

# Automate Outpost Deployments with CloudFormation

# Deploy Outpost resources using CloudFormation
aws cloudformation deploy --template-file outpost-config.yml --stack-name
my-outpost-stack

# Monitor Outposts with CloudWatch
# List Outpost-related CloudWatch metrics
aws cloudwatch list-metrics --namespace AWS/Outposts 

# Monitor CPU usage of Outpost instances
aws cloudwatch get-metric-data --metric-name CPUUtilization --namespace
AWS/Outposts

# Integrate Outposts with CI/CD

# List all CI/CD pipelines
aws codepipeline list-pipelines

# Start a deployment pipeline for Outposts
aws codepipeline start-pipeline-execution --name <pipeline-name> 
aws codebuild start-build --project-name <build-project>

# Start a build process for Outposts workloads
# Deploy an application to an Outpost
aws deploy create-deployment --application-name <app-name>
--deployment-group-name <group-name> --s3-location
bucket=<bucket-name>,key=<app.zip>,bundleType=zip


# Security and Compliance for Outposts
# Create an IAM role for Outpost management
aws iam create-role --role-name <role-name> --assume-role-policy-document
file://policy.json 

# List stored secrets for Outposts
aws secretsmanager list-secrets 

# Retrieve a stored
aws secretsmanager get-secret-value --secret-id <secret-name> 
secret

# List AWS CloudTrail logs for security auditing
aws cloudtrail describe-trails

# Detect security threats related to Outposts
aws guardduty list-findings 

# Delete or Deactivate an Outpost
# Delete an Outpost (must be empty)
aws outposts delete-outpost --outpost-id <outpost-id> 

# Cancel an Outpost order before delivery
aws outposts cancel-order --order-id <order-id> 

```
# AZURE 
```
1. Azure Virtual Machines (VMs)
→ Create a VM
● az vm create --resource-group <rg> --name <vm-name> --image <image>
→ List all VMs
● az vm list -o table
→ Stop a VM
● az vm stop --name <vm-name> --resource-group <rg>
→ Start a VM
● az vm start --name <vm-name> --resource-group <rg>
→ Delete a VM
● az vm delete --name <vm-name> --resource-group <rg>
→ Resize a VM
● az vm resize --name <vm-name> --resource-group <rg> --size <vm-size>
→ Show VM details
● az vm show --name <vm-name> --resource-group <rg>
→ Open a port on a VM
● az vm open-port --port <port-number> --name <vm-name> --resource-group <rg>

```
2. Azure Storage
→ Create a storage account
● az storage account create --name <storage-name> --resource-group <rg>
--location <region>
→ Create a blob container
● az storage container create --name <container-name> --account-name
<storage-name>
→ Upload a file to Blob Storage
● az storage blob upload --file <file-path> --container-name <container-name>
--account-name <storage-name>
→ List blobs in a container
● az storage blob list --container-name <container-name> --account-name
<storage-name>
→ Delete a storage account
● az storage account delete --name <storage-name> --resource-group <rg>

```
3. Azure Kubernetes Service (AKS)
→ Create an AKS cluster
● az aks create --resource-group <rg> --name <aks-name> --node-count
<num> --generate-ssh-keys
→ Get kubeconfig for AKS cluster
● az aks get-credentials --resource-group <rg> --name <aks-name>
→ List AKS cluster nodes
● kubectl get nodes
→ List all pods in AKS
● kubectl get pods -A
→ Deploy an application in AKS
● kubectl apply -f <file.>
→ Remove an application from AKS
● kubectl delete -f <file.>
→ Delete an AKS cluster
● az aks delete --name <aks-name> --resource-group <rg>

```
4. Azure Functions
→ Create an Azure Function App
● az functionapp create --resource-group <rg> --name <app-name>
--consumption-plan-location <region> --runtime <runtime>
→ List all Function Apps
● az functionapp list -o table
→ Delete a Function App
● az functionapp delete --name <app-name> --resource-group <rg>
→ Initialize a local Azure Functions project
● func init <app-name>
→ Create a new function
● func new
→ Run functions locally
● func start
→ Deploy function to Azure
● func azure functionapp publish <app-name>

```
6. Azure Networking
Virtual Network (VNet)
– List VNets
● az network vnet list --output table 
– Create a VNet
● az network vnet create --name myVNet --resource-group myResourceGroup
--subnet-name mySubnet 
Network Security Group (NSG)
– List NSGs
● az network nsg list --output table
- Create an NSG
● az network nsg create --resource-group myResourceGroup --name myNSG –

Load Balancer
– List load balancers
● az network lb list --output table
– Create a Load Balancer
● az network lb create --resource-group myResourceGroup --name myLB
--sku Standard --frontend-ip-name myFrontend --backend-pool-name
myBackendPool 

```
# Azure DevOps (CI/CD)
```
Azure DevOps Projects
– List all DevOps projects
● az devops project list --output table 
– Create a DevOps
● az devops project create --name myDevOpsProject 
project
- Delete a DevOps project 
● az devops project delete --id PROJECT_ID --yes

Azure Repos (Git)
– List all repositories
● az repos list --output table
– Create a new repo
● az repos create --name myRepo
– Delete a repo
● az repos delete --name myRepo --yes 

Azure Pipelines
● az pipelines list --output table – List all pipelines
● az pipelines create --name myPipeline --repository myRepo --branch main
--repository-type gitHub – Create a pipeline
● az pipelines run --name myPipeline – Run a pipeline

```
# Azure Monitor & Logging
```
Azure Monitor
– List metrics for a resource
● az monitor metrics list --resource myResourceID 
– List metric alerts
● az monitor metrics alert list --resource-group myResourceGroup 

Azure Log Analytics
– List log analytics workspaces
● az monitor log-analytics workspace list --output table 
– Create a Log
Analytics workspace
● az monitor log-analytics workspace create --resource-group
myResourceGroup --workspace-name myWorkspace 

```
# Security & Compliance
```
Azure Security Center
– List security assessments
● az security assessment list --output table 
– Enable
auto-provisioning for Security Center
● az security setting update --name AutoProvisioning --value On

Azure Key Vault
– List Key Vaults
● az keyvault list --output table
– Create a Key Vault 
● az keyvault create --name myKeyVault --resource-group myResourceGroup
--location eastus 
– Store a secret in Key Vault
● az keyvault secret set --vault-name myKeyVault --name mySecret --value
"MySecretValue" 
- Retrieve a secret
● az keyvault secret show --vault-name myKeyVault --name mySecret 

```
# Azure Policies & Governance
```
– List all policy assignments
● az policy assignment list --output table
– Assign a policy 
● az policy assignment create --name myPolicyAssignment --policy
myPolicyDefinition 
– Delete a policy assignment
● az policy assignment delete --name myPolicyAssignment

```
# Azure Active Directory (AAD)
```
– List all users
● az ad user list --output table 
– List all groups
● az ad group list --output table 
– List all applications
● az ad app list --output table 
– List all service principals
● az ad sp list --output table

```
# Azure Backup & Recovery
```
– List all backup vaults
● az backup vault list --output table
– Create a backup vault 
● az backup vault create --resource-group myResourceGroup --name
myBackupVault 
- List backup items
● az backup item list --resource-group myResourceGroup --vault-name
myBackupVault --output table 

```
# GCP Cloud
```
1. Compute Engine (VMs)
→ Create a VM instance
● gcloud compute instances create <vm-name> --zone=<zone>
--machine-type=<type> --image=<image>

→ List all VM instances
● gcloud compute instances list

→ Start a VM instance
● gcloud compute instances start <vm-name> --zone=<zone>

→ Stop a VM instance
● gcloud compute instances stop <vm-name> --zone=<zone>

→ Delete a VM instance
● gcloud compute instances delete <vm-name> --zone=<zone>

→ SSH into a VM instance
● gcloud compute ssh <vm-name> --zone=<zone>

→ Open a specific port
● gcloud compute firewall-rules create <rule-name> --allow tcp:<port>

```
# Google Kubernetes Engine (GKE)
```
→ Create a GKE cluster
● gcloud container clusters create <cluster-name> --num-nodes=<num>
--zone=<zone>

→ Get credentials for the GKE cluster
● gcloud container clusters get-credentials <cluster-name> --zone=<zone>

→ List cluster nodes
● kubectl get nodes

→ List all running pods
● kubectl get pods -A

→ List all running pods
● kubectl get pods -A

→ Deploy an application to GKE
● kubectl apply -f <file.>

→ Remove an application from GKE
● kubectl delete -f <file.>

→ Delete a GKE cluster
● gcloud container clusters delete <cluster-name> --zone=<zone>

```
# Cloud Run (Serverless Containers)
```
→ Deploy an application to Cloud Run
● gcloud run deploy <service-name> --image=<gcr.io/project/image>
--platform=managed --region=<region> --allow-unauthenticated

→ List all deployed Cloud Run services
● gcloud run services list

→ Update Cloud Run service to the latest image
● gcloud run services update-traffic <service-name> --to-latest

→ Delete a Cloud Run service
● gcloud run services delete <service-name>

→ Set environment variables in a Cloud Run service
● gcloud run services update <service-name> --set-env-vars
VAR_NAME=value

```
# Google Cloud Storage (GCS)
```
– List all storage buckets
● gcloud storage buckets list 

– Create a storage bucket
● gcloud storage buckets create my-bucket --location US 
– Upload a file
● gcloud storage cp file.txt gs://my-bucket/ 
– Delete a file
● gcloud storage rm gs://my-bucket/file.txt 
– Delete a storage bucket
● gcloud storage buckets delete my-bucket 

```
# Google Cloud IAM (Identity & Access Management)
```
● gcloud iam roles list – List all IAM roles
● gcloud iam service-accounts list – List all service accounts
● gcloud projects add-iam-policy-binding PROJECT_ID
--member=user:EMAIL --role=roles/editor – Assign a role to a user
● gcloud projects remove-iam-policy-binding PROJECT_ID
--member=user:EMAIL --role=roles/editor – Remove a role from a user

```
Google Cloud SQL (Managed Database Service)
● gcloud sql instances list – List all Cloud SQL instances
● gcloud sql instances create my-db --tier=db-f1-micro --region=us-central1 –
Create a Cloud SQL instance
● gcloud sql instances start my-db – Start a Cloud SQL instance
● gcloud sql instances stop my-db – Stop a Cloud SQL instance
● gcloud sql instances delete my-db – Delete a Cloud SQL instance

```
# Google Cloud Build (CI/CD) 
```
● gcloud builds list – List all Cloud Build runs
● gcloud builds submit --tag gcr.io/PROJECT_ID/my-app – Build and push an
image
● gcloud builds triggers list – List Cloud Build triggers

```
Google Cloud Deploy (CI/CD)
● gcloud deploy releases list --delivery-pipeline=my-pipeline – List
deployment releases
● gcloud deploy rollouts list --release=my-release
--delivery-pipeline=my-pipeline – List rollouts
```
# Google Cloud Logging & Monitoring
```
Cloud Logging
● gcloud logging logs list – List available logs
● gcloud logging read "resource.type=gce_instance" --limit 10 – Read VM
logs


Cloud Monitoring
● gcloud monitoring metrics list – List available monitoring metrics
● gcloud monitoring dashboards list – List all dashboards


```
# Google Cloud Networking
```
VPC (Virtual Private Cloud)
● gcloud compute networks list – List VPC networks
● gcloud compute networks create my-vpc --subnet-mode=custom – Create a
VPC network

Firewall Rules
● gcloud compute firewall-rules list – List firewall rules
● gcloud compute firewall-rules create allow-ssh --network=my-vpc
--allow=tcp:22 – Allow SSH access

Load Balancers
● gcloud compute forwarding-rules list – List all load balancers

```
# Google Cloud Security
```
Cloud Identity-Aware Proxy (IAP)
● gcloud iap web list – List IAP-secured applications
● gcloud iap settings get --resource-type=app-engine – Get IAP settings

Cloud Key Management Service (KMS)
● gcloud kms keyrings list --location global – List key rings
● gcloud kms keys list --keyring my-keyring --location global – List
encryption keys

```
Google Artifact Registry
● gcloud artifacts repositories list – List all Artifact Repositories
● gcloud artifacts repositories create my-repo --repository-format=docker
--location=us-central1 – Create a Docker registry

```
# Google Cloud Pub/Sub Messaging 
```
● gcloud pubsub topics list – List all Pub/Sub topics
● gcloud pubsub topics create my-topic – Create a topic

● gcloud pubsub subscriptions list – List all subscriptions
● gcloud pubsub subscriptions create my-sub --topic=my-topic – Create a
subscription

```
Google Cloud Backup & Disaster Recovery
● gcloud backup vaults list – List all backup vaults
● gcloud backup policies list – List backup policies

```
Google Cloud Policies & Governance
● gcloud policy-tags list --location=us – List policy tags
● gcloud resource-manager org-policies list – List all organizational policies
```
Google Cloud Scheduler (Cron Jobs)
● gcloud scheduler jobs list – List all scheduled jobs
● gcloud scheduler jobs create http my-job --schedule="0 * * * *"
--uri=https://example.com/cron – Create a scheduled HTTP job

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