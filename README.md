# Deploy a Professional Python REST API with Docker

This project is based on Pau Labarta Bajo's guide [here](https://paulabartabajo.substack.com/p/lets-write-a-professional-dockerfile?utm_campaign=email-half-post&r=1bjj41&utm_source=substack&utm_medium=email).

It covers the different levels of writing standard Dockerfiles

- **Dockerfile.naive** is a simple Dockerfile that ends up needlessly bloated

- **Dockerfile.1stage** takes advantage of Docker caching to ensure dependencies aren't constantly reinstalled every time code changes are made.

- **Dockerfile.2stage** uses Docker multi-stage builds to guarantee smaller and more efficient final docker images.


## Deployment
A Makefile is provided to faciliate seamless deployment. 

To containerize the Rest API application, run any of the following to build:

`make build-naive` to deploy using the **Dockerfile.naive** file

`make build-single-stage` to deploy using the **Dockerfile.1stage**

`make build-multi-stage` to deploy using the **Dockerfile.2stage** file

To deploy:
```
docker run -p 8090:8000 taxi-data-api-python:multi-stage-build
```

The container serves on port `8000`. You may customize accordingly.


To send a sample request testing the application:
```
make sample-request
```