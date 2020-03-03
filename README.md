# NDCDevOpsWorkshop

## Summary

The purpose of this repository and file is to take you through the "Turbocharging your Azure DevOps experience with Octopus Deploy" Workshop scheduled for 11th & 12th March in Oslo, Norway.

This session will be led by a Continuous Delivery Archtect [Derek Campbell](https://twitter.com/DevOpsDerek) from [Octopus Deploy](https://octopus.com/), and Founder and Owner of Octopus Deploy [Paul Stovell](https://twitter.com/paulstovell).

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

## Octopus Cloud Sign-up

The first thing we will do, is sign-up for the free Cloud Starter edition for each attendee.

* Browse to <https://octopus.com/>
* Click Get Started
* Register
* Input URL, Select "West Europe" Region,Company, Name, Email & Password
* Wait for it to spin-up & sign in.
* Take note of URL

## Azure DevOps Sign-up

We will now sign up for an Azure DevOps account, Organization & Project

* Browse to <http://dev.azure.com/>
* Select Start Free
* Sign-in with an account that has no Azure DevOps Organizations
* Create Organization, Select Organization Name & Select West Europe

## Integrating Azure DevOps & Octopus Deploy

* Generate API Key (Class led Instructions provided)
* Generate Azure Service Principal (Class led Instructions provided)
* Note Down API Key & ASP Details
* Install Octopus Deploys Azure DevOps extension in Azure DevOps (Class led Instructions provided)
* Set up Service Connection to your Octopus Cloud Instance (Class led Instructions provided)

## OctoFX Background

OctoFX is a sample application, built to demonstrate how a multi-tier application can be deployed using Octopus Deploy.

The application consists of four major components:

* Trading Website
A customer-facing ASP.NET MVC website, where customers trade currencies. Customers can register, login, manage their beneficiary account details, get quotes, and book deals.
* Dealer Portal
An ASP.NET MVC website used by the dealers to adjust the rates offered to customers.
* Deal Settlement Service
A .NET Windows Service that simulates the bank reconcilation and deal settlement process. It checks whether the OctoFX clearing accounts have received funds for any pending deals, and then initiates the transfer when deals are ready to be settled.

A SQL Server database underpins the system.

### Pipeline

![CI/CD Pipeline](/Images/pipeline.png)

### Development

![Development Infrastructure](/Images/dev.png)

### Test

![Test Infrastructure](/Images/test.png)

### Production

![Production Infrastructure](/Images/prod.png)

## Wednesday 11th March Afternoon Session

## Azure Sign-up

## Deploying Azure Infrastructure

## Adding Infrastructure to Octopus Deploy

## Create Deployment Process in Octopus Deploy

## Thursday 12th March Morning Session

## Create Build & Release in Azure DevOps

## Packaging Applications

## Full Deployment

## Thursday 12th March Afternoon Session

## Channels

## LifeCycles

## Multi-Tenancy

## Runbooks

## Spaces

## Common Deployment Patterns

### Blue/Green

### Red/Black

### Canary Deployments

## Octopus & Azure DevOps Administration

## Wrap-up & Feedback