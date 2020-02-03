# Audit and deploy Resource Locks on Resource Groups based on Tags

Deploy Resource Locks CanNotDelete to Resource Groups that have a specific Tag.
Within this Policy, you sepcify the Tag Name and Tag Value that will be used for identifying the Resource Groups to audit and deploy to.

## Try in the Azure Portal

[![Deploy to Azure](http://azuredeploy.net/deploybutton.png)](https://portal.azure.com/#blade/Microsoft_Azure_Policy/CreatePolicyDefinitionBlade/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fstefanrothnet%2Fazure-policy%2Fmaster%2Fdeploy-resourceGroup-resourceLocks%2Fazuredeploy.json)

## Try with PowerShell

````powershell
$definition = New-AzPolicyDefinition -Name "deploy-resourceGroup-resourceLocks" -DisplayName "Audit and deploy Resource Locks on Resource Groups based on Tags" -description "Audits and remediates all Resource Groups that have a specific Tag, for the CanNotDelete Resource Lock." -Policy 'https://raw.githubusercontent.com/stefanrothnet/azure-policy/master/deploy-resourceGroup-resourceLocks/azurepolicy.rules.json' -Parameter 'https://raw.githubusercontent.com/stefanrothnet/azure-policy/master/deploy-resourceGroup-resourceLocks/azurepolicy.parameters.json' -Mode All
$definition
$assignment = New-AzPolicyAssignment -Name <assignmentname> -Scope <scope> -tagName <tagName> -tagValue <tagValue> -PolicyDefinition $definition
$assignment 
````

## Try with CLI

````cli
az policy definition create --name 'deploy-resourceGroup-resourceLocks' --display-name 'Audit and deploy Resource Locks on Resource Groups based on Tags' --description 'Audits and remediates all Resource Groups that have a specific Tag, for the CanNotDelete Resource Lock.' --rules 'https://raw.githubusercontent.com/stefanrothnet/azure-policy/master/deploy-resourceGroup-resourceLocks/azurepolicy.rules.json' --params 'https://raw.githubusercontent.com/stefanrothnet/azure-policy/master/deploy-resourceGroup-resourceLocks/azurepolicy.parameters.json' --mode All

az policy assignment create --name <assignmentname> --scope <scope> --policy "deploy-resourceGroup-resourceLocks" 
````
