
# [MSlearn - .NET Aspire](https://learn.microsoft.com/en-us/dotnet/aspire)

## [Overview](https://learn.microsoft.com/en-us/dotnet/aspire/get-started/aspire-overview)

**Orchestration:** .NET Aspire provides features for running and connecting multi-project applications and their dependencies for local development environments.

- App composition - Awareness of all the projects the make up an app and how they fit together
- Service discovery - Manage connection strings and injecting them into services

```
// Create a distributed application builder given the command line arguments.
var builder = DistributedApplication.CreateBuilder(args);

// Add a Redis server to the application.
var cache = builder.AddRedis("cache");

// Add the frontend project to the application and configure it to use the 
// Redis server, defined as a referenced dependency.
builder.AddProject<Projects.MyFrontend>("frontend")
       .WithReference(cache);
```
    
**Components:** .NET Aspire components are NuGet packages for commonly used services, such as Redis or Postgres, with standardized interfaces ensuring they connect consistently and seamlessly with your app.

- Services - Redis, Postgres, Events, Telemetry, etc


- **Tooling:** .NET Aspire comes with project templates and tooling experiences for Visual Studio, Visual Studio Code, and the dotnet CLI to help you create and interact with .NET Aspire apps.

## [First Aspire App](https://learn.microsoft.com/en-us/dotnet/aspire/get-started/build-your-first-aspire-app?pivots=vscode)

### Requirements

https://learn.microsoft.com/en-us/dotnet/aspire/fundamentals/setup-tooling

Install Aspire workload

```
dotnet workload update
dotnet workload install aspire
dotnet workload list
```

Set container runtime (Docker is default but need to change if using Podman)


Linux

```
export DOTNET_ASPIRE_CONTAINER_RUNTIME=podman
```

Windows

```
$env:DOTNET_ASPIRE_CONTAINER_RUNTIME = "podman"
```

### Create the starter template

```
dotnet new aspire-starter -n AspireApp1 --no-https
```

Was having trouble using https in codespaces. Had to set an env variable to allow it.

https://learn.microsoft.com/en-us/dotnet/aspire/troubleshooting/allow-unsecure-transport?tabs=unix


### Run the app

```
cd AspireApp1.AppHost
dotnet run
```

- [App on port 5010](https://super-couscous-q9x4rx6rx5fggj-5010.app.github.dev/)
- [Dashboard on port 15193](https://super-couscous-q9x4rx6rx5fggj-15193.app.github.dev/)


### Resources

- https://github.com/dotnet/aspire-samples
