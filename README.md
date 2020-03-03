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
* Multi-Tenancy, Channels, Lifecycles & Spaces.
* Common Deployment patterns such as Canary, Blue/Green & Red/Black.

### Who should attend

This workshop is for Developers, Ops and DevOp Engineers starting on their CI/CD journey or for engineers looking for some fresh ideas. Additionally, if you are using an older version of Octopus and want a refresher, then come along.

## 11th March 2020 Morning - Configuration

The first thing we will do this morning is go through the pre-requisites and ensure you have these setup.

### Pre-Requisites

* Free Azure/MSDN Subscription with access to create an Azure Service Principal. A Corporate Subscription is best to be avoided.
* Email address to spin up free Azure DevOps & Octopus instances

### Computer Setup

Attendees will need a laptop with Windows with the following software:

* Visual Studio Code
* MSBuild
* NET Framework 4.6.1+
* GIT

## Wednesday 11th March Morning Session

Welcome to "Turbocharging your Azure DevOps experience with Octopus Deploy" where over the next 2 days, we will setup Azure DevOps, Azure Infrastructure and Octopus Cloud to deploy OctoFX.

### What is Continuous Integration

“Continuous integration (CI) is the practice of merging all developers' working copies to a shared mainline several times a day.”

### What is Continuous Delivery

“Continuous delivery is a software engineering approach in which teams produce software in short cycles, ensuring that the software can be reliably released and deployed at any time. It aims at building, testing, and releasing software with greater speed and frequency.”

### Octopus Cloud Sign-up

The first thing we will do, is sign-up for the free Cloud Starter edition for each attendee. You can get more details on [Octopus.com](https://octopus.com/docs/octopus-cloud)

* Browse to <https://octopus.com/>
* Click Get Started
* Register
* Input URL, Select "West Europe" Region,Company, Name, Email & Password
* Wait for it to spin-up & sign in.
* Take note of URL

### Azure DevOps Sign-up

We will now sign up for an Azure DevOps account, Organization & Project

* Browse to <http://dev.azure.com/>
* Select Start Free
* Sign-in with an account that has no Azure DevOps Organizations
* Create Organization, Select Organization Name & Select West Europe
* Take noe of URL

### Integrating Azure DevOps & Octopus Deploy

* Generate API Key (Class led Instructions provided)
* Generate Azure Service Principal (Class led Instructions provided)
* Note Down API Key & ASP Details
* Install Octopus Deploys Azure DevOps extension in Azure DevOps (Class led Instructions provided)
* Set up Service Connection to your Octopus Cloud Instance (Class led Instructions provided)

### OctoFX Background

OctoFX is a sample application, built to demonstrate how a multi-tier application can be deployed using Octopus Deploy.

The application consists of three major components:

* Trading Website - A customer-facing ASP.NET MVC website, where customers trade currencies. Customers can register, login, manage their beneficiary account details, get quotes, and book deals.
* Deal Settlement Service - A .NET Windows Service that simulates the bank reconcilation and deal settlement process. It checks whether the OctoFX clearing accounts have received funds for any pending deals, and then initiates the transfer when deals are ready to be settled.
* A SQL Server database underpins the system.

### Pipeline

We will set up the following pipeline for OctoFX, using Octopus Deploy & Azure DevOps, deploying to Azure Infrastructure.

![CI/CD Pipeline](/Images/pipeline.png)

### Infrastructure Overview

As a summary we will be deploying:

* 4 x Azure Web Apps (1 for Development, 1 for Test and 2 for Production)
* 1 x SQL Server for all environments
* 1 x Jump Box for all environments
* 1 x Windows Server for OctoFX Window Services for all environments

### Development

For the development environment, we will be deploying

* 1 x Azure Web App for Development
* 1 x SQL Database for Development
* 1 x Windows Service for Development
* 1 x Jump Box (For security & SQL Deployments)

![Development Infrastructure](/Images/dev.png)

### Test

For the test environment, we will be deploying

* 1 x Azure Web App for Test
* 1 x SQL Database for Test
* 1 x Windows Service for Test
* 1 x Jump Box (For security & SQL Deployments)

![Test Infrastructure](/Images/test.png)

### Production

For the development environment, we will be deploying

* 2 x Azure Web Apps for Production
* 1 x SQL Database for Production
* 1 x Windows Service for Production
* 1 x Jump Box (For security & SQL Deployments)

![Production Infrastructure](/Images/prod.png)

## Wednesday 11th March Afternoon Session

### Azure Sign-up

### Deploying Azure Infrastructure

* Turn on auto-shutdown on Azure VM's to save cost

### Adding Infrastructure to Octopus Deploy

This section of the Workshop, will be led by a presentation so please follow on-screen.

### Create Deployment Process in Octopus Deploy

This section of the Workshop, will be led by a presentation so please follow on-screen.

### Thursday 12th March Morning Session

* Turn on Infrastructure if you have shutdown enabled.

### Create Build & Release in Azure DevOps

This section of the Workshop, will be led by a presentation

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

Thanks for spending the last two days with us, we hope you enjoyed the workshop.

We wanted to list a few items for you to consider carrying out at the end of the workshop, to help reduce any cost to you personally.

* Destroy your Infrastructure, as this will continue charging you.
* Keep Azure DevOps, as there should be no cost
* Octopus Cloud will remain free for all of time as long as you have no more than 10 targets.
* For more information on Octopus, check out the [Optimum Setup Guide](https://github.com/OctopusDeploy/OptimumSetupBook)
* Check out the [Octopus documentation](http://octopus.com/docs/)
* Please check out [Octopus Guides](https://octopus.com/docs/guides) where you can select your own CI/CD pipeline and it will generate a video for you on how to set it up.
* For more videos, check out our [YouTube Channel](http://octopus.com/videos)
* Check out our [Events Page](https://octopus.com/events) for upcoming Webinars & Events, and for previously recorded Webinars
* You can find more Octopus Samples on our Octopus Samples hosted Cloud Instance with Guest Authentication [here](http://samples.octopus.app/)
* We have a [Jenkins Sample](https://jenkinssample.octopus.com/) that you can browse.
* We have a [TeamCity Sample](https://teamcitysample.octopus.com/) that you can browse
* You can see an existing build for OctoFX on our [Azure DevOps Sample](https://dev.azure.com/octopussamples/OctoFX)
* Follow us on [Twitter](https://twitter.com/OctopusDeploy)

Can you please take 5 minutes, and help us by filling out this anonymous [feedback form](https://forms.gle/tXi3Vn9n4kPKT5ai7).
