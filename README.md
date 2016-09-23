#MC VMSS editor is another VMSS tool modified from gbowerman, this is for Mooncake China Azure only


original repo - > https://github.com/gbowerman/vmssdashboard


----------


## VMSS Editor
GUI editor to view and manage Azure VM Scale Sets. 

![Image of VMSS Editor](./docs/vmsseditor-img.png)

VMSS Editor is a Python/Tkinter script to manage VM Scale Sets. You can use it to:
- View VM Scale Set properties and status.
- Manually scale a VM Scale Set in or out.
- Upgrade the sku of a platform image.
- Upgrade the version of a platform image, or upgrade a custom image.
- Vertically scale - increase of decrease VMs size and roll it out across the set.
- Perform a rolling upgrade of image or VM size across scale set
- Start/Restart/Power off/Stop dealloc a scale set.
- View scale set VMs in a heat map showing fault domains and update domains.
- Operate on fault domains: Upgrade/Reimage/Start/Power off.
- Operate on individual VMs: Upgrade/Reimage/Start/Power off/Delete/Restart/Dealloc. 


### Installation
  1. Install Python 3.x.
  2. Install the azurerm REST wrappers for Microsoft Azure: pip install mcazurerm
  3. Clone or copy this repo. Specifically you need vmsseditor.py, subscription.py, vmss.py, vm.ico and vmssconfig.json.
  4. Register an Azure application, create a service principal and get your tenant id. See "Using vmssdashboard and vmsseditor" below.
  5. Put in values for your application and subscription in vmssconfig.json.
  7. Run: python vmsseditor.py
  
### Using vmsseditor

To use these apps (and in general to access Azure Resource Manager from a program without going through 2 factor authentication) you need to register your application with Azure and create a "Service Principal" (an application equivalent of a user). Once you've done this you'll have 3 pieces of information: A tenant ID, an application ID, and an application secret. You will use these to populate the vmssconfig.json file. For more information on how to get this information go here: [Authenticating a service principal with Azure Resource Manager][service-principle]. See also:
[Azure Resource Manager REST calls from Python][python-auth].

[service-principle]: https://azure.microsoft.com/en-us/documentation/articles/resource-group-authenticate-service-principal/ - make sure you create it with at least "Contributor" rights, not "Reader".
[python-auth]: https://msftstack.wordpress.com/2016/01/05/azure-resource-manager-authentication-with-python

### Performing a rolling upgrade

The rolling upgrade feature was added to show how scale set operations like "manualUpgrade" can be combined to form a semi-automated roll-out of VM updates without disrupting application availability.

Here's a 2 minute video demo of the rolling upgrade feature in action..

[![rolling upgrade demo](https://img.youtube.com/vi/LuEzErQF-Io/0.jpg)](https://www.youtube.com/watch?v=LuEzErQF-Io)
