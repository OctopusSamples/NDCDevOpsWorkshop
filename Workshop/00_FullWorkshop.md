# NDCDevOpsWorkshop

## Summary

The purpose of this repository and file is to take you through the "Turbo-charging your Azure DevOps experience with Octopus Deploy" workshop scheduled for the 11th & 12th March in Oslo, Norway.

This workshop will be led by Continuous Delivery Architect [Derek Campbell](https://twitter.com/DevOpsDerek) from [Octopus Deploy](https://octopus.com/).

![toc]

## Agenda

This workshop covers core CI/CD concepts and best practices, reviews real-world release management and automation problems, and how to overcome them using Azure, Azure DevOps, and Octopus Deploy.

### What you will learn

We will take an existing application and get it building and testing on Azure DevOps, then configure the release, and lastly, pass the artifact through to Octopus Deploy ready for deployment.

You will get hands-on access provisioning infrastructure on Azure, building an Azure DevOps pipeline and creating an Octopus Cloud instance. You will use all of these tools to configure and prepare a build, test it, create the release and deployment pipeline of a sample application, and deploy from Dev to Test, and lastly to Production.

The list of topics includes:

* Creating Octopus Cloud instance.
* Creating Azure DevOps project.
* Integrating Azure DevOps & Octopus Deploy.
* Set up Azure Service Principal.
* Creating Azure Web Apps & VMs in Azure.
* Adding infrastructure in Octopus Deploy.
* Creating the deployment process in Octopus Deploy.
* Creating build in Azure Pipelines & test plans in Azure Test Plans.
* Packaging applications.
* Administration of Azure DevOps & Octopus.
* Runbooks, Multi-Tenancy, Workers, Channels, Lifecycles, & Spaces.
* Common Deployment patterns such as Canary, Blue/Green, & Red/Black.

### Who should attend

This workshop is for Developers, Ops, and DevOp Engineers starting on their CI/CD journey or for engineers looking for some fresh ideas. This is also ideal for anybody using an older version of Octopus who wants a refresher.

## Wednesday 11th March Morning Session

Welcome to "Turbo-charging your Azure DevOps experience with Octopus Deploy." Over the next two days, we will setup Azure DevOps, Azure infrastructure, and Octopus Cloud to deploy OctoFX.

The first thing we will do this morning is to go through the pre-requisites and ensure you have these setup.

### Pre-Requisites

* Free Azure/MSDN subscription with access to create an Azure Service Principal. A Corporate subscription is best avoided.
* Email address to spin up free Azure DevOps & Octopus instances. (We have some available if you have already used your email for Azure and Azure DevOps, ask for access to email).

### Computer Setup

Attendees will need a laptop with Windows and the following software:

* Visual Studio Code
* MSBuild
* NET Framework 4.6.1+
* GIT
* Remote Desktop Software like [Microsoft's Remote Desktop Connection Manager](https://www.microsoft.com/en-gb/download/details.aspx?id=44989)

### What is Continuous Integration

"[Continuous integration](https://en.wikipedia.org/wiki/Continuous_integration) (CI) is the practice of merging all developers' working copies to a shared mainline several times a day."

### What is Continuous Delivery

"[Continuous delivery](https://en.wikipedia.org/wiki/Continuous_delivery) is a software engineering approach in which teams produce software in short cycles, ensuring that the software can be reliably released and deployed at any time. It aims at building, testing, and releasing software with greater speed and frequency."

### What is Continuous Deployment

"[Continuous deployment](https://en.wikipedia.org/wiki/Continuous_deployment) (CD) is a software engineering approach in which software functionalities are delivered frequently through automated deployments. Continuous deployment contrasts with continuous delivery, a similar approach in which software functionalities are also regularly delivered and deemed to be capable of being deployed but are not deployed.

### Octopus Cloud Sign-up

The first thing we will do is sign-up for the free Cloud Starter edition for each attendee. You can get more details on [Octopus.com](https://octopus.com/docs/octopus-cloud).

* Browse to <https://octopus.com/>
* Click Get Started
* Register
* Input URL, Select the "West Europe" Region, Company, Name, Email & Password
* Wait for it to spin-up & sign in.
* Take note of URL

### Azure DevOps Sign-up

We will now sign up for an Azure DevOps account, Organization & Project. You can get more details at [Microsoft Docs](https://docs.microsoft.com/en-us/azure/devops/user-guide/sign-up-invite-teammates?view=azure-devops).

* Browse to <http://dev.azure.com/>
* Select Start Free
* Sign-in with an account that has no Azure DevOps Organizations (You will need to set up a Microsoft account for this)
* Create Organization, Select Organization Name & Select West Europe
* Create OctoFX Project and leave blank
* Take note of the URL

### Integrating Azure DevOps & Octopus Deploy

* [Generate an Octopus API Key](https://octopus.com/docs/octopus-rest-api/how-to-create-an-api-key) (Class led instructions provided).
* [Generate Azure Service Principal](https://octopus.com/docs/infrastructure/deployment-targets/azure#create-service-principal-account-in-azure) (Class led instructions provided).
* Note the API Key & Azure Service Principal details.
* Set up Azure Service Principal in Octopus (Class led instructions provided. It will likely fail validation if created less than 15 minutes ago - Try again at least 15 minutes after you created it).
* Install [Octopus Deploy's Azure DevOps extension](https://octopus.com/downloads) in Azure DevOps (Class led instructions provided).
* Set up Service Connection to your Octopus Cloud instance (Class led instructions provided).

### OctoFX Background

[OctoFX](https://github.com/OctopusSamples/OctoFX) is a sample application built to demonstrate how a multi-tier application is deployed using Octopus Deploy.

The application consists of three major components:

* Trading Website - A customer-facing ASP.NET MVC website, where customers trade currencies. Customers can register, login, manage their beneficiary account details, get quotes, and book deals.
* Deal Settlement Service - A .NET Windows Service that simulates the bank reconciliation and deals settlement process. It checks whether the OctoFX clearing accounts have received funds for any pending deals, and then initiates the transfer when deals are ready to be settled.
* A SQL Server database underpins the system.

## Wednesday 11th March Afternoon Session

### Pipeline

We will set up the following pipeline for OctoFX, using Octopus Deploy & Azure DevOps, deploying to Azure Infrastructure.

![CI/CD Pipeline](/Images/pipeline.png)

### Infrastructure Overview

As a summary, we will deploy:

* 4 x Azure Web Apps (1 for Development, 1 for Test, and 2 for Production).
* 1 x SQL Server for all environments.
* 1 x Jump Box for all environments.
* 1 x Windows Server for OctoFX Window Services for all environments.

The SQL Server, Jump Box, & Windows Services Server are all shared between environments to keep the hosting costs low.

### Development

For the development environment, we will deploy:

* 1 x Azure Web App for Development.
* 1 x SQL Database for Development.
* 1 x Windows Service for Development.
* 1 x Jump Box (For security & SQL Deployments).

![Development Infrastructure](/Images/dev.png)

### Test

For the test environment, we will deploy:

* 1 x Azure Web App for Test.
* 1 x SQL Database for Test.
* 1 x Windows Service for Test.
* 1 x Jump Box (For security & SQL Deployments).

![Test Infrastructure](/Images/test.png)

### Production

For the development environment, we will deploy:

* 2 x Azure Web Apps for Production.
* 1 x SQL Database for Production.
* 1 x Windows Service for Production.
* 1 x Jump Box (For security & SQL Deployments).

![Production Infrastructure](/Images/prod.png)

### Azure Sign-up

You will need an email address that is not tied to an existing Azure subscription. If you need an email address to sign up, you can create one on gmail.com, outlook.com, or if you ask the workshop host, they can provide you with one.

* Browse to <https://azure.microsoft.com/en-gb/free/>.
* Go through the sign-up process.
* You should have access to 12 months of free services, £150 credit to use in 30 days, and access to 25+ free Services.
* Save the details.

### Deploying Azure Infrastructure (Class led instructions provided)

This section will be carried out as Instructor-led training.

#### What are ARM Templates

An Azure Resource Manager(ARM) template is a JavaScript Object Notation (JSON) file that defines the infrastructure and configuration for your project.

With more companies moving to the cloud, many teams have adopted agile development methods. These teams iterate quickly. They need to deploy their solutions to the cloud repeatedly and know their infrastructure is in a reliable state. As infrastructure has become part of the iterative process, the division between operations and development has disappeared. Teams need to manage infrastructure and application code through a unified process.

To meet these challenges, you can automate deployments and adopt the practice of infrastructure as code.

In code, you define the infrastructure that needs to be deployed. The infrastructure code becomes part of your project. Just like the application code, you store the infrastructure code in a source repository and version it, and anyone on your team can run the code and deploy similar environments.

To implement infrastructure as code for your Azure solutions, use Azure Resource Manager templates.

The template is a JavaScript Object Notation (JSON) file that defines the infrastructure and configuration for your project. The template uses declarative syntax, which lets you state what you intend to deploy without having to write the sequence of programming commands to create it.

In the template, you specify the resources to deploy and the properties for those resources.

### Adding Infrastructure to Octopus Deploy

This section of the workshop will be led by a presentation, so please follow on-screen.

* Create 4 Web Apps using ARM Template. (1 x Development, 1 x Test & 2 x Production).
* Create 1 Bastion box using Server ARM Template.
* Create 1 SQL Server using SQL ARM Template.
* Create 1 Windows Service Server with Server ARM Template.

### Infrastructure Tips & Instructions

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

### Create the Deployment Process in Octopus Deploy

This section of the workshop will be led by a presentation, so please follow on-screen. You can also see OctoFX being configured in Octopus Deploy on [YouTube](https://www.youtube.com/watch?v=6DsJvtTcGMc).

* Create Development, Test, & Production environments (if not already done).
* Create OctoFX project.
* Create OctoFX variables.
* Create OctoFX variable for connection string (Server=#{OctoFX.Database.Server};Database=#{OctoFX.Database.Name};User ID=#{OctoFX.Database.User};Password=#{OctoFx.Database.Password};).
* Create OctoFX deployment process.

Your OctoFX deployment process should look something like:

![It should look something like](/Images/octopusoctofx.png)

### Thursday 12th March Morning Session

* Turn on infrastructure if you have shutdown enabled, and run Octopus health check and confirm all are available.

### Create Build & Release in Azure DevOps

This section of the workshop will be led by a presentation. We have a recording available on [YouTube](https://www.youtube.com/watch?v=36DLmkQ6Gs4) which you can use to configure Azure DevOps.

You should already have Azure DevOps, with an organization and the OctoFX project from yesterday.

* Browse to <https://dev.azure.com/> and login with details used yesterday.
* Go to Azure Repos and import <https://github.com/OctopusSamples/OctoFX/> into Azure Repos.
* Create Azure Pipeline for OctoFX.

Your Azure Pipeline should look something like:

![It should look something like](/Images/azurepipelinesoctofx.png)

* Create Azure Release pipeline

Azure Release pipeline should look something like:

![Azure Release pipeline should look something like](/Images/azurereleasecreatereleasepipelinesoctofx.png)

Azure Release Dev pipeline should look something like:

![Azure Dev Release pipeline should look something like](/Images/azurereleasedevpipelinesoctofx.png)

Azure Release Test pipeline should look something like:

![Azure Test Release pipeline should look something like](/Images/azurereleasetestpipelinesoctofx.png)

Azure Release Production pipeline should look something like:

![Azure Production Release pipeline should look something like](/Images/azurereleaseprodpipelinesoctofx.png)

### Packaging Applications

There are a variety of tools you can use to package your applications, and as long as you can create supported packages, you can deploy your applications with Octopus Deploy.

We've created the following tools to help you package your applications:

* The [Octopus CLI](https://octopus.com/docs/packaging-applications/create-packages/octopus-cli) to create Zip Archives and NuGet packages for .NET Core apps and full .NET framework applications.
* [OctoPack](https://octopus.com/docs/packaging-applications/create-packages/octopack) to create NuGet packages for ASP.NET apps (.NET Framework) and Windows Services (.NET Framework).
* The [TeamCity](https://octopus.com/docs/packaging-applications/build-servers/teamcity) plugin.
* The [Azure DevOps](https://octopus.com/docs/packaging-applications/build-servers/tfs-azure-devops/using-octopus-extension) plugin.

In addition to these tools, you can use other tools to create your packages; for instance, you might use the following:

* The built-in tools for [TeamCity](https://blog.jetbrains.com/teamcity/2010/02/artifact-packaging-with-teamcity/).
* [NuGet.exe](https://docs.microsoft.com/en-us/nuget/tools/nuget-exe-cli-reference) to create NuGet packages.
* [NuGet Package Explorer.](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer)
* [Grunt, gulp, or octojs](https://octopus.com/docs/deployment-examples/node-deployments/node-on-linux#create-and-push-node.js-project) for JavaScript apps.

In OctoFX, we are using nuspec files, so our files will be generated for us and you won't need to use the package step from the Octopus Azure DevOps plugin. Read more about [OctoPack](https://octopus.com/docs/packaging-applications/create-packages/octopack).

### Full Deployment

This section of the workshop will be led by a presentation, so please follow on-screen.

### Troubleshoot Full Deployment

In this section, we will troubleshoot any issues you're seeing (more often than not, it's the SQL user having problems).

* Check SQL Credentials.
* Check any Transformations.
* Check Azure Firewall.

## Thursday 12th March Afternoon Session

### Channels

You can watch a webinar about channels and lifecycles on [YouTube](https://www.youtube.com/watch?v=y_cS_DL4CcY).

As you deploy your projects, you can assign releases of projects to specific channels. This is useful when you want releases of a project to be treated differently depending on the criteria you've set. Without channels, you could find yourself duplicating projects to implement multiple release strategies. This would, of course, leave you trying to manage various duplicated projects. Channels let you use one project with multiple release strategies.

Channels can be useful in the following scenarios:

* Feature branches (or experimental branches) are deployed to test environments but not Production.
* Early access versions of the software are released to members of your early access program.
* Hot-fixes are deployed straight to Production and then deployed through the rest of your infrastructure after the fix has been released.

When you are implementing a deployment process that uses channels, you can scope the following to specific channels:

* Lifecycles
* Steps
* Variables
* Tenants

You can also define versioning rules per channel to ensure that only versions that meet specific criteria are deployed to particular channels.

Read more about [channels](https://octopus.com/docs/deployment-process/channels).

### Lifecycles

You can watch a webinar about channels and lifecycles on [YouTube](https://www.youtube.com/watch?v=y_cS_DL4CcY)

Lifecycles give you control over the way releases of your software are promoted between your environments. Lifecycles enable several advanced deployment workflow features:

* Control the order of promotion: for example, to prevent a release being deployed to Production if it hasn't been deployed to staging.
* Automate deployment to specific environments: for example, automatically deploy to test as soon as a release is created.
* Retention policies: specify the number of releases to keep depending on how far they have progressed through the lifecycle.

Phases define lifecycles. A lifecycle can have one or many phases.

* Phases occur in order. One phase must have a complete, successful deployment before the release is deployed to the next phase.
* Phases have one or more environments.
* Environments in a phase can be defined as automatic deployment environments or manual deployment environments.
* Phases can have a set number of environments that must be released before the next phase is available for deployment.

You can specify multiple lifecycles to control which projects are deployed to which environments.

Lifecycles are managed from the library page by navigating to Library ➜ Lifecycles:

Lifecycles are a crucial component of channels that give you even greater control over how your software is deployed. Channels let you use multiple lifecycles for a project and then automatically deploy to specific channels, using the defined lifecycle, based on the version of the software being deployed.

You can read more [lifecycles](https://octopus.com/docs/deployment-process/lifecycles)

### Multi-Tenancy

You can watch a webinar about Multi-Tenanted deployments with Octopus Deploy on [YouTube](https://www.youtube.com/watch?v=qsHSosC3GmA).

This section describes how to use Octopus to manage deployments of your applications to multiple end-customers.

Consider the following scenario:

NameBadge makes HR software for large corporate customers. They provide the software as a SaaS offering to their customers and host the website and associated services for them. Due to how the application is structured, for each customer, they deploy:

* A different SQL database.
* A copy of an ASP.NET website.
* A copy of a Windows Service.

The critical issue in this scenario is that the same components need to be deployed multiple times; once for each end-customer.

1. Deploy multiple instances of your project into the same [environment](/docs/infrastructure/environments/index.md);

* Tenant-per-customer
* Tenant-per-tester
* Tenant-per-feature/tenant-per-branch
* Tenant-per-geographical-region
* Tenant-per-datacenter

2. Easily manage unique configuration settings using variables defined on the tenant.
3. Promote releases to your tenants using safe customer-aware lifecycles, potentially through multiple environments:

* Tenant-specific UAT and Production environments.

4. Tailor the deployment process of your projects per-tenant as necessary.
5. Implement dedicated or shared hosting models for your tenants.
6. Employ tenant-aware security for managing tenants and deploying projects, including 3rd-party self-service sign in.
7. Implement early access or pre-release test programs incorporating 1st-party or 3rd-party testers.
8. Easily scale to large numbers of tenants using tags to manage tenants as groups instead of individuals.
9. Easily implement simple multi-tenant deployment scenarios and scale to support complex scenarios as your needs require.

Read more about [multi-tenancy](https://octopus.com/docs/deployment-patterns/multi-tenant-deployments).

### Runbooks

You can watch a full webinar on Runbooks on [YouTube](https://www.youtube.com/watch?v=aK1-pFe5dYM).

A deployment is only one phase in the life of an application. There are typically many other tasks that are performed to keep an application operating. A large part of DevOps is running operations separate from deploying applications, and this is where runbooks helps.

Runbooks are used to automate routine maintenance and emergency operations tasks like infrastructure provisioning, database management, and website failover and restoration.

Read more about [Runbooks](https://octopus.com/docs/operations-runbooks).

### Spaces

You can watch a webinar about Spaces on [YouTube](https://youtu.be/EJgM0r58VDc?t=278)

With Spaces, you can partition your Octopus Deploy Server so that each of your teams can only access the projects, environments, and infrastructure they work with from the spaces they are members of. Users can be members of multiple teams and have access to various spaces, but the entities and infrastructure they work with will only be available in the space it is assigned to.

Read more about [Spaces](https://octopus.com/docs/administration/spaces)

### Workers

You can watch a webinar about Workers on [YouTube](https://youtu.be/EJgM0r58VDc?t=1697)

Workers are machines that can execute tasks that don't need to be run on the Octopus Server or individual deployment targets.

You can manage your Workers by navigating to Infrastructure ➜ Worker Pools in the Octopus Web Portal. Workers are useful for the following scenarios:

* Publishing to Azure websites.
* Deploying AWS CloudFormation templates.
* Deploying to AWS Elastic Beanstalk.
* Uploading files to Amazon S3.
* Backing up databases.
* Performing database schema migrations
* Configuring load balancers.

Read more about [Workers](https://octopus.com/docs/infrastructure/workers).

### Common Deployment Patterns

#### Blue/Green

Blue-green deployments are a pattern that reduces downtime during production deployments by having two production environments ("blue" and "green").

> One of the challenges with automating deployment is the cut-over itself, taking software from the final stage of testing to live Production. You usually need to do this quickly to minimize downtime. The **blue-green deployment** approach does this by ensuring you have two production environments, as identical as possible. At any time one of them, let's say blue for the example, is live. As you prepare a new release of your software, you do your final stage of testing in the green environment. Once the software is working in the green environment, you switch the router so that all incoming requests go to the green environment - the blue one is now idle.
>
> * [Martin Fowler](http://martinfowler.com/bliki/BlueGreenDeployment.html)

As well as reducing downtime, Blue/Green can be a powerful way to use extra hardware compared to having a dedicated staging environment:

* Staging: When blue is active, green becomes the staging environment for the next deployment.
* Rollback: We deploy to blue and make it active. Then a problem is discovered. Since green still runs the old code, we can roll back easily.
* Disaster recovery: After deploying to blue and we're satisfied that it is stable, we can deploy the new release to green too. This gives us a standby environment ready in case of disaster.

Read more about [blue/green deployments](https://octopus.com/docs/deployment-patterns/blue-green-deployments).

#### Red/Black

When deploying new versions of a centralized application like a web service, there is a strategy you can use to direct production traffic to the latest version only after it has been successfully deployed and optionally tested. This strategy goes by the name blue/green or red/black, with each color representing a copy of the target environment. Traffic is routed to one color or the other (or potentially both in a canary deployment or during A/B testing, but that's a story for another time). Having two environments running side by side hosting different versions of an application means traffic can be switched over, and back again if an issue is found, with little to no downtime.

So why is this strategy referred to as both green/blue and red/black? Do these colors imply technical differences?

StackOverflow says

Our first stop is to StackOverflow, where we find the question [What's the difference between Red/Black deployment and Blue/Green Deployment?](https://stackoverflow.com/questions/45259589/whats-the-difference-between-red-black-deployment-and-blue-green-deployment).

The highest voted answer indicates that there is indeed a difference between these two terms:

> in blue-green deployment, both versions may be getting requests at the same time temporarily, while in red-black only one of the versions is getting traffic at any point in time

The answer then goes on to say that:

> But red-black deployment is a newer term being used by Netflix, Istio, and other frameworks/platforms that support container orchestration

I've frequently seen the term red/black being attributed to tools created by Netflix and container platforms in general, so let's go to their documentation to see how they define these strategies.

Read more about [Red/Black(<https://octopus.com/blog/blue-green-red-black).>

#### Canary Deployments

Canary deployments are a pattern for rolling out releases to a subset of users or servers. The idea is first to deploy the change to a small subset of servers, test it, and then roll the change out to the rest of the servers. The canary deployment serves as an early warning indicator with less impact on downtime; if the canary deployment fails, the rest of the servers aren't impacted.

> Canaries were once regularly used in [coal mining](http://en.wikipedia.org/wiki/Coal_mining "Coal mining") as an early warning system. [Toxic](http://en.wikipedia.org/wiki/Toxic "Toxic") [gases](http://en.wikipedia.org/wiki/Gas "Gas") such as [carbon monoxide](http://en.wikipedia.org/wiki/Carbon_monoxide "Carbon monoxide"), [methane](http://en.wikipedia.org/wiki/Methane "Methane") or [carbon dioxide](http://en.wikipedia.org/wiki/Carbon_dioxide "Carbon dioxide") in the mine would kill the bird before affecting the miners. Signs of distress from the bird indicated to the miners that conditions were unsafe. The use of miners' canaries in [British](http://en.wikipedia.org/wiki/Great_Britain "Great Britain") mines was phased out in 1987.
>
> * [Wikipedia](http://en.wikipedia.org/wiki/Domestic_Canary#Miner.27s_canary)

The necessary steps of a canary deployment are:

1. Deploy to one or more canary servers.
2. Test, or wait until satisfied.
3. Deploy to the remaining servers.

The test phase of the canary deployment can work in many ways. You could run some automated tests, perform manual testing yourself, or even leave the server live and wait to see if end-users encounter problems. All three of these approaches might be used. Depending on how you plan to test, you might decide to remove the canary server from the production load balancer and return it only when rolling out the change to the rest of the servers.

:::hint
**Similar to staging**
Canary deployments are similar to using a staging environment. The difference is that staging environments are usually dedicated to the task; a staging web server doesn't become a production server. By contrast, in a canary deployment, the canary server remains part of the production fleet when the deployment is complete. Canary deployments may be worth considering if you do not have the resources for a dedicated staging environment.
:::

Read more about [Canary Deployments](https://octopus.com/docs/deployment-patterns/canary-deployments).

### Octopus & Azure DevOps Administration

* [Auditing](https://octopus.com/docs/administration/managing-users-and-teams/auditing).
* [External Authentication Providers](https://octopus.com/docs/administration/authentication).
* [Users/Teams/Permissions](https://octopus.com/docs/administration/managing-users-and-teams).
* [Upgrading Octopus](https://octopus.com/docs/administration/upgrading).
* [Retention Policies](https://octopus.com/docs/administration/retention-policies).
* [Cloud vs On-Premise](https://octopus.com/docs/octopus-cloud).

## Wrap-up & Feedback, and Resources

Thanks for spending the last two days with us. We hope you enjoyed the workshop and learned a lot!

### Recommendations

* Destroy your infrastructure, as this will continue charging you.
* Keep Azure DevOps, as there should be no cost.
* Octopus Cloud will remain free for as long as you have no more than ten targets.

### Octopus Resources

* For more information on Octopus, check out the [Optimum Setup Guide](https://github.com/OctopusDeploy/OptimumSetupBook).
* [Octopus documentation](http://octopus.com/docs/).
* [Octopus Guides](https://octopus.com/docs/guides) where you can select your own CI/CD pipeline to generate a video, documentation, and a TestDrive VM that walks you through a complete CI/CD setup.
* [Octopus YouTube channel](http://octopus.com/videos).
* [Octopus Events Page](https://octopus.com/events) for upcoming webinars & events, and for previously recorded webinars.
* [Sample Octopus instance](http://samples.octopus.app/).
* [Octopus Jenkins sample](https://jenkinssample.octopus.com/).
* [Octopus TeamCity sample](https://teamcitysample.octopus.com/).
* [Azure DevOps OctoFX sample](https://dev.azure.com/octopussamples/OctoFX).
* [Octopus Twitter](https://twitter.com/OctopusDeploy).

### Azure DevOps Resources

* [Microsoft Learn](https://docs.microsoft.com/en-us/learn/) has some great resources for Azure DevOps & Azure.
* [Azure Quickstart Templates](https://azure.microsoft.com/en-gb/resources/templates/) and [Github](https://github.com/Azure/azure-quickstart-templates) are great resources for Quickstart ARM Templates.
* Azure DevOps certification [exam detail page](https://docs.microsoft.com/en-us/learn/certifications/azure-devops).
* Azure Administrator exam details on this [page](https://docs.microsoft.com/en-gb/learn/certifications/azure-administrator).
* [Azure Docs](https://docs.microsoft.com/en-gb/azure/).
* [Azure DevOps Docs](https://docs.microsoft.com/en-gb/azure/devops/).
* [Channel 9 video content](https://channel9.msdn.com/).

Please take 5 minutes and help us by filling out this anonymous [feedback form](https://forms.gle/tXi3Vn9n4kPKT5ai7).
