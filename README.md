# SAP Hana Dev/Test ARM Templates
ARM templates for SAP Hana Dev/Test environment.

These templates assume you have an existing virtual network already deployed and a Puppet master server deployed in the virtual network.  These templates deploy just the SAP ERP and SAP Hana DB virtual machines.

## Deployment Instructions
### PowerShell
1. Open **.\deploymentParameters\appsTier.Parameters.json**
2. Replace the values in the following properties to match your environment:
    * `virtualNetworkResourceGroupName` : The name of the __resource group__ that contains the virtual network you want the SAP ERP virtual machine deployed in.
    * `virtualNetworkName` : The name of the virtual network.
    * `subnetName` : The name of the subnet where you want the SAP ERP virtual machine deployed.
    * `privateIpAddresses` :The private IP addresses to assign to the network interface cards (NICS) attached to the SAP ERP virtual machine.  You must specify two private IP addresses from the subnet address range.
    * `puppetServerIpAddress` : The private IP address of the Puppet Server virtual machine.
4. (optional) You can change other properties, such as vmName, vmSize, image, etc. to customize the deployment to your environment.  
5. Save the changes.
6. Open **.\deploymentParameters\dataTier.Parameters.json**
7. Repeat steps 2 through 4 for the SAP Hana DB virtual machine.
8. Open a PowerShell console.
```PowerShell
# Authenticate to Azure Subscription
Login-AzureRmAccount

# Deploy 
.\Deploy-AzureResourceGroup.ps1 -ResourceGroupLocation westus
