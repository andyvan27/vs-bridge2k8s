# vs-bridge2k8s
 Visual Studio Bridge to Kubernetes

## Install Bridge to Kubernetes Extension
- For Visual Studio 2022, go to menu Extensions | Manage Extensions, search for Bridge to Kubernetes and install it.
- For Visual Studio Code, go to extensions, search for Bridge to Kubernetes and install it.

## Get code
- Follow steps of this page: https://learn.microsoft.com/en-us/visualstudio/bridge/bridge-to-kubernetes-vs?view=vs-2019 to get sample code and deploy to an AKS cluster

### Deploy to AKS
- Create AKS cluster
```
az login
az account list
az account set --subscription <subscription id or name> --> az account set --subscription "HSFTRMS Sponsor Sub"
az group create --name <resource group name> --location <region name> --> az group create --name ank8s --location australiasoutheast
az aks create -g <resource group name> -n <aks cluster name> --enable-managed-identity --node-count 2  --node-vm-size Standard_B2S --generate-ssh-keys --> az aks create -g ank8s -n ank8s --enable-managed-identity --node-count 1  --node-vm-size Standard_B2S --generate-ssh-keys
az aks get-credentials --resource-group <resource group name> --name <aks cluster name> --> az aks get-credentials --resource-group ank8s --name ank8s

kubectl cluster-info
kubectl create namespace todo-app
kubectl apply -n todo-app -f deployment.yaml
kubectl get service -n todo-app frontend
```
- Follow steps on code page to attach a breakpoint in database-api C# project and try to hit it.
- Follow this page to debug node js code in VS Code: https://learn.microsoft.com/en-us/visualstudio/bridge/bridge-to-kubernetes-sample

## References
- Video: https://www.youtube.com/watch?v=FRpUJoDdI1o
