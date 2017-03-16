# SAP Hana Dev/Test ARM Templates
ARM templates for SAP Hana Dev/Test environment.

## Deployment Instructions
### PowerShell
1. Open **.\deploymentParameters\virtualNetwork.Parameters.json**
2. Replace the IP address in `mgmtSubnetNsgSourceAddressPrefix` with your IP address.
  The ARM template will whitelist this IP address in the *mgmt* subnet to allow SSH connections to the jumpbox (bastion host).
3. Open a PowerShell console.
```PowerShell
# Authenticate to Azure Subscription
Login-AzureRmAccount

# Deploy 
.\Deploy-AzureResourceGroup.ps1 -ResourceGroupLocation westus
