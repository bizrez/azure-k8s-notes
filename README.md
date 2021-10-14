# azure-k8s-notes
Deploying a multi-container application to Azure Kubernetes Services

> dilemma - Running a company subscription that does not allow me to use Active Directory for applications and configuration of Azure resources.
  
> solution - Go native connection. Hooked up the pipeline with a connection.   

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

 ![image](https://user-images.githubusercontent.com/993459/137400802-f57b8a2c-dfee-48b2-b9ee-0617fe0bd005.png) 
 
 ![image](https://user-images.githubusercontent.com/993459/137400279-e4759344-4dc9-4657-b83f-e76bcacfa89d.png)  
 
 


![image](https://user-images.githubusercontent.com/993459/137397895-020bb245-2da5-4187-91b3-c83d4217020d.png) 

![image](https://user-images.githubusercontent.com/993459/137397936-48d695a9-33ca-45cc-b17b-2257816eddf5.png)

2. Add containerRegistry to the variables

