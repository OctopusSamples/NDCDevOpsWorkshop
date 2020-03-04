# How to use these ARM Templates

## Infrastructure Summary

As a summary, we will be deploying:

* 4 x Azure Web Apps (1 for Development, 1 for Test and 2 for Production)
* 1 x SQL Server for all environments
* 1 x Jump Box for all environments
* 1 x Windows Server for OctoFX Window Services for all environments

## ARM Templates

There are 4 ARM Templates

* [Bastion](https://en.wikipedia.org/wiki/Bastion_host) ARM Template
* Windows Service Server for the Rate Service
* SQL Server with Developer Edition
* Azure Web Apps for OctoFX Website

## Virtual Machine How to Deploy Infrastructure

1. Login to [Azure](https://portal.azure.com/)
2. Select correct Subscription
3. Select `Create a Resource`
4. Input `Template deployment (deploy using custom templates)`
5. Select `Create`
6. Select `Create a Windows Virtual Machine`
7. Create Resource Group
8. Select `Edit Template`
9. Use `template.json` from appropriate ARM Template folder
10. Use `paramaters.json` from appropriate ARM Template folder
11. Enter missing details and complete Infrastructure Deployment

## Azure Web App How To Deploy Infrastructure

1. Login to [Azure](https://portal.azure.com/)
2. Select correct Subscription
3. Select `Create a Resource`
4. Input `Template deployment (deploy using custom templates)`
5. Select `Create`
6. Select `Create a Web App`
7. Create Resource Group
8. Select `Edit Template`
9. Use `template.json` from appropriate ARM Template folder
10. Use `paramaters.json` from appropriate ARM Template folder
11. Enter missing details and complete Infrastructure Deployment.
