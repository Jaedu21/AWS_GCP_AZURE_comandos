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

# Rabbitmq

```
docker run -d --name server-rabbitmq -p 9000:15672 -p 8080:5672 rabbitmq:management-alpine
```