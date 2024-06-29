![Static Badge](https://img.shields.io/badge/Azure%20CLI-007FFF)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?logo=docker&logoColor=white)

By Selman Karaosmanoglu 

## Date created
28 June 2024

# Azure Docker Deployment

## Overview

This project contains the necessary files and instructions to deploy a FastAPI application as a Docker container to Azure Container Apps.

## Getting Started

## Login

```bash
az login
```

## Build and run image locally

### Build the Docker Image

To build the Docker image for the FastAPI demo, run the following command:

```bash
docker build --tag fastapi-demo .
```

### Run the image locally in a Docker container.

```bash
docker run --detach --publish 3100:3100 fastapi-demo
```

### Deploy to Azure Container Apps

Deploy the containerized application to Azure Container Apps using the following command:

```bash
az containerapp up --resource-group web-fastapi-aca-rg --name web-aca-app --ingress external --target-port 3100 --source .
```

- **Resource Group**: Specify the resource group where your Azure Container Apps will reside.
- **Ingress**: Set to 'external' to allow external access to the application.
- **Target Port**: The port that the application will listen on.

## Cleanup

```bash
az group delete --name web-fastapi-aca-rg
```

## Requirements

- Azure CLI
- Docker
  
## References

* [FastAPI Docker docs](https://github.com/tiangolo/uvicorn-gunicorn-fastapi-docker)
* [Microsoft Learn](https://learn.microsoft.com/en-us/azure/developer/python/tutorial-containerize-simple-web-app?tabs=web-app-fastapi)
* Duke University - Virtualization, Docker, and Kubernetes for Data Engineering program
