# NDCDevOpsWorkshop Azure DevOps Configuration

## Thursday 12th March Morning Session

* Turn on infrastructure if you have shutdown enabled, and run Octopus health check and confirm all are available.

## Create Build & Release in Azure DevOps

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

## Packaging Applications

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

## Full Deployment

This section of the workshop will be led by a presentation, so please follow on-screen.

## Troubleshoot Full Deployment

In this section, we will troubleshoot any issues you're seeing (more often than not, it's the SQL user having problems).

* Check SQL Credentials.
* Check any Transformations.
* Check Azure Firewall.