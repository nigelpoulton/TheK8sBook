# Test app for demonstrating containerizing web app

Super-simple Node web app for containerization demos,

## Instructions for use

1. Fork the repo 
2. Clone repo locally
3. Build Docker iamge `docker image build -t <tag> .` from within the root directory of the repo 
4. Push image to container registry
5. Run container/Pod using the created image

## Used by

This repo and app is currently used by:

- [The Kubernetes Book](https://www.amazon.com/Kubernetes-Book-Nigel-Poulton/dp/B09QFM8H6T/ref=tmm_pap_swatch_0?_encoding=UTF8&qid=1661247547&sr=8-3)

## Build and Dockerfile info

**Previous versions used Centos 7 base image.**

```
FROM node:current-slim
COPY . /src
RUN cd /src; npm install
EXPOSE 8080
CMD cd /src && node ./app.js
```

Bootstrap: https://www.bootstrapcdn.com/