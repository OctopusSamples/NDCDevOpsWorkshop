# NDCDevOpsWorkshop

## Summary

The purpose of this repository and file is to take you through the "Turbocharging your Azure DevOps experience with Octopus Deploy" Workshop scheduled for 11th & 12th March in Oslo, Norway.

This session will be led by a Continuous Delivery Architect [Derek Campbell](https://twitter.com/DevOpsDerek) from [Octopus Deploy](https://octopus.com/), and Founder and Owner of Octopus Deploy [Paul Stovell](https://twitter.com/paulstovell).

![toc]

## Agenda

This workshop will cover core CI/CD concepts and best practices, and review real-world release management and automation problems and how to overcome them using Azure, Azure DevOps, and Octopus Deploy.

### What you will learn

We will start by taking an existing sample repository and get that building locally in Visual Studio. We will then take the application and get it building and testing on Azure DevOps, then configure the Release and lastly pass the artifact through to Octopus Deploy ready for deployment.

You will get hands-on access to provisioning infrastructure on Azure, building an Azure DevOps pipeline & creating an Octopus Cloud instance. You will use all of these tools to configure and prepare a build, test it, create the release and deployment pipeline of a sample application and get you deploying from Dev, through to test and lastly to Production.

The list of topics include:

* Creating Octopus Cloud instance.
* Creating Azure DevOps Project.
* Integrating Azure DevOps & Octopus Deploy.
* Setup Azure Service Principal
* Creating Azure Web Apps & VM's in Azure.
* Adding Infrastructure in Octopus Deploy.
* Creating the Deployment process in Octopus Deploy.
* Creating Build in Azure Pipelines & Test plans in Azure Test Plans.
* Packaging Applications.
* Administration of Azure DevOps & Octopus.
* Runbooks, Multi-Tenancy, Channels, Lifecycles & Spaces.
* Common Deployment patterns such as Canary, Blue/Green & Red/Black.

### Who should attend

This workshop is for Developers, Ops and DevOp Engineers starting on their CI/CD journey or for engineers looking for some fresh ideas. Additionally, if you are using an older version of Octopus and want a refresher, then come along.

## Wednesday 11th March Morning Session

Welcome to "Turbocharging your Azure DevOps experience with Octopus Deploy" where over the next 2 days, we will setup Azure DevOps, Azure Infrastructure and Octopus Cloud to deploy OctoFX.

The first thing we will do this morning is go through the pre-requisites and ensure you have these setup.

### Pre-Requisites

* Free Azure/MSDN Subscription with access to create an Azure Service Principal. A Corporate Subscription is best to be avoided.
* Email address to spin up free Azure DevOps & Octopus instances. (We have some available if you have already used your email for Azure, and Azure DevOps, ask for access to email)

### Computer Setup

Attendees will need a laptop with Windows with the following software:

* Visual Studio Code
* MSBuild
* NET Framework 4.6.1+
* GIT

### What is Continuous Integration

“[Continuous integration](https://en.wikipedia.org/wiki/Continuous_integration) (CI) is the practice of merging all developers' working copies to a shared mainline several times a day.”

### What is Continuous Delivery

“[Continuous delivery](https://en.wikipedia.org/wiki/Continuous_delivery) is a software engineering approach in which teams produce software in short cycles, ensuring that the software can be reliably released and deployed at any time. It aims at building, testing, and releasing software with greater speed and frequency.”

### What is Continuous Deployment

"[Continuous deployment](https://en.wikipedia.org/wiki/Continuous_deployment) (CD) is a software engineering approach in which software functionalities are delivered frequently through automated deployments. CD contrasts with continuous delivery, a similar approach in which software functionalities are also frequently delivered and deemed to be potentially capable of being deployed but are actually not deployed.

### Octopus Cloud Sign-up

The first thing we will do, is sign-up for the free Cloud Starter edition for each attendee. You can get more details on [Octopus.com](https://octopus.com/docs/octopus-cloud)

* Browse to <https://octopus.com/>
* Click Get Started
* Register
* Input URL, Select "West Europe" Region,Company, Name, Email & Password
* Wait for it to spin-up & sign in.
* Take note of URL

### Azure DevOps Sign-up

We will now sign up for an Azure DevOps account, Organization & Project. You can get more details on [Microsoft Docs](https://docs.microsoft.com/en-us/azure/devops/user-guide/sign-up-invite-teammates?view=azure-devops)

* Browse to <http://dev.azure.com/>
* Select Start Free
* Sign-in with an account that has no Azure DevOps Organizations (You will need to setup a Microsoft account for this)
* Create Organization, Select Organization Name & Select West Europe
* Create OctoFX Project and leave blank
* Take note of URL

### Integrating Azure DevOps & Octopus Deploy

* [Generate an Octopus API Key](https://octopus.com/docs/octopus-rest-api/how-to-create-an-api-key) (Class led Instructions provided)
* [Generate Azure Service Principal](https://octopus.com/docs/infrastructure/deployment-targets/azure#create-service-principal-account-in-azure) (Class led Instructions provided)
* Note Down API Key & Azure Service Principal Details
* Set up Azure Service Principal in Octopus (Class led Instructions provided) (It will likely fail validation if created less than 15 minutes ago)
* Install [Octopus Deploys Azure DevOps extension](https://octopus.com/downloads) in Azure DevOps (Class led Instructions provided)
* Set up Service Connection to your Octopus Cloud Instance (Class led Instructions provided)

### OctoFX Background

[OctoFX](https://github.com/OctopusSamples/OctoFX) is a sample application, built to demonstrate how a multi-tier application can be deployed using Octopus Deploy.

The application consists of three major components:

* Trading Website - A customer-facing ASP.NET MVC website, where customers trade currencies. Customers can register, login, manage their beneficiary account details, get quotes, and book deals.
* Deal Settlement Service - A .NET Windows Service that simulates the bank reconcilation and deal settlement process. It checks whether the OctoFX clearing accounts have received funds for any pending deals, and then initiates the transfer when deals are ready to be settled.
* A SQL Server database underpins the system.

## Wednesday 11th March Afternoon Session

### Pipeline

We will set up the following pipeline for OctoFX, using Octopus Deploy & Azure DevOps, deploying to Azure Infrastructure.

![CI/CD Pipeline](/Images/pipeline.png)

### Infrastructure Overview

As a summary we will be deploying:

* 4 x Azure Web Apps (1 for Development, 1 for Test and 2 for Production)
* 1 x SQL Server for all environments
* 1 x Jump Box for all environments
* 1 x Windows Server for OctoFX Window Services for all environments

The SQL Server, Jump Box & Windows Services Server are all shared between environments to keep the hosting costs low.

### Development

For the development environment, we will be deploying:

* 1 x Azure Web App for Development
* 1 x SQL Database for Development
* 1 x Windows Service for Development
* 1 x Jump Box (For security & SQL Deployments)

![Development Infrastructure](/Images/dev.png)

### Test

For the test environment, we will be deploying:

* 1 x Azure Web App for Test
* 1 x SQL Database for Test
* 1 x Windows Service for Test
* 1 x Jump Box (For security & SQL Deployments)

![Test Infrastructure](/Images/test.png)

### Production

For the development environment, we will be deploying:

* 2 x Azure Web Apps for Production
* 1 x SQL Database for Production
* 1 x Windows Service for Production
* 1 x Jump Box (For security & SQL Deployments)

![Production Infrastructure](/Images/prod.png)

### Azure Sign-up

You will need an email address that is not tied to an existing Azure Subscription. If you need an email address to sign up, you can create one on gmail.com, outlook.com or if you ask the workshop host, they can provide you with one.

* Browse to <https://azure.microsoft.com/en-gb/free/>
* Go through Sign-up process
* You should have access to 12 months of free services, £150 credit to use in 30 days, and access to 25+ free Services
* Save details

### Deploying Azure Infrastructure (Class led Instructions provided)

This section will be mostly carried out as Instructor led training.

#### What are ARM Templates

Azure Resource Manager(ARM) template is a JavaScript Object Notation (JSON) file that defines the infrastructure and configuration for your project.

With the companies moving to the cloud, many teams have adopted agile development methods. These teams iterate quickly. They need to repeatedly deploy their solutions to the cloud, and know their infrastructure is in a reliable state. As infrastructure has become part of the iterative process, the division between operations and development has disappeared. Teams need to manage infrastructure and application code through a unified process.

To meet these challenges, you can automate deployments and use the practice of infrastructure as code.

In code, you define the infrastructure that needs to be deployed. The infrastructure code becomes part of your project. Just like application code, you store the infrastructure code in a source repository and version it. Any one on your team can run the code and deploy similar environments.

To implement infrastructure as code for your Azure solutions, use Azure Resource Manager templates.

The template is a JavaScript Object Notation (JSON) file that defines the infrastructure and configuration for your project. The template uses declarative syntax, which lets you state what you intend to deploy without having to write the sequence of programming commands to create it.

In the template, you specify the resources to deploy and the properties for those resources.

### Adding Infrastructure to Octopus Deploy

This section of the Workshop, will be led by a presentation so please follow on-screen.

* Create 4 Web Apps using ARM Template. (1 x Development, 1 x Test & 2 x Production)
* Create 1 Bastion box using Server ARM Template
* Create 1 SQL Server using SQL ARM Template
* Create 1 Windows Service Server with Server ARM Template

### Infrastructure Tips & Instructions

All of the below will be carried out by Class led Instructions.

* Turn on auto-shutdown on Azure VM's to save cost
* Get Web Apps IP addresses in Properties, and add this and IP from Windows Service Server to be allowed to connect to Port 1433 on the SQL Server.
* Turn on Windows & SQL Authentication on SQL Server.
* Allow RDP on SQL Server to just the Bastion Box, and connect in to SQL Server.
* Install [Tentacles](https://octopus.com/downloads) on Bastion box and Windows Services Server and add to Octopus Cloud
* Add Environments Development, Test & Production to Octopus Cloud.
* Add Infrastructure to Octopus Cloud Instance
* Tag Azure Web Apps with "OctoFX-Web
* Tag Bastion Box with "OctoFX-Bastion"
* Tag Windows Service Server with "OctoFX-RateSvc"

### Create Deployment Process in Octopus Deploy

This section of the Workshop, will be led by a presentation so please follow on-screen.

* Create Development, Test & Production Environments (if not already done)
* Create OctoFX Project
* Create OctoFX Variables
* Create OctoFX Deployment Process

![It should look something like](/Images/octopusoctofx.png)

### Thursday 12th March Morning Session

* Turn on Infrastructure if you have shutdown enabled & Run Octopus Health check and confirm all are available.

### Create Build & Release in Azure DevOps

This section of the Workshop, will be led by a presentation.

You should already have Azure DevOps, with an organization and the OctoFX Project from yesterday.

* Browse to <https://dev.azure.com/> and login with details used yesterday.
* Go to Azure Repos and import <https://github.com/OctopusSamples/OctoFX/> into Azure Repos.
* Create Azure Pipeline for OctoFX.

![It should look something like](/Images/azurepipelinesoctofx.png)

* Create Azure Release Pipeline

![Azure Release pipeline should look something like](/Images/azurereleasecreatereleasepipelinesoctofx.png)
![Azure Dev Release pipeline should look something like](/Images/azurereleasedevpipelinesoctofx.png)
![Azure Test Release pipeline should look something like](/Images/azurereleaseptestipelinesoctofx.png)
![Azure Production Release pipeline should look something like](/Images/azurereleasepipeprodlinesoctofx.png)

### Packaging Applications

### Full Deployment

This section of the Workshop, will be led by a presentation so please follow on-screen.

## Thursday 12th March Afternoon Session

### Channels

You can read more [Channels](https://octopus.com/docs/deployment-process/channels)

### Lifecycles

You can read more [LifeCycles](https://octopus.com/docs/deployment-process/lifecycles)

### Multi-Tenancy

You can read more [Multi-Tenancy](https://octopus.com/docs/deployment-patterns/multi-tenant-deployments)

### Runbooks

You can read more about [Runbooks](https://octopus.com/docs/operations-runbooks)

### Spaces

With Spaces you can partition your Octopus Deploy Server so that each of your teams can only access the projects, environments, and infrastructure they work with from the spaces they are members of. Users can be members of multiple teams and have access to multiple spaces, but the entities and infrastructure they work with will only be available in the space it is assigned to.

You can read more [here](https://octopus.com/docs/administration/spaces)

### Common Deployment Patterns

#### Blue/Green

You can read more [here](https://octopus.com/docs/deployment-patterns/blue-green-deployments)

#### Red/Black

You can read more about Red vs Black [here](https://octopus.com/blog/blue-green-red-black)

#### Canary Deployments

You can read more about [Canary Deployments](https://octopus.com/docs/deployment-patterns/canary-deployments)

### Octopus & Azure DevOps Administration

* [Auditing](https://octopus.com/docs/administration/managing-users-and-teams/auditing)
* [External Authentication Providers](https://octopus.com/docs/administration/authentication)
* [Users/Teams/Permissions](https://octopus.com/docs/administration/managing-users-and-teams)
* [Upgrading Octopus](https://octopus.com/docs/administration/upgrading)
* [Retention Policies](https://octopus.com/docs/administration/retention-policies)
* [Cloud vs On-Premise](https://octopus.com/docs/octopus-cloud)

## Wrap-up & Feedback, and Resources

Thanks for spending the last two days with us, we hope you enjoyed the workshop and learned a lot!

### Recommendations

* Destroy your Infrastructure, as this will continue charging you.
* Keep Azure DevOps, as there should be no cost
* Octopus Cloud will remain free for all of time as long as you have no more than 10 targets.

### Octopus Resources

* For more information on Octopus, check out the [Optimum Setup Guide](https://github.com/OctopusDeploy/OptimumSetupBook)
* [Octopus documentation](http://octopus.com/docs/)
* [Octopus Guides](https://octopus.com/docs/guides) where you can select your own CI/CD pipeline and it will generate a video for you on how to set it up.
* [Octopus YouTube Channel](http://octopus.com/videos)
* [Octopus Events Page](https://octopus.com/events) for upcoming Webinars & Events, and for previously recorded Webinars
* [Sample Octopus Instance](http://samples.octopus.app/)
* [Octopus Jenkins Sample](https://jenkinssample.octopus.com/).
* [Octopus TeamCity Sample](https://teamcitysample.octopus.com/)
* [Azure DevOps OctoFX Sample](https://dev.azure.com/octopussamples/OctoFX)
* [Octopus Twitter](https://twitter.com/OctopusDeploy)

### Azure DevOps Resources

* [Microsoft Learn](https://docs.microsoft.com/en-us/learn/) has some great resources for Azure DevOps & Azure
* [Azure Quickstart Templates](https://azure.microsoft.com/en-gb/resources/templates/) and [Github](https://github.com/Azure/azure-quickstart-templates) are great resources for Quickstart ARM Templates
* Azure DevOps certification [exam detail page](https://docs.microsoft.com/en-us/learn/certifications/azure-devops).
* Azure Administrator exam details on this [page](https://docs.microsoft.com/en-gb/learn/certifications/azure-administrator)
* [Azure Docs](https://docs.microsoft.com/en-gb/azure/)
* [Azure DevOps Docs](https://docs.microsoft.com/en-gb/azure/devops/)
* [Channel 9 video content](https://channel9.msdn.com/)

Can you please take 5 minutes, and help us by filling out this anonymous [feedback form](https://forms.gle/tXi3Vn9n4kPKT5ai7).
