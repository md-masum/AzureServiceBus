# Azure Service Bus

## Sign in to Azure
1. Launch the Azure Cloud Shell and select Bash and the environment.
2. Create variables used in the Azure CLI commands. Replace <myLocation> with a region near you.
	```Bash
	myLocation=<myLocation>
	myNameSpaceName=<myNameSpageName>
	```

## Create Azure resources
1. Create a resource group to hold the Azure resources you're creating.
	```Bash
	az group create --name <ResourceGroupName> --location $myLocation
	```
2. Create a Service Bus messaging namespace. The following command creates a namespace using the variable you created earlier. The operation takes a few minutes to complete.
	```Bash
	az servicebus namespace create \
		--resource-group <ResourceGroupName> \
		--name $myNameSpaceName \
		--location $myLocation
	```
3. Create a Service Bus queue
	```Bash
	az servicebus queue create --resource-group <ResourceGroupName> \
		--namespace-name $myNameSpaceName \
		--name az204-queue
	```

## Retrieve the connection string for the Service Bus Namespace
1. Open the Azure portal and navigate to the created resource group.

2. Select the resource you created.

3. Select Shared access policies in the Settings section, then select the RootManageSharedAccessKey policy.

4. Copy the Primary Connection String from the dialog box that opens up and save it to a file, or leave the portal open and copy the key when needed.

