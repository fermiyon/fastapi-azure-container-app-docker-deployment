# Azure Docker Deployment

Deploy docker container to Azure Container Apps

## Login

```bash
az login
```

## Build and run image locally

### Build the image

```bash
docker build --tag fastapi-demo .
```

### Run the image locally in a Docker container.

```bash
docker run --detach --publish 3100:3100 fastapi-demo
```

## Deploy web app to Azure

```bash
az containerapp up --resource-group web-fastapi-aca-rg --name web-aca-app --ingress external --target-port 3100 --source .
```

## Cleanup

```bash
az group delete --name web-fastapi-aca-rg
```
  
## References

* [FastAPI Docker docs](https://github.com/tiangolo/uvicorn-gunicorn-fastapi-docker)
* [Microsoft Learn](https://learn.microsoft.com/en-us/azure/developer/python/tutorial-containerize-simple-web-app?tabs=web-app-fastapi)