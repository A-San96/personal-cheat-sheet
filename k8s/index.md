<a href="../README.md">
<button>⬅Retour</button>
</a>

# kubernetes cheat sheet

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