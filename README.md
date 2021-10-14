# azure-k8s-notes
Deploying a multi-container application to Azure Kubernetes Services

[Deploying a multi-container application to Azure Kubernetes Services](https://www.azuredevopslabs.com/labs/vstsextend/kubernetes/)

```
version=$(az aks get-versions -l westus  --query 'orchestrators[-1].orchestratorVersion' -o tsv)
```
```
az group create --name akshandsonlab --location westus
```
```
az aks create --resource-group akshandsonlab --name k8sgo --enable-addons monitoring --kubernetes-version $version --generate-ssh-keys --location westus
```

```
az acr create --resource-group akshandsonlab --name k8sgo --sku Standard --location westus
```
```
az aks update -n k8sgo -g akshandsonlab --attach-acr k8sgo
```
```
az sql server create -l westus -g akshandsonlab -n k8sgo -u sqladmin -p P2ssw0rd1234
```

```
az sql db create -g akshandsonlab -s k8sgo -n mhcdb --service-objective S0
```

1. Create Connection 
 
![image](https://user-images.githubusercontent.com/993459/137396438-1261cd42-253a-49c5-9902-3426c37a9703.png)  

![image](https://user-images.githubusercontent.com/993459/137396598-97cb21a1-fa28-463d-b0ca-6f9ba780172f.png)  

