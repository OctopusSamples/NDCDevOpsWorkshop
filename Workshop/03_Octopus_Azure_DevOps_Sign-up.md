# NDCDevOpsWorkshop Octopus & Azure DevOps Sign-up

## Octopus Cloud Sign-up

The first thing we will do is sign-up for the free Cloud Starter edition for each attendee. You can get more details on [Octopus.com](https://octopus.com/docs/octopus-cloud).

* Browse to <https://octopus.com/>
* Click Get Started
* Register
* Input URL, Select the "West Europe" Region, Company, Name, Email & Password
* Wait for it to spin-up & sign in.
* Take note of URL

## Azure DevOps Sign-up

We will now sign up for an Azure DevOps account, Organization & Project. You can get more details at [Microsoft Docs](https://docs.microsoft.com/en-us/azure/devops/user-guide/sign-up-invite-teammates?view=azure-devops).

* Browse to <http://dev.azure.com/>
* Select Start Free
* Sign-in with an account that has no Azure DevOps Organizations (You will need to set up a Microsoft account for this)
* Create Organization, Select Organization Name & Select West Europe
* Create OctoFX Project and leave blank
* Take note of the URL

## Integrating Azure DevOps & Octopus Deploy

* [Generate an Octopus API Key](https://octopus.com/docs/octopus-rest-api/how-to-create-an-api-key) (Class led instructions provided).
* [Generate Azure Service Principal](https://octopus.com/docs/infrastructure/deployment-targets/azure#create-service-principal-account-in-azure) (Class led instructions provided).
* Note the API Key & Azure Service Principal details.
* Set up Azure Service Principal in Octopus (Class led instructions provided. It will likely fail validation if created less than 15 minutes ago - Try again at least 15 minutes after you created it).
* Install [Octopus Deploy's Azure DevOps extension](https://octopus.com/downloads) in Azure DevOps (Class led instructions provided).
* Set up Service Connection to your Octopus Cloud instance (Class led instructions provided).