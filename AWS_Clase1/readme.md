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