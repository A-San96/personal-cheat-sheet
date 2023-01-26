<a href="../README.md">
<button>⬅Back</button>
</a>

# Azure CLI Cheat sheet

## Basic command

```bash
# Connect to azure
az login

# Disconnect to azure
az logout

## List subscription
az account list -o table

## Change subscription
az account set -s <subs-id>
```

## Virtual Machine (VM)
Docs for `az vm`: [click here](https://learn.microsoft.com/en-us/cli/azure/vm?view=azure-cli-latest)

```bash
# List VM
az vm list -o table

# Start VM
az vm start -g <rg-name> -n <vm-name>

# Restart VM
az vm restart -g <rg-name> -n <vm-name>

# Stop VM
az vm stop -g <rg-name> -n <vm-name>

# Delete VM
az vm delete -g <rg-name> -n <vm-name>
```