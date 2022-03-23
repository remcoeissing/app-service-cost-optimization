# App Serivce Cost Optimization

Many teams are leveraging App Services for hosting their sites, APIs etc..

## Empty App Service Plans

By far the easiest way that organizations can save money on App Services is by getting rid of App Service Plans that are empty. It's a misconception that you are billed on the App Service / website, the actual billing occurs on the App Service Plan hosting your website. A single App Service Plan can host 1 or multiple sites, depending on the selected size. Having an App Service Plan hosting 0 websites is not good value for money, you pay without using it for anything useful. I've ran across this scenario at many customers, where usually the App Service hosted on the App Service Plan got removed and the team was not aware. In one case the App Service Plan was using a P1V3 plan and running 3 instances, equating to around 638 Euros every month.

## Optimize App Service Plans

App Service Plans have different SKUs, there are cases where a newer version of an App Service Plan can offer similar or better performance. This performance will be achieved with the similar or even lower costs. 

## Installation

The workbook can be installed by deploying the ARM template into your subscription.

```powershell
$parameters = @{
    workbookDisplayName = 'App Service Plan - Cost Optimization'
    workbookSourceId = '/subscriptions/{subscription}/resourcegroups/{resourceGroup}/providers/microsoft.operationalinsights/workspaces/{la-workspace}'
}

New-AzResourceGroupDeployment -Name 'app-service-cost-optimization-workbook' -ResourceGroupName '{resourcegroup}' -TemplateFile .\app-service-cost-workbook.json -TemplateParameterObject $parameters
```