# NDCDevOpsWorkshop Azure Infrastructure

## OctoFX Background

[OctoFX](https://github.com/OctopusSamples/OctoFX) is a sample application built to demonstrate how a multi-tier application is deployed using Octopus Deploy.

The application consists of three major components:

* Trading Website - A customer-facing ASP.NET MVC website, where customers trade currencies. Customers can register, login, manage their beneficiary account details, get quotes, and book deals.
* Deal Settlement Service - A .NET Windows Service that simulates the bank reconciliation and deals settlement process. It checks whether the OctoFX clearing accounts have received funds for any pending deals, and then initiates the transfer when deals are ready to be settled.
* A SQL Server database underpins the system.

## Pipeline

We will set up the following pipeline for OctoFX, using Octopus Deploy & Azure DevOps, deploying to Azure Infrastructure.

![CI/CD Pipeline](/Images/pipeline.png)

## Infrastructure Overview

As a summary, we will deploy:

* 4 x Azure Web Apps (1 for Development, 1 for Test, and 2 for Production).
* 1 x SQL Server for all environments.
* 1 x Jump Box for all environments.
* 1 x Windows Server for OctoFX Window Services for all environments.

The SQL Server, Jump Box, & Windows Services Server are all shared between environments to keep the hosting costs low.

## Development

For the development environment, we will deploy:

* 1 x Azure Web App for Development.
* 1 x SQL Database for Development.
* 1 x Windows Service for Development.
* 1 x Jump Box (For security & SQL Deployments).

![Development Infrastructure](/Images/dev.png)

## Test

For the test environment, we will deploy:

* 1 x Azure Web App for Test.
* 1 x SQL Database for Test.
* 1 x Windows Service for Test.
* 1 x Jump Box (For security & SQL Deployments).

![Test Infrastructure](/Images/test.png)

## Production

For the development environment, we will deploy:

* 2 x Azure Web Apps for Production.
* 1 x SQL Database for Production.
* 1 x Windows Service for Production.
* 1 x Jump Box (For security & SQL Deployments).

![Production Infrastructure](/Images/prod.png)

## Azure Sign-up

You will need an email address that is not tied to an existing Azure subscription. If you need an email address to sign up, you can create one on gmail.com, outlook.com, or if you ask the workshop host, they can provide you with one.

* Browse to <https://azure.microsoft.com/en-gb/free/>.
* Go through the sign-up process.
* You should have access to 12 months of free services, £150 credit to use in 30 days, and access to 25+ free Services.
* Save the details.

## Deploying Azure Infrastructure (Class led instructions provided)

This section will be carried out as Instructor-led training.

### What are ARM Templates

An Azure Resource Manager(ARM) template is a JavaScript Object Notation (JSON) file that defines the infrastructure and configuration for your project.

With more companies moving to the cloud, many teams have adopted agile development methods. These teams iterate quickly. They need to deploy their solutions to the cloud repeatedly and know their infrastructure is in a reliable state. As infrastructure has become part of the iterative process, the division between operations and development has disappeared. Teams need to manage infrastructure and application code through a unified process.

To meet these challenges, you can automate deployments and adopt the practice of infrastructure as code.

In code, you define the infrastructure that needs to be deployed. The infrastructure code becomes part of your project. Just like the application code, you store the infrastructure code in a source repository and version it, and anyone on your team can run the code and deploy similar environments.

To implement infrastructure as code for your Azure solutions, use Azure Resource Manager templates.

The template is a JavaScript Object Notation (JSON) file that defines the infrastructure and configuration for your project. The template uses declarative syntax, which lets you state what you intend to deploy without having to write the sequence of programming commands to create it.

In the template, you specify the resources to deploy and the properties for those resources.

## Adding Infrastructure to Octopus Deploy

This section of the workshop will be led by a presentation, so please follow on-screen.

* Create 4 Web Apps using ARM Template. (1 x Development, 1 x Test & 2 x Production).
* Create 1 Bastion box using Server ARM Template.
* Create 1 SQL Server using SQL ARM Template.
* Create 1 Windows Service Server with Server ARM Template.

## Infrastructure Tips & Instructions

All of the following will be carried out by class led instructions:

* Turn on auto-shutdown on Azure VM's to reduce costs.
* Get Web Apps IP addresses in properties, and add this and the IP from Windows Service Server to be allowed to connect to port 1433 on the SQL Server.
* Turn on Windows & SQL Authentication on SQL Server.
* Allow RDP on SQL Server to just the Bastion Box, and connect into SQL Server.
* Install [Tentacles](https://octopus.com/downloads) on Bastion box and Windows Services Server, and add to Octopus Cloud.
* Add the environments Development, Test, & Production to Octopus Cloud.
* Add infrastructure to Octopus Cloud instance.
* Tag Azure Web Apps with `OctoFX-Web`.
* Tag Bastion Box with `OctoFX-Bastion`.
* Tag Windows Service Server with `OctoFX-RateSvc`.

## Create the Deployment Process in Octopus Deploy

This section of the workshop will be led by a presentation, so please follow on-screen. You can also see OctoFX being configured in Octopus Deploy on [YouTube](https://www.youtube.com/watch?v=6DsJvtTcGMc).

* Create Development, Test, & Production environments (if not already done).
* Create OctoFX project.
* Create OctoFX variables.
* Create OctoFX variable for connection string (Server=#{OctoFX.Database.Server};Database=#{OctoFX.Database.Name};User ID=#{OctoFX.Database.User};Password=#{OctoFx.Database.Password};).
* Create OctoFX deployment process.

Your OctoFX deployment process should look something like:

![It should look something like](/Images/octopusoctofx.png)