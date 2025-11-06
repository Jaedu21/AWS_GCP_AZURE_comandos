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


# Rabbitmq

```
docker run -d --name server-rabbitmq -p 9000:15672 -p 8080:5672 rabbitmq:management-alpine
```