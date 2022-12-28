# Can't be from slim image as need tools for some of the examples
FROM node:current-alpine

LABEL MAINTAINER=nigelpoulton@hotmail.com

# Copy source code to /src in container
COPY . /src

# Install app and dependencies into /src in container
RUN cd /src; npm install

# Document the port the app listens on
EXPOSE 8080

# Run this command (starts the app) when the container starts
CMD cd /src && node ./app.js
