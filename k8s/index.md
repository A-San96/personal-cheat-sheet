<a href="../README.md">
<button>⬅Back</button>
</a>

# kubernetes cheat sheet
This my personal cheatsheet but you can check the official cheatsheet here choose your prefered language:
- [Kubernetes Official Cheetsheet in french](./cheat-sheet-k8s-fr.md)
- [Kubernetes Official Cheetsheet in english](./cheatsheet-k8s-en.md)
## Clusters, Contexts and Users
- View
```bash
# List all clusters
kubectl config get-clusters
# List all contexts
kubectl config get-contexts
# List all users
kubectl config get-users
```
- Switch to another context
```bash
kubectl config use-context <NAME OF CONTEXT>
```
- Remove
```bash
#### First Method for Cluster and context ####
kubectl config delete-cluster <NAME OF CLUSTER>
kubectl config delete-context <NAME OF CONTEXT>

#### Second Method for Cluster and context ####
kubectl config unset clusters.<NAME OF CLUSTER>
kubectl config unset contexts.<NAME OF CONTEXT>

# Remove user
kubectl config unset users.<USER>


```

## Horizontal Pod Autoscaler
A deployment feature that allows additional pods to be created when a CPU usage threshold is reached.
Commands :
- Create HPA
```bash
kubectl autoscale deployment <NAME> --cpu-percent=<CPU_PERCENTAGE> --min=<MIN_REPLICAS> --max=<MAX_REPLICAS>
```
- View HPA
```bash
kubectl get hpa
```